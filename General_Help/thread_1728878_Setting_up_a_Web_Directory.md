---
title: "Setting up a Web Directory"
date: 2011-04-14
forum: General Help
---

### Post by SkyBlue1984 on 2011-04-14
Hi,

I have been using Ubuntu for around 2 years now so am fairly familiar with it now! 

I am interested in setting up a Web Directory. However, I have no idea of setting up hosting/servers etc etc. I have no programming experience so in this I am a complete beginner. If someone could advise me or point me in the direction of something which will give details of setting up a web site to a complete beginner like myself, then that would be great!

I was going to purchase a directory script with regards to setting up the actual directory, it is just the hosting and server i want to get set up. I have no idea about this at all at the moment.

Thank you!!!! :D

---

### Post by Blasphemist on 2011-04-14
Hi back at ya!

I have a Drupal web development environment on my laptop but I can't tell if that or something like that is actually what you are looking for.

What is the end result(s) that you want? Is this for learning, development or some other use? 

Hosting your own site requires you get a domain so that you have an address so to speak. As long as you want to use Go Daddy (elephant killer CEO) I can help with that if you want. The hardest thing is choosing the name but you may be past that.

What kind of site are you thinking of? You can use a huge variety of tools from text editors to powerful content management systems of varying complexity depending on your needs. I saw a site the other day that was created in Vim.

Anyway, it'll help for you to describe your project in whatever detail you can.

---

### Post by SkyBlue1984 on 2011-04-14
> **Blasphemist said:**
> Hi back at ya!

I have a Drupal web development environment on my laptop but I can't tell if that or something like that is actually what you are looking for.

What is the end result(s) that you want? Is this for learning, development or some other use? 

Hosting your own site requires you get a domain so that you have an address so to speak. As long as you want to use Go Daddy (elephant killer CEO) I can help with that if you want. The hardest thing is choosing the name but you may be past that.

What kind of site are you thinking of? You can use a huge variety of tools from text editors to powerful content management systems of varying complexity depending on your needs. I saw a site the other day that was created in Vim.

Anyway, it'll help for you to describe your project in whatever detail you can.

Hi!

I should have mentioned that I work in SEO so am familiar with buy buying domains and the like. Basically I wanted to set up a basic holiday web directory.

---

### Post by WorMzy on 2011-04-14
You're going to purchase a script to set up the directory?

I'm sorry, but I really don't understand what you mean by this.


You can install a LAMP (Linux + Apache, MySQL and PHP) server on your machine by running
```
sudo apt-get install lamp-server^
```

Everything should be set up for you, including the web directory (/var/www). After that, you can place documents here, and you'll be able to access them at [http://localhost]("http://localhost"), and, depending on how your network is set up, [at your IP address]("http://www.whatismyip.com/automation/n09230945.asp").

---

### Post by SkyBlue1984 on 2011-04-14
> **WorMzy said:**
> You're going to purchase a script to set up the directory?

I'm sorry, but I really don't understand what you mean by this.


You can install a LAMP (Linux + Apache, MySQL and PHP) server on your machine by running
```
sudo apt-get install lamp-server^
```Everything should be set up for you, including the web directory (/var/www). After that, you can place documents here, and you'll be able to access them at [http://localhost](http://localhost), and, depending on how your network is set up, [at your IP address]("http://www.whatismyip.com/automation/n09230945.asp").

Thank you, WorMzy!! 

