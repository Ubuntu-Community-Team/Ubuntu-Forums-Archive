---
title: "Get rid of open dns"
date: 2010-04-17
forum: General Help
---

### Post by Ebere on 2010-04-17
How do I get rid of open dns ?

I am sick and tired of the way they grab a link and hold onto it for several minutes. Not letting you actually retry the link, but redirecting you back to their own search engine, every time...

I have already opened the configuration for my router, and made sure that open dns is not selected there.

How do I make sure that my kubuntu system is not defaulting somehow to open dns ?

Or is there some way to force firefox itself, to kick open dns to the curb ?

---

### Post by lovinglinux on 2010-04-17
[http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/](http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/)

---

### Post by Ebere on 2010-04-18
> **lovinglinux said:**
> [http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/](http://www.labnol.org/software/browsers/prevent-opendns-google-redirects-firefox-address-bar-ie/2662/)

Thank you.

That was a very informative link. 

I made some changes based on the info there.

However...

That solution has to do with the keyword search function in Firefox.

The problem I am talking about is:

If there is the slightest delay in response from a link, OpenDNS kicks in, and sends you to their own search page.

Then, for the next several minutes... every time that you try to go back to the link, opendns redirects you back to their search page again.

For instance... If I opened this thread, saw a link to another page on this forum... Clicked on that link... And there was the slightest delay in response... OpenDNS kicks in, and for the next several minutes.. Any and EVERY link to any page whatsoever, at ubuntuforums.com... Would be redirected to the opendns search page.

Do not pass go. Do not collect 200 dollars. And do not even pretend to attempt to check the link again. Just toss this poor bugger back to our search page...

Even though there is absolutely nothing wrong with the forum, or any of the links that I try.

At that point, if I completely leave any links to here, alone, for at least 5 minutes, then try again... All the links and pages work correctly again... -Until- the next time that a page hesitates in the slightest.. then it is back to the same old circus.

Irritating doesn't even begin to describe it.

I have gotten to the point where I want opendns as far away from my system, and my connection, as possible.

---

### Post by lovinglinux on 2010-04-18
> **Ebere said:**
> Thank you.

That was a very informative link. 

I made some changes based on the info there.

However...

That solution has to do with the keyword search function in Firefox.

The problem I am talking about is:

If there is the slightest delay in response from a link, OpenDNS kicks in, and sends you to their own search page.

Then, for the next several minutes... every time that you try to go back to the link, opendns redirects you back to their search page again.

For instance... If I opened this thread, saw a link to another page on this forum... Clicked on that link... And there was the slightest delay in response... OpenDNS kicks in, and for the next several minutes.. Any and EVERY link to any page whatsoever, at ubuntuforums.com... Would be redirected to the opendns search page.

Do not pass go. Do not collect 200 dollars. And do not even pretend to attempt to check the link again. Just toss this poor bugger back to our search page...

Even though there is absolutely nothing wrong with the forum, or any of the links that I try.

At that point, if I completely leave any links to here, alone, for at least 5 minutes, then try again... All the links and pages work correctly again... -Until- the next time that a page hesitates in the slightest.. then it is back to the same old circus.

Irritating doesn't even begin to describe it.

I have gotten to the point where I want opendns as far away from my system, and my connection, as possible.

You could use [Google DNS](http://www.google.com/search?q=Google+DNS). On my system, I change the DNS server on the router configuration. I'm not sure if you can setup the DNS on Ubuntu.

---

### Post by Ebere on 2010-05-07
An update:

This doesn't get rid of opendns, but it may help a lot, by getting rid of some of the problems that were opening the door to opendns taking over the request for a link... with their search page.

I edited:  /etc/nsswitch.conf.

Commented out the line: hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

(Note: I commented the line out by adding # and a space at the beginning of the line. I did this, so that if it causes problems in the future, I can change it back without having to TRY to remember what the line said before. LOL)

Added on a new line just below that:   hosts:  files dns

Pages that used to take forever to load up, are coming right up, now.

I don't know if this actually takes care of it, but since making the change, I have only had two page load errors, and in niether case, did opendns pop up it's search page.

If I start having the problem again, regardless of this change, I'll try to remember to come back here and update again.

---

