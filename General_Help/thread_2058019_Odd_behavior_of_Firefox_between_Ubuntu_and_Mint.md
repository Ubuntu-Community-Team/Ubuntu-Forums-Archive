---
title: "Odd behavior of Firefox between Ubuntu and Mint"
date: 2012-09-14
forum: General Help
---

### Post by RedRat on 2012-09-14
I have installed Firefox on both 12.04/64 Ubuntu and Mint 13/64. When I go to close Mint Firefox and I have several tabs open, FF asks if I want to save and quit. On Ubuntu, I do not have that option, it is just "Close multiple tabs", it quits and then when restarted, it goes to my home page. 

This is Firefox 15.01 on Ubuntu and Firefox 15.01 on Mint. Supposedly same version. 

Any ideas of what is going on here?

---

### Post by wojox on 2012-09-14
Is everything identical in Edit > Preferences > Tabs?

---

### Post by RedRat on 2012-09-14
> **wojox said:**
> Is everything identical in Edit > Preferences > Tabs?
Yes, they are. Identical. 

Did not have this problem in my old 8.04 or 10.04 Ubuntu.

---

### Post by vasa1 on 2012-09-14
What do you have in about:config?
browser.tabs.warnOnClose;false or browser.tabs.warnOnClose;true ?

Also, do you use some prefs.js in either OS? Are your extensions the same in both OS?

---

### Post by RedRat on 2012-09-14
> **vasa1 said:**
> What do you have in about:config?
browser.tabs.warnOnClose;false or browser.tabs.warnOnClose;true ?

Also, do you use some prefs.js in either OS? Are your extensions the same in both OS?
Ok went in and made those Booleans the same as in Mint. No go. Still the same problem. I went into Extensions and deactivated the Ubuntu extensions, still no go and in fact you cannot even enter "about:config", it tries to go to [www.about.config](www.about.config). I have basically the same extensions loaded in my Mint version. 

Not sure about the prefs.js. Where is that located?

---

### Post by vasa1 on 2012-09-15
> **RedRat said:**
> Ok went in and made those Booleans the same as in Mint. No go. Still the same problem. I went into Extensions and deactivated the Ubuntu extensions, still no go and in fact you cannot even enter "about:config", it tries to go to [www.about.config](www.about.config). I have basically the same extensions loaded in my Mint version. 

Not sure about the prefs.js. Where is that located?

In my case, pref.js here:
/home/vasa1/.mozilla/firefox/ian3h6lc.June/pref.js

Your other point is worrisome. If you can't get about:config to open, that's not good.
I'm away for some hours, but you may want to share the list of your extensions here.
The other thing you can do is to try Firefox in safe mode. That will temporarily disable your extensions.

Even having the same extensions may not mean much because they could be tweaked (unintentionally) differently.

BTW, while the Canonical Firefox is different from the Firefox direct from Mozilla in *some* ways, so is the Mint one, but possibly in *different* ways. I'm think the Mint version has a different search engine by default. Don't know much about that but I understand that changing search engines in Mint Firefox isn't elementary.

---

### Post by vasa1 on 2012-09-15
You could also look at these two links:

Use the Profile Manager to create and remove Firefox profiles
[http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

and

Troubleshoot Firefox issues using Safe Mode
[http://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode](http://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode)

---

### Post by RedRat on 2012-09-15
[vasa1]("http://ubuntuforums.org/member.php?u=449866")
Sorry, I was not clear. After enabling the extensions that were unique to Ubuntu, then I could get to about:config. Note, there is no underscore after "about". I can get in there now. I disabled those that were unique to Ubuntu. My basic extensions are the same ones in both browsers. Since these are new installations, I have not added all that many extensions. While I can't say with absolute certainty that extensions are playing a role, I don't think they are the culprits here. 

I have had another problem with Firefox, in that the Title bar will disappear on occasion, this is quite annoying since I cannot minimize FF. I am beginning to think there might be something wrong with the FF installation. 

BTW, this is a clean install on a brand new hard drive made with the live CD, no carry-overs since the old hard drive was destroyed.

---

### Post by RedRat on 2012-09-15
> **vasa1 said:**
> You could also look at these two links:

Use the Profile Manager to create and remove Firefox profiles
[http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](http://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

and

Troubleshoot Firefox issues using Safe Mode
[http://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode](http://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode)
OK looked into starting FF in safe mode. Still no joy. Still does not give me that option to save and quit the tabs.

---

### Post by vasa1 on 2012-09-15
> **RedRat said:**
> ... Note, there is no underscore after "about". ...
I have had another problem with Firefox, in that the Title bar will disappear on occasion, this is quite annoying since I cannot minimize FF. I am beginning to think there might be something wrong with the FF installation. 
...
No, there isn't any underscore. I wrote **about:config**. Just checked my earlier post.
Second, there's [another report of the frame disappearing]("http://ubuntuforums.org/showpost.php?p=12239672&postcount=2430"). Spooky!

---

