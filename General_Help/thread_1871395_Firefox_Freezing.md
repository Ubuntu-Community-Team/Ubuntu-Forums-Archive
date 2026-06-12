---
title: "Firefox Freezing"
date: 2011-10-28
forum: General Help
---

### Post by mrdave100 on 2011-10-28
Newbie here.  I'm running Ubuntu 10.04 and just recently Firefox has been freezing up on me.  I'm able to move the mouse, but I can't do anything on the computer.  In windows I used to ctrl+alt+delete and go into task manager and shut down the application that was frozen.  Is there a way to do something like that in Ubuntu?  I don't know what else to do but hit the power button and restart the computer.

---

### Post by hansdown on 2011-10-28
Hi, mrdave100.

Are you able to click the close button on firefox?

It should give you a prompt, to force quit.

---

### Post by mrdave100 on 2011-10-28
No, the close button doesn't work or give me a force quit option.

---

### Post by Alan.Brown on 2011-10-28
Alt + PrtScr + B will reboot your computer cleanly

Check here

[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

HTH

Alan

---

### Post by hansdown on 2011-10-28
Haven't seen that for a while,Alan.Brown.

Referring to, alt+ prtscr+ b.

The reisub command, "may" be preferable.

---

### Post by mrdave100 on 2011-10-28
Thanks!!  It just froze up 2 more times since I made my first post.  The netflix website seems to one culprit.  It's aggravating to say the least.  I just hooked up my new ASUS monitor tonight, but I find it hard to believe that is somehow related, but I guess it could be.  I'm just tried Chromium and it worked fine.  I may surf with Chromium awhile and see what happens.  I don't mind switching browsers, but after using Firefox the last several year, I've gotten very comfortably with it.

---

### Post by hansdown on 2011-10-28
> **mrdave100 said:**
> Thanks!!  It just froze up 2 more times since I made my first post.  The netflix website seems to one culprit.  It's aggravating to say the least.  I just hooked up my new ASUS monitor tonight, but I find it hard to believe that is somehow related, but I guess it could be.  I'm just tried Chromium and it worked fine.  I may surf with Chromium awhile and see what happens.  I don't mind switching browsers, but after using Firefox the last several year, I've gotten very comfortably with it.

One firefox addon, that I use, is;

```
ghosterly
```

It actively blocks "third party cookies".

One of the the most blocked cookies, is; google analitics; every mouse click.

---

### Post by Alan.Brown on 2011-10-29
I looked for "ghosterly" and found "ghostery"


Alan

---

### Post by oldtimer7777 on 2011-10-29
> **mrdave100 said:**
> Newbie here.  I'm running Ubuntu 10.04 and just recently Firefox has been freezing up on me.  I'm able to move the mouse, but I can't do anything on the computer.  In windows I used to ctrl+alt+delete and go into task manager and shut down the application that was frozen.  Is there a way to do something like that in Ubuntu?  I don't know what else to do but hit the power button and restart the computer.

Sometimes when this happens I just clear everything out with bleachbit...

sudo apt-get install bleachbit
sudo bleachbit

make sure not to delete your passwords and stuff... otherwise clean it out with that and you should have better results..

---

### Post by hansdown on 2011-10-29
> **Alan.Brown said:**
> I looked for "ghosterly" and found "ghostery"


Alan

Yes.

Sorry for the typo.

---

### Post by Alan.Brown on 2011-10-29
"ghostery" seems to be very good - cleans up the screen a lot

Thanks

Alan

---

### Post by hansdown on 2011-10-29
> **Alan.Brown said:**
> "ghostery" seems to be very good - cleans up the screen a lot

Thanks

Alan

It will open your eyes, to what a mouse click will invite.

Cheers.

---

### Post by little_penguin on 2011-10-30
I am currently using Lucid 10.04 and had the same problem with Firefox freezing and locking up the computer. The version it uses is 3.6 if I recall, probably a bit too old. After installing the latest Firefox 7 (from the Mozilla Firefox website), the freezing problem seems to have gone away.

I followed the instructions from here: [http://www.libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint](http://www.libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint)

Edit: I take this back, the problem with freezing and a non-responding system is still there after upgrading Firefox :(. I suspect it might also be due to overheating? This netbook gets extremely hot very quickly. Hope someone else has some ideas. Back to the drawing board...

---

### Post by lovinglinux on 2011-10-30
See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) and [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by little_penguin on 2011-10-30
This is just to say I decided to install the Ubuntu Netbook Edition 10.04, installed all the updates and it's much more responsive than the standard desktop version was with this hardware, not surprising really. I shouldn't have been using the desktop version on this Samsung NP N140 netbook, due to its low specs. So far I've had no system freezing...

---

