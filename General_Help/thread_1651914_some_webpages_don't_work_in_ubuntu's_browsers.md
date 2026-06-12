---
title: "some webpages don't work in ubuntu's browsers"
date: 2010-12-23
forum: General Help
---

### Post by watgrad on 2010-12-23
hello - I've run into problems in some websites where Chrome, Chromium, Firefox and Konqueror will not render the pages correctly (yes, I've installed and tried them all).  I've tried on three different computers with dual boot Windows and Ubuntu and get the same results...If I boot into windows, I can browse the pages with no problems,  
however, in Ubuntu these pages just hang at certain points...

Is there some setting I can adjust to improve web performance?

Here are two sites for example:
[http://www.sheetmusicplus.com/](http://www.sheetmusicplus.com/)
Try clicking on one of the instrument links in the navigation bar...no response.

Or

[http://www.hco-on.ca/english/Search/](http://www.hco-on.ca/english/Search/)
browse by location, a warning sign appears, click 'agree' and wait endlessly...

Why would these pages work correctly on Windows, but not in Ubuntu?
I HATE having to boot into Windows, so if I can avoid it I will!

Any ideas?

---

### Post by sammiev on 2010-12-23
> **watgrad said:**
> hello - I've run into problems in some websites where Chrome, Chromium, Firefox and Konqueror will not render the pages correctly (yes, I've installed and tried them all).  I've tried on three different computers with dual boot Windows and Ubuntu and get the same results...If I boot into windows, I can browse the pages with no problems,  
however, in Ubuntu these pages just hang at certain points...

Is there some setting I can adjust to improve web performance?

Here are two sites for example:
[http://www.sheetmusicplus.com/](http://www.sheetmusicplus.com/)
Try clicking on one of the instrument links in the navigation bar...no response.

Or

[http://www.hco-on.ca/english/Search/](http://www.hco-on.ca/english/Search/)
browse by location, a warning sign appears, click 'agree' and wait endlessly...

Why would these pages work correctly on Windows, but not in Ubuntu?
I HATE having to boot into Windows, so if I can avoid it I will!

Any ideas?

Just tried the 1st address posted and had no troubles with the instrument links in the navigation bar. I would say you are missing a plug-in. Check to see if you have the java and flash plug-ins.

---

### Post by dcstar on 2010-12-23
> **sammiev said:**
> Just tried the 1st address posted and had no troubles with the instrument links in the navigation bar. I would say you are missing a plug-in. Check to see if you have the java and flash plug-ins.

Both sites work fine for me using Firefox. They use Javascript so if that is turned off or blocked then they will be basically useless.

---

### Post by djeikyb on 2010-12-23
Works for me.
Chromium 10.0.620.0 (70025) Ubuntu 10.04

---

### Post by watgrad on 2010-12-24
Thanks for your support!

I checked the plugins

I have IcedTea6 for Java
and
Shockwave Flash 10.3 for flash files

both are enabled, but no access to these sites - could there be another system issue/problem?

---

### Post by johnmay on 2010-12-24
I have noticed that with Firefox some sites don't work well unless the latest version of java / flash is installed.

---

### Post by watgrad on 2010-12-24
Well,
I updated Java, but that didn't help...

---

### Post by pricetech on 2010-12-24
Both work for me in Opera.

Try enabling partner repositories and installing Java (search for sun-java6-plugin) and Ubuntu Restricted Extras.

See if that helps.

---

### Post by watgrad on 2010-12-24
sigh - no change...  

I don't think it can be the plugins - I can access the javascript menus - but when I click on menu items or buttone - ubuntu endlessly loads the next page.

None of the browsers in ubuntu will render the pages correctly - even internet explorer running in awindows guest through VirtualBox won't render the pages correctly.  But if I reboot directly into Windows - I have no problems with the webpages...

It is strange that it also effects my laptops (one HP - the other MacBook) in exactly the same way...

---

### Post by matt_symes on 2010-12-24
Hi

Sorry mate. Works for me in both chrome and firefox. It must be an issue with your setup.

Kind regards

---

### Post by Frogs Hair on 2010-12-24
Both sites work with Firefox and Opera .

---

### Post by djeikyb on 2010-12-24
> **watgrad said:**
> It is strange that it also effects my laptops (one HP - the other MacBook) in exactly the same way...Are you running _any_ kind of adblocking software? Like..privoxy? Adblock+? Any sort of firewall on the machines? Any sort of firewall on the router? It sounds like Ubuntu is not your problem, especially if other OSes on the network are having similar issues. Something in your particular configuration, or external to the computer is messing you up. Can you temporarily bypass the router and plug directly into the net?

---

### Post by watgrad on 2010-12-24
> **djeikyb said:**
> Are you running _any_ kind of adblocking software? Like..privoxy? Adblock+? Any sort of firewall on the machines? Any sort of firewall on the router? It sounds like Ubuntu is not your problem, especially if other OSes on the network are having similar issues. Something in your particular configuration, or external to the computer is messing you up. Can you temporarily bypass the router and plug directly into the net?

No firewall on my computer - but the router has a firewall.  I tried what you suggested and connected directly to the DSL modem.  I could browse the pages with no problem!  Thanks. :D

Now - I need to figure out how to adjust the firewall on the router to stop interfering with Ubuntu...

---

### Post by pikachu714 on 2010-12-24
I think things work best in google chrome because it already has all the plug-ins. Are you behind a proxy or is your internet filtered? Sometimes that can mess things up with webpages when it tries to find external javascript, flash, or css because that page is blocked or is not on the proxy server.

---

### Post by watgrad on 2010-12-29
so - I've discovered that my problem is with my wireless router...for some reason it is blocking some webpages in ubuntu only - not in windows...strange...does ubuntu use different ports when browsing internet than windows?

Anyway - my router is a Dlink WBR-1310...

I'm just wondering - those of you not having trouble with web browsing in ubuntu - what wireless router do you use?  I want to make sure to get one that works!

---

### Post by karthick87 on 2010-12-29
Try clearing your browser caches and then try again..Also look at the following link

[http://support.mozilla.com/kb/Basic+Troubleshooting](http://support.mozilla.com/kb/Basic+Troubleshooting)

---

### Post by theozzlives on 2010-12-29
Some sites are made for MSIE only. You can add the user agent switcher addon to make firefox look like MSIE. Also after reading the Thread, go to terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```
you'll get flash, java, and some other goodies.

---

### Post by watgrad on 2010-12-29
Thanks theozzlives and karthick87 - I appreciate your suggestions.

The user agent plugin for firefox didn't help with this problem - but I'm glad you told me about it for future reference.

I have tracked this down to my router - if I bypass it, I have no trouble on the internet.  When I use the router - some webpages fail to load... My router is a cheap one - so I cannot adjust settings in it too much...I think I will have to get a new router...

---

### Post by djeikyb on 2011-01-17
1. Outta curiousity, what brand and model router are you using? If you do replace it, I highly recommend the Linksys WRT-54GL running DDWRT firmware. I've bought six or seven of these for myself and family. They're very stable and relatively easy to configure.

2. Did you ever try running your browser with a clean profile? Delete, or at least rename, your preferences folder (ie ~/.mozilla or ~/.firefox) and relaunch the browser. Could be something got corrupted.

---

### Post by watgrad on 2011-01-17
Hi - it is a d-link wbr-1310
An old model that has worked well in the past - but for some reason prevents certain webpages from loading properly.  It has limited options to control it's built-in firewall...so I think I will replace it.  Thanks for your suggestion - I will price those routers.

---

