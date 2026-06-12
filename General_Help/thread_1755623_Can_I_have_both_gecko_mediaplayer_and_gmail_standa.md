---
title: "Can I have both gecko mediaplayer and gmail standard view in Firefox 4 ?"
date: 2011-05-11
forum: General Help
---

### Post by FrostBlue on 2011-05-11
Hi ,
I have set an option for Gecko Mediaplayer to work properly on Apple.com in firefox 4.
I think it was something like this

*QuickTime/7.6.2 ( qtver=7.6.2 ; os=Windows NT 5.1Service Pack 3 )*

Now gmail doesn't detect Firefox and gives me the Basic html view , asks me to upgrade to Firefox.

Is there someway I can have both working ?

---

### Post by lovinglinux on 2011-05-11
What exactly happens when you try apple.com with gecko-mediaplayer, without the hack?

---

### Post by FrostBlue on 2011-05-12
It doesn't play the trailers at apple.com. Also it doesn't really work on other websites. Firefox says additional plugin required when trying to watch .mov files. Adding the value above in about:config makes it work as expected.

I check my browser agent at this link[ http://www.wannabrowser.com/ ]("http://www.wannabrowser.com/")and it says Windows NT and not Linux. I think this is the problem , gmail cant detect Firefox 4 b'cuz of this.

---

### Post by lovinglinux on 2011-05-12
> **FrostBlue said:**
> It doesn't play the trailers at apple.com. Also it doesn't really work on other websites.

Please post the results of the following command:

```
cat ~/.mozilla/firefox/**/pluginreg.dat 
```

> **FrostBlue said:**
> Firefox says additional plugin required when trying to watch .mov files. Adding the value above in about:config makes it work as expected.

If changing the user agent works, then use [User Agent Switcher]("https://addons.mozilla.org/en-US/firefox/addon/59/") to easily switch that depending on the site you visit.

---

### Post by FrostBlue on 2011-05-12
Sorry I couldn't paste the output here as the forum gives me an error saying you have added 10 images,etc..
But I have pasted the output here [http://pastebin.com/2LYStAfG]("http://pastebin.com/2LYStAfG")
And I will look into Agent Switcher and see if it works for me.

---

### Post by lovinglinux on 2011-05-12
> **FrostBlue said:**
> Sorry I couldn't paste the output here as the forum gives me an error saying you have added 10 images,etc..
But I have pasted the output here [http://pastebin.com/2LYStAfG]("http://pastebin.com/2LYStAfG")
And I will look into Agent Switcher and see if it works for me.

Your report is fine. I don't know why it doesn't play. Perhaps you are missing some gstreamer codecs.

---

### Post by FrostBlue on 2011-05-13
I removed the string from config and tried Apple site. The gecko player window shows up but doesn't load the video. The bar doesn't move at all.
And I checked other websites , they seem to work fine now.

So its only Apple website.

I kinda need Gmail in Standard view so I am gonna keep it this way for sometime and try for an alternative.

---

