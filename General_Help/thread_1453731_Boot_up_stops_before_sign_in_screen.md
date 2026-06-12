---
title: "Boot up stops before sign in screen"
date: 2010-04-13
forum: General Help
---

### Post by sandlizard on 2010-04-13
I have Ubuntu 9.10 remix on my Dell mini 10, dual booting with windows xp. Everything worked fine, not a single hitch. Then this week I turned the computer on, and Ubuntu goes through the boot sequence and I get a blank screen before the sign on screen. Same result each time. I've worked with Ubuntu for about a year, but have never had boot problems and am really clueless on what to do here. I've searched for this problem without results. Thanks for any suggestions.

---

### Post by davidpbrown on 2010-04-13
Try booting into Recovery of the latest version.. from memory it's pressing Escape while grub is counting down at the start. From the little I know, that seems to be a grab of the last good boot.

---

### Post by quadproc on 2010-04-13
> **sandlizard said:**
> I have Ubuntu 9.10 remix on my Dell mini 10, dual booting with windows xp. Everything worked fine, not a single hitch. Then this week I turned the computer on, and Ubuntu goes through the boot sequence and I get a blank screen before the sign on screen. Same result each time...
I think that you mean that your system quits displaying anything at the time just before it should have presented the login screen.

Did you happen to notice if you saw any spiel from Windows about "fixing" something on the disk (I am assuming that you ran Windows before the failed Ubuntu boot.)?  I had that happen to me when I booted Windows after using Ubuntu.  I don't know what Windows "fixed" but it caused some damage to the Ubuntu file system - I had to run fsck to fix that.  Since then I do not boot Windows.  In fact, as soon as I confirm that grub is not depending on anything on that disk, that entire disk will be repartitioned so that it can do something useful for me.

When you said that Ubuntu goes through the boot sequence, did you mean that you get the usual BIOS stuff, then you get the grub screen which lets you choose which Ubuntu version to load, and then the screen goes black?  If so, the problem could be due to damage to the boot information that grub uses, or to the kernel, or to the X windows system, or ...  But at least you know that grub is there and runs.

If you are getting the choice of what to boot, I suggest trying the recovery version from the menu options.  This, if it boots, will give you a command line interface which you can use to help figure out what went wrong.  Especially interesting are the logs. At the CLI you could do```
 cd /var/log
tail -n 24 syslog
```to see the last 24 entries in the system log.  Those entries will contain the date and time so that you can tell if they coincide with when your startup problem occurred.

Also, from the recovery mode, you can do any of the terminal commands such as cp, ls, cd, more, less, cat, and so forth.  These might help.

quadproc

---

### Post by sandlizard on 2010-04-13
> **quadproc said:**
> I think that you mean that your system quits displaying anything at the time just before it should have presented the login screen.

Did you happen to notice if you saw any spiel from Windows about "fixing" something on the disk (I am assuming that you ran Windows before the failed Ubuntu boot.)?  I had that happen to me when I booted Windows after using Ubuntu.  I don't know what Windows "fixed" but it caused some damage to the Ubuntu file system - I had to run fsck to fix that.  Since then I do not boot Windows.  In fact, as soon as I confirm that grub is not depending on anything on that disk, that entire disk will be repartitioned so that it can do something useful for me.

When you said that Ubuntu goes through the boot sequence, did you mean that you get the usual BIOS stuff, then you get the grub screen which lets you choose which Ubuntu version to load, and then the screen goes black?  If so, the problem could be due to damage to the boot information that grub uses, or to the kernel, or to the X windows system, or ...  But at least you know that grub is there and runs.

If you are getting the choice of what to boot, I suggest trying the recovery version from the menu options.  This, if it boots, will give you a command line interface which you can use to help figure out what went wrong.  Especially interesting are the logs. At the CLI you could do```
 cd /var/log
tail -n 24 syslog
```to see the last 24 entries in the system log.  Those entries will contain the date and time so that you can tell if they coincide with when your startup problem occurred.

Also, from the recovery mode, you can do any of the terminal commands such as cp, ls, cd, more, less, cat, and so forth.  These might help.

quadproc

You have described exactly what is happening. Grub comes up, I get the grub selection screen, and can choose kernels, same results with each though. And yes I can boot into recovery. I just have no idea what to do when I get there. I did not notice windows fixing anything, in fact in retrospect  I think this started after a fairly significant Ubuntu update. 

I will look at the logs and try the fix disc option suggested. Thanks!

---

### Post by sandlizard on 2010-04-13
Problem update. I just turned the computer on and now it boots straight into windows xp. No grub, no hint there is Ubuntu even on the system. 
I think I will wait for 10.10 to come out the last week in April, I have all my data backed up, and format the whole drive and put the new remix on the entire drive, thanks for the help guys. I only did the dual boot to "try before I buy (of course you don't buy Ubuntu)". I love the netbook remix and will just wait for the new version. Again thanks guys. 

I guess if there is a fairly simple recovery option, I would try it. I've got the install disk and a portable usb dvd drive. It would be good practice/experiment for future problems.

---

### Post by sandlizard on 2010-04-13
Did complete reinstall of Ubuntu and restored data. Working fine now, we'll see what happens.

---

