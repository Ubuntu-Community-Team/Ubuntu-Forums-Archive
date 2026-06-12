---
title: "Firefox crashes in Ubuntu 10.04 - workaround didn't work"
date: 2010-05-27
forum: General Help
---

### Post by caradeporra on 2010-05-27
I believe it has something to do with flash and something called no-script.

If you google "firefox 10.04 bryce harrington" you can come across what is supposedly a fix for this, however this did not relieve my issue. The issue remains that I can open firefox, go to google and it's ok. Gmail, Youtube, and many other websites immediately close firefox - no error messages or anything. I started firefox in safe mode with no add-ons and deleted all extensions, pages, user settings etc. and it still happens.

This is a MAJOR issue, because if I can't run firefox I am in trouble - I also use opera, but that is because I have, well had, an issue with opening multiple instances of firefox - as in, I could not open more than one instance. That is another issue for another day, right now I JUST NEED FIREFOX TO FUNCTION!

Any help on this would be greatly appreciated as I have been googling for several days now trying to figure this thing out to no avail.

---

### Post by lovinglinux on 2010-05-27
> **caradeporra said:**
> I am having what i believe is the same issue, it has nothing to do with yahoo mail.  I believe it has something to do with flash and something called no-script.

NoScript is a Firefox extension that prevents untrusted web sites from running scripts. It can block flash content too.

> **caradeporra said:**
> If you google "firefox 10.04 bryce harrington" you can come across what is supposedly a fix for this, however this did not relieve my issue.

Please be careful when following tutorials from random sites. If you followed that tutorial, then you have included a PPA repository to update xorg server from a third-party source. If that didn't fix your problem,  then you should disable that PPA and restore the default xorg.

I read the site that talks about that problem. I have no problems whatsoever with NoScript crashing Firefox and I haven't seen any threads on these forums reporting that behavior. There are threads reporting crashes, but several of them are related to libmoon package (Silverlight). If the user has libmoon installed, then removing it usually fixes the problem. Try that.

> **caradeporra said:**
> This is a MAJOR issue, because if I can't run firefox I am in trouble - I also use opera, but that is because I have, well had, an issue with opening multiple instances of firefox - as in, I could not open more than one instance.

Firefox doesn't allow to open multiple instances. If you click the Firefox launcher while Firefox is already opened, it will open a new window. You can force Firefox to open a new instance by using the command below. Nevertheless, you won't be able to use the same profile already in use. You need to open it with a second profile:

```
firefox -no-remote -P
```

> **caradeporra said:**
> ...right now I JUST NEED FIREFOX TO FUNCTION!

What version of Ubuntu, Firefox and Flash you are running? Is your system 32bit or 64bit?

---

### Post by caradeporra on 2010-05-28
> **caradeporra said:**
> You were very correct on this.  I had installed libmoon several months back to see what it was about (needless to say it didn't work), however this issue only begun when I updated to 10.04, as 9.10 had no issues like that.  I would have NEVER discovered that it was libmoon causing that - after uninstalling Firefox is back to it's normal self.  

  Thank you very much.  Now I will begin my google search to rever back the xorg.  thanks again!

> **lovinglinux said:**
> I'm not sure. I followed that tutorial on a Virtual Machine to see what files were changed by that PPA. The files were *xserver-common* and *xserver-xorg-core*. Then I disabled the PPA and tried to re-install the packages, but apt wouldn't allow me to do so.

I guess you will need to wait for a new update, unless someone else knows a solution.

This is from another thread, I posted it in this one under it's own thread title in case other users are having these problems.  If anyone knows how to revert back to original xorg-server please post.

This is now solved - Solution (thanks lovinglinux) is to uninstall libmoon packages and restart firefox.

---

### Post by barney385 on 2010-05-28
Yep. I've been having the same problem with No-Script too.

It's now disabled, and probably on it's way to a permanent deletion.

It took me 3 days to figure out what was going on since I'd only have htep warnings in my logs with no description of the culprit.

Since I disabled it, everything works fine now.

Does anyone know if this is just a x86 problem?

---

### Post by Irishpolyglot on 2010-05-31
This issue is still happening for me since upgrade. I also applied the advice in the link mentioned. (BTW did you find what code to run to restore the default xorg? I should get on that soon, but I'm not sure)
I had installed silverlight before, but removed it (plugin silverlight + libmoon in Synaptec) and noscript was never on my system.

What's strange is that Gmail will work fine for me sometimes and then be impossible to load others. I'm getting really sick of using it in HTML or in other browsers. Is there anything else left to try?

Thanks!!

---

### Post by lovinglinux on 2010-05-31
> **Irishpolyglot said:**
> This issue is still happening for me since upgrade. I also applied the advice in the link mentioned. (BTW did you find what code to run to restore the default xorg? I should get on that soon, but I'm not sure)
I had installed silverlight before, but removed it (plugin silverlight + libmoon in Synaptec) and noscript was never on my system.

What's strange is that Gmail will work fine for me sometimes and then be impossible to load others. I'm getting really sick of using it in HTML or in other browsers. Is there anything else left to try?

Thanks!!

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Irishpolyglot on 2010-05-31
Thanks but I've tried those "general" fixes, several times and for a couple of hours, and the problem persists despite tests and a lot of restarting firefox. Maybe I should just downgrade back to my previous version of Firefox.. or is the problem within Ubuntu 10.04 itself somehow?

---

### Post by lovinglinux on 2010-05-31
> **Irishpolyglot said:**
> Thanks but I've tried those "general" fixes, several times and for a couple of hours, and the problem persists despite tests and a lot of restarting firefox. Maybe I should just downgrade back to my previous version of Firefox.. or is the problem within Ubuntu 10.04 itself somehow?

Please create a new thread for your issue. Also tell what version of Firefox you are using and in which conditions the problem occur.

---

### Post by caradeporra on 2010-05-31
irish,

  If you are having the same issues, and the general troubleshooting doesnt help maybe you should investigate the libmoon package still.  Perhaps when you uninstalled it you didn't do a complete removal?  Also try going to system - administration - computer janitor and remove the unnecessary libs that are still on there, then try again.

---

### Post by deyanyosifov on 2010-09-10
I also had the same problem and the libmoon package was never installed on my system. After a lot of trying this and that I just got a solution - a quite easy one actually:
1.Open a terminal and go to your home directory if not already there.
2. Issue the following command: sudo rm -r .mozilla

That's it! :D

Note: All your customized settings in firefox will be gone. You can save the list of your favourite sites in a file beforehand and then recover it after the sudo rm -r .mozilla command.

---

### Post by lovinglinux on 2010-09-10
> **deyanyosifov said:**
> I also had the same problem and the libmoon package was never installed on my system. After a lot of trying this and that I just got a solution - a quite easy one actually...

Please avoid recommending that. First of all, there is no need to use sudo, which is only necessary for folders/files you don't have writing permissions. Additionally, the **sudo rm -r** command is **dangerous**. If the user runs it incorrectly, he can lose everything and make his system unusable. Besides, there is always the possibility of fixing Firefox without destroying personal data and I recommend orienting the user to create a new profile first, to see if it really fixes the problem, before deleting the mozilla folder. See Firefox's [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) and [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html) tutorials.

---

