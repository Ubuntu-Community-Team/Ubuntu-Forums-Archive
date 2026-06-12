---
title: "No shutdown/restart etc in Ubuntu 9.10 upgrade"
date: 2009-11-19
forum: General Help
---

### Post by stickerpoint on 2009-11-19
Hello,

Does anyone else have the same problem? I upgraded to Ubuntu 9.10, and I have no shutdown/reboot option on the gnome desktop. I have of course an on/off button on the computer:), but it seems strange to me.

Kind regards

---

### Post by prem1er on 2009-11-19
Not sure what is causing your problem (as this is not normal), but you can always open a terminal and do...

```
sudo reboot
```

or 

```
sudo shutdown -h now
```

while you're waiting for a solution.

---

### Post by Usufruct on 2009-11-19
> **stickerpoint said:**
> Hello,

Does anyone else have the same problem? I upgraded to Ubuntu 9.10, and I have no shutdown/reboot option on the gnome desktop. I have of course an on/off button on the computer:), but it seems strange to me.

Kind regards

Try clicking on your username up in the top right corner of your screen (on a default install).  You should find what you need there.

---

### Post by prem1er on 2009-11-19
> **Usufruct said:**
> Try clicking on your username up in the top right corner of your screen (on a default install).  You should find what you need there.

Yes, definitely try that first. But as you mentioned you were upgrading from a previous version, I had assumed that you knew where to look. Sorry.

---

### Post by stickerpoint on 2009-11-21
Hello,

I did know where to look, only that there is no user name at the top-right-hand corner - no other corners either I'm afraid, but I don't take the suggestion to look there as a personal affront! :D. This is an upgrade I made a few weeks ago on an eee-pc 9.10 Gnome 2.28.1. The time and date are in the upper right-hand corner.

Could anyone please post a screenshot of their desktop? Mine is attached...

Kind regards

---

### Post by ukapolog on 2009-11-21
Funnily enough when I uograded to Ubuntu 9.10 I had exactly the same problem but it settled down within a week or two and now I can mostly  restart or shut down as normal - no real problem. Why this problem sorted itself out I have no idea.

---

### Post by Scott753 on 2009-11-21
I'm still a newbie here, but I just installed 9.10 last week and my desktop looks nothing like yours. I didn't really change anything around, so that may account for the difference, or you may have a different version of gnome.

I just thought I'd post my desktop in case that helped you out.

---

### Post by running_rabbit07 on 2009-11-21
Roght click on a panel and click add to panel then select the power button to add.

---

### Post by YosefKaro on 2009-11-21
With wubi, this is a known bug for which a fix has been committed.  Maybe the update has already been made available which would explain why someone would have this problem after upgrading to Karmic and then it mysteriously goes away. ;)

But it looks like your problem is different.  It looks like the theme that you are using is not showing where your name should appear in the upper-right-hand-corner.  Try switching back to the original theme or try using different theme.

-Yos

---

### Post by running_rabbit07 on 2009-11-21
> **YosefKaro said:**
> With wubi, this is a known bug for which a fix has been committed.  Maybe the update has already been made available which would explain why someone would have this problem after upgrading to Karmic and then it mysteriously goes away. ;)

But it looks like your problem is different.  It looks like the theme that you are using is not showing where your name should appear in the upper-right-hand-corner.  Try switching back to the original theme or try using different theme.

-Yos

Changing themes doesn't usually change where buttons are placed. I believe either by operator error or from the upgrade, the button was deleted. As I mentioned above, there is a way of adding the button via right clicking the panel.

---

### Post by stickerpoint on 2009-11-21
Well, thank you all for the ideas - it seems that the rabbit had the right answer. After right-clicking carefully in many places in the top status bar, I found the right area to add an icon. A shutdown icon was available, so now all is well! It might of course have been human error on upgrade (although there was no human intervention!), but in any event I have added the necessary. This icon was present on the previous version of Ubuntu, so I imagine that it is/was a bug in the upgrade program as Yosef wrote. I find 9.10 not as stable at present as the 9.04 or even 8.10, but that's only my opinion.

Thanks again!

---

### Post by running_rabbit07 on 2009-11-21
> **stickerpoint said:**
> Well, thank you all for the ideas - it seems that the rabbit had the right answer. After right-clicking carefully in many places in the top status bar, I found the right area to add an icon. A shutdown icon was available, so now all is well! It might of course have been human error on upgrade (although there was no human intervention!), but in any event I have added the necessary. This icon was present on the previous version of Ubuntu, so I imagine that it is/was a bug in the upgrade program as Yosef wrote. I find 9.10 not as stable at present as the 9.04 or even 8.10, but that's only my opinion.

Thanks again!

Your welcome, I wasn't pointing fingers, I've accidentally deleted my trash bin many times. I think they'll get Karmic ironed out soon, hang in there and have fun.:D

---

