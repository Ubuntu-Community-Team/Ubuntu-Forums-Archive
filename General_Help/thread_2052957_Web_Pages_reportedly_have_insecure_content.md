---
title: "Web Pages reportedly have insecure content"
date: 2012-09-04
forum: General Help
---

### Post by laserman on 2012-09-04
For about the last couple of weeks, I have been getting a lot of notifications when I open a web page where it tells me that the web page has insecure content. Options include Load? or Don't Load (recommended). When accessing https sites, I have also experienced an "X" and https is in red. When I click on the drop down on the red https, it tells me that this page includes other resources which are not secure.

Has there been a change to Chromium that has caused this or are web pages not set up properly to render SSL properly? This is general across the board with no specific web pages in question. I am getting it ALL THE TIME. 

or

Is it the version of Chromium I am running (18.0.1025.151 (Developer Build 130497 Linux) Ubuntu 10.04) with my Ubuntu 10.04 version?

Anyone else experiencing this?

:confused:

laserman

---

### Post by SeijiSensei on 2012-09-04
Usually this is a problem with a badly-designed website and often concerns graphic objects.  If any of the objects are accessed with an http:// URL rather than a https:// URL, you'll see these kind of warnings.  One common situation is where you access a page with HTTPS that links to images on another site.  Unless those links also use HTTPS, you'll get warned.  Having done exactly this in the past, I know that it takes a while as a developer to track down everything a page links to and make sure it is accessible via HTTPS.

---

### Post by laserman on 2012-09-04
SeijiSensei,

That makes a lot of sense and can understand that being the problem. 

With that being said, isn't there also the option for all of your web browsing to be set at secure connections only? I'm beginning to wonder if I have fat fingered something that may have caused this to be activated. I did look through the options in Chromium but didn't see anything that jumped out at me where I may have done this.

laserman

---

### Post by laserman on 2012-09-04
I think I may have found it. Because Chromium is tied to Google, I can see why this would affect my browser (using Chromium).

On my settings page in Google, I must have set my web browsing to view all pages in https. It is under the General Tab in Settings. After having un-checked that and waiting about a half an hour for settings to take, I no longer get these warnings.

I'll give it a bit for replies, otherwise, I will later mark this solved.

laserman

---

### Post by laserman on 2012-09-04
Okay, now I can mark it solved. Not the route I wanted to take but it did correct my issue.

First, I tested from a live CD, installing chromium-browser. I did not get the errors as I was getting before (unsecure sites). 

Went back to the laptop and purged chromium-browser. Went into terminal and deleted /.config/chromium. 

Installed chromium-browser and did not get any errors. Lost my passwords but was able to maintain my favorites through sync.

laserman

---

### Post by laserman on 2012-09-05
Well, I thought I was out of the woods but I'm not. I'm still getting the "This page has insecure content" and even with a Live CD. Has anyone else experienced this?

laserman

---

### Post by laserman on 2012-09-06
Well, Well, Well...

When I was using the Live CD and any other platform with Chrome or Chromium, I was signing into my account, syncing everything. By syncing everything, it was taking Extensions as well.

One other thing that started happening on the browser that really raised my eyebrows was I was getting redirected on links I would click on. I disconnected my network connection.

I found reading that extensions may cause this...(dirty *&%$#@!).I deleted two extensions from my list. One was Super Sorter (that I added) to sort my bookmarks and the other I have no idea where it came from (probably coat tailed on the previous) and it was Web Movie Plugin 3.0. Super Sorter was not enabled but Web Movie Plugin was. 

I removed both of them. Cleared everything from my history. Cleared all of my passwords and bookmarks (They are on my backup sync). Restarted Chromium and the re-directs disappeared and the insecure content no longer pops up.

Conclusion: Call it what you want, malware, phishing, popups...whatever, can't stand them. Gone now. Will be a bit more vigil before I add any extensions.

I hope this information helps others that may cross something like this.

;)

---

### Post by vasa1 on 2012-09-06
> **laserman said:**
> Well, Well, Well...
... Will be a bit more vigilant before I add any extensions.
...
Absolutely. I keep extensions to a minimum for both Firefox and Chrome. One thing that can help is to see how old and established the extension is. I don't trust the "ratings" and comments on the extension pages. They can be gamed. Some of the decent extensions even have their own forums.

---

