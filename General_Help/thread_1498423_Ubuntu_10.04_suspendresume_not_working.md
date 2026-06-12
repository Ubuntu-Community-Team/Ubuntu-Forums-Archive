---
title: "Ubuntu 10.04 suspend/resume not working"
date: 2010-05-31
forum: General Help
---

### Post by fprintf on 2010-05-31
> **fprintf said:**
> Sorry to say but I am having identical issues to those posting previously. Mine is an old IBM T30 with an ATI Radeon video card. It took me only a few minutes to get sleep on Jaunty working on it, mostly the removal of scripts that had previously been necessary (from the Thinkpad WIKI as I recall) to be stored in /etc/pm/sleep.d

I am super bummed because this machine stays in sleep in my office except when I need to quickly check the 'Net. Powering it up/off each time is a serious drag. I am wondering if degrading back to Jaunty will be required.

and then a little digging and investigation pointed to the video quirk handling system/HAL:

> **fprintf said:**
> Ok, I am doing some digging into this and looking at my logs from prior to the install, when the suspend/resume was working and now. It appears that the video quirk handling system is not working. For example, in my old pre-Lucid Lynx pm-suspend.log there is a line:


/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-radeon-off 
success.

This line does not appear in any logs subsequent to the new 10.04 install. Now the question is, how do I fix it so that HAL sends the appropriate quirk?  Help??

finally I tried moving the video quirk handling into the userscript space with some success in suspend, but not in resume.

> **fprintf said:**
> I really think this has something to do with HAL or the video quirks not being called correctly. If I copy 98video-quirk-db-handler from /usr/lib/pm-utils/sleep.d over to /etc/pm/sleep.d (the user space settings for suspend/resume I think), the suspend works perfectly. That is, my backlight goes off like it is supposed to.

However the resume does not work properly. I probably need to write a quick 21radeon script that turns the screen on properly on resume. Right now, like so many others, I get either a black screen with the backlight on, or it will come up with my background image but none of the gnome menubars. 

Thanks for any help troubleshooting this. I see lots of bugs are filed over the course of the past few years. I have not filed one yet.

Like I and many others have said in the thread, suspend/resume is not working and any help or troubleshooting would be appreciated. I have the logs available to prove what is going on behind the scenes if necessary.

---