[http://www.esyndicat.com/product/bidding-directory-script.html](http://www.esyndicat.com/product/bidding-directory-script.html) - this is the sort of thing I meant about buying a script, please forgive me I am very new to this!!

I also meant to include, the reason why I was thinking of buying a script is because I cannot programme or anything at the moment. So was after something that would let me create the directory itself.

---

### Post by Blasphemist on 2011-04-14
Have you looked at Drupal Gardens and WordPress.com? You can use them to play with the two industry leaders from a noob point of view and not have to pay anything. They can be good for non-noob
s too. You can use them to get walked through the set up and get a working site up and accessible to whomever you want quickly and easily, and free. If you then want to move it to your system you can. If you still want to do this locally, my focus has been on Drupal. If you want help with doing that local, guide me about how much detail you want so that I don't overwhelm you.

---

### Post by Blasphemist on 2011-04-14
I checked out your link and it doesn't look like a good place to start to me. I recommend that you go to wordpress.com and set up a blog. Start with the 10 step walk through guide. If this doesn't look like you can meet your needs, try to more fully describe what you mean by a holiday directory please.

---

### Post by SkyBlue1984 on 2011-04-15
[http://www.theholidaydirectory.co.uk](http://www.theholidaydirectory.co.uk) - This is an example of a holiday directory.

---

### Post by Tk0680 on 2011-04-15
I sense some running-before-walking going on here.

The example you linked will be an advanced, database-driven site, most likely running on a framework like Zend or Rails. Bear in mind that, if you shell out for one of these scripts (and, honestly, I wouldn't trust the example you linked to be what you seem to be looking for at all) with no ability to customise/modify it as you see fit, you are very stuck should you find something about it you dislike.

I'd strongly recommend you either gain the experience you're missing at the moment, or get in touch with someone who understands more about the whole shebang.

---

### Post by SkyBlue1984 on 2011-04-15
At the moment I was thinking of just setting up a very basic one whilst I become more familiar with it all. Basically, something like this - [http://www.tgp-internet.com](http://www.tgp-internet.com) - this wouldn't be too hard to set- up, surely?!

---

### Post by Blasphemist on 2011-04-15
TK, I believe we may be in the midst of a genius with SkyBlue. I agree about the running before walking here. This web site creation stuff may look simple to you but it is not. You cannot, let me be very clear, CANNOT buy this script and have a site like this up and maintainable. I highly recommend you start with walking for free and learn just how much you have to learn. The sites you used for examples use many technologies and to me they aren't even the best or easiest to use technologies. If you use Chrome or Chromium browsers you can install the built with extension and start looking at the technologies used at sites you visit. Again, I recommend you start with Drupal Gardens or WordPress.com. 

This is built with information on the second example you gave Sky.

Server Information
Apache
Apache Usage Statistics - Websites using Apache
Apache has been the most popular web server on the Internet since April 1996.
Unix
Unix Usage Statistics - Websites using Unix
A *nix based operating system (undisclosed).
mod_ssl
mod_ssl Usage Statistics - Websites using mod_ssl
This module provides strong cryptography for the Apache 1.3 webserver via the Secure Sockets Layer (SSL v2/v3) and Transport Layer Security (TLS v1) protocols
OpenSSL
OpenSSL Usage Statistics - Websites using OpenSSL
The OpenSSL Project is a collaborative effort to develop a robust, commercial-grade, full-featured, and Open Source toolkit implementing the Secure Sockets Layer (SSL v2/v3) and Transport Layer Security (TLS v1) protocols as well as a full-strength general purpose cryptography library.
Auth Passthrough
Auth Passthrough Usage Statistics - Websites using Auth Passthrough
Frontpage security module for Apache.
Limiter Modules
Limiter Modules Usage Statistics - Websites using Limiter Modules
Log Byte and Bandwidth Limiter modules.
Frameworks
PHP
PHP Usage Statistics - Websites using PHP
PHP is a widely-used general-purpose scripting language that is especially suited for Web development and can be embedded into HTML.
Frontpage Extensions
Frontpage Extensions Usage Statistics - Websites using Frontpage Extensions
A web site administration tool from Microsoft for the Microsoft Windows line of operating systems. It was part of Microsoft Office application suite from 1997 to 2003.
Advertising
Google Adsense
Google Adsense Usage Statistics - Websites using Google Adsense
A contextual advertising solution for delivering Google AdWords ads that are relevant to site content pages.
Analytics and Tracking
Google Analytics
Google Analytics Usage Statistics - Websites using Google Analytics
Google Analytics offers a host of compelling features and benefits for everyone from senior executives and advertising and marketing professionals to site owners and content developers.
JavaScript Libraries
JQuery
JQuery Usage Statistics - Websites using JQuery
JQuery is a fast, concise, JavaScript Library that simplifies how you traverse HTML documents, handle events, perform animations, and add Ajax interactions to your web pages. jQuery is designed to change the way that you write JavaScript.
JQuery UI
JQuery UI Usage Statistics - Websites using JQuery UI
jQuery UI provides abstractions for low-level interaction and animation, advanced effects and high-level, themeable widgets, built on top of the jQuery JavaScript Library, that you can use to build highly interactive web applications.
JQuery Validate
JQuery Validate Usage Statistics - Websites using JQuery Validate
JQuery Form Validation Plugin.
Prototype
Prototype Usage Statistics - Websites using Prototype
Prototype is a javascript framework which aims to ease development of dynamic web applications.
script.aculo.us
script.aculo.us Usage Statistics - Websites using script.aculo.us
script.aculo.us provides you with easy-to-use, cross-browser user interface JavaScript libraries to make your web sites and web applications fly.
Widgets
Thickbox
Thickbox Usage Statistics - Websites using Thickbox
ThickBox is a webpage UI dialog widget written in JavaScript on top of the jQuery library. Its function is to show a single image, multiple images, inline content, iframed content, or content served through AJAX in a hybrid modal.
Open Thumbnails
Open Thumbnails Usage Statistics - Websites using Open Thumbnails
Leader in web preview technology. Serving thumbshots to over 1,000 sites
Document Information
XHTML Transitional
XHTML Transitional Usage Statistics - Websites using XHTML Transitional
The website claims XHTML Transitional status. XHTML 1.0 Transitional is the same as HTML 4.01 Transitional, but follows XML syntax rules. It supports everything found in XHTML 1.0 Strict, but also permits the use of a number of elements and attributes that are judged presentational, in order to ease the transition from HTML 3.2 and earlier. These include center, u, strike, and applet.
Cascading Style Sheets
Cascading Style Sheets Usage Statistics - Websites using Cascading Style Sheets
Cascading Style Sheets (CSS) is a stylesheet language used to describe the presentation of a document written in a markup language. Its most common application is to style web pages written in HTML
Meta Keywords
Meta Keywords Usage Statistics - Websites using Meta Keywords
Meta tag containing keywords related to the page.
Meta Description
Meta Description Usage Statistics - Websites using Meta Description
The description attribute provides a concise explanation of the page content.
Meta Robot
Meta Robot Usage Statistics - Websites using Meta Robot
This page contains a meta robots tag which tells search engines and robots to index or not index the page.
Javascript
Javascript Usage Statistics - Websites using Javascript
JavaScript is a scripting language most often used for client-side web development. Its proper name is ECMAScript, though "JavaScript" is much more commonly used. The website uses JavaScript.
Conditional Comments
Conditional Comments Usage Statistics - Websites using Conditional Comments
The website uses conditional comments that are supported by Microsoft Internet Explorer. They allow web developers to show or hide HTML code based on the version of the viewer's browser.
Encoding
UTF-8
UTF-8 Usage Statistics - Websites using UTF-8
UTF-8 (8-bit UCS/Unicode Transformation Format) is a variable-length character encoding for Unicode. It is the preferred encoding for web pages.

---

