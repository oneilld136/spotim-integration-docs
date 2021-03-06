# Spot.IM on AMP (Accelerated Mobile Pages)
Spot.IM supports Accelerated Mobile Page (AMP). If you're not familiar with AMP, it's an open source HTML library, JavaScript library, and caching service designed for building high performance web pages. AMP pages are highly optimized and adhere to a set of standards to maximize performance across a variety of browsers and platforms. To learn more, see Google's [What is AMP](https://www.ampproject.org/learn/overview/) page.

## Contents
- [Contents](#contents)
- [Before You Begin](#before-you-begin)
  - [Best Practices for Post IDs](#best-practices-for-post-ids)
- [Using AMP for the Standard Social Kit](#using-amp-for-the-standard-social-kit)

## Before You Begin
To use AMP, you will need the following information:

1. Your `Spot ID`. If you don't know your Spot ID, contact your Spot.IM account manager.
2. The `POST_ID` of the page you want to add a Spot.IM Conversation to. The `POST_ID` can be any alphanumeric value as long as it's unique to the page.

### Best Practices for Post IDs
Post IDs can contain the following characters:

- Letters
- Numbers
- Underscores
- Dashes

Post IDs should be short. A common approach is to use the page's title or content. For example:

`article_1`
`article-title`
`article-short-link`


## Using AMP for the Standard Social Kit
At the moment, Popular in the Community Widget has AMP-compatible code in Beta stages.
If you wish to implement on AMP both Popular in the Community and Conversation, please reach out to your account manager.

From the account manager you will recieve two html files:
1. Header - styling code to be added to your head section. It will be an HTML code snippet, wrapped with <style amp-custom> tags. _**Note:** If you have an existing `<style amp-custom>` tag, append the snippet you recieve to that tag.
  
2. Body - Code of the Popular in the Community and Conversation, a.k.a the SpotIM standard implementation. If your AMP implementation is based on your general site template, replace the entire SpotIM block of code with the the snippet you recieve. If not, position the code in the place you want to implement both of the widgets.

The file with the implementation code to be pasted into the Body of the page has the conversation AMP implemantation code presented above, with your `SPOT_ID` already configured - https://github.com/SpotIM/spotim-integration-docs/tree/master/google-amp#using-amp-for-conversation. Make sure to replace the `POST_ID` parameter with your own value.

_**Note:** By default, this code will present Conversation below Popular in the Community Widget. If you prefer differently, make sure to ask your Account Manager for this adjustment. 

## Amp for SSO
Currently, we do not support AMP for SSO directly. However, we have an option to redirect to the mobile, non-amp version of the article page. 

###Implementation Instructions
1. Search for the source code of the conversation iframe in the amp code provided. The easiest way to locate this is to search for "postId" and it should bring up code that looks like this:
<img src="https://s3.amazonaws.com/www.spotim.name/rich/amp_image_example.png">

2. The query parameters of the source will need to be modified. Listed below are the query parameters that are required
    * spot_im_highlight_immediate=true
    * spotId=sp_SampleSpotId (set this variable equal to your spot id)
    * postId=-1 (set this variable equal to the post id of the article)
    * inactive=true
    * data-post-url='https%3A%2F%2Fwww.examplewebsite.com' (set this variable to the article url in encoded url form)
      
    <img src="https://s3.amazonaws.com/www.spotim.name/rich/amp_image_example2.png"> 
    
3. Make sure that each article page has the appropriate postId and data-post-url in encoded url form. If you click on conversation while on a Spot.IM supported amp page, it should redirect you to the mobile non-amp version of the article and automatically scroll down to conversation. <br><br>
**Warning - If the data-post-url is wrong (i.e. not in encoded url form or a link that does not have Spot on it), clicking on conversation will redirect to the link provided which may be broken**

