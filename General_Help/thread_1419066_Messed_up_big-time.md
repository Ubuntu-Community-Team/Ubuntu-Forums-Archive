---
title: "Messed up big-time"
date: 2010-03-01
forum: General Help
---

### Post by huggs on 2010-03-01
I was trying to change my background image in my grub bootloader, so I edited 05_debian_theme, and then  did sudo update-grub in terminal, and it appeared that all went well. I didn't even get the " no path specified" error. But then when I rebooted to check out my cool new background, grub put me straight to the black screen where you type stuff, instead of my graphical interface. (the screen where it says something like" Tab lists possible commands..."). Is there any way I can fix this, or did I just completely wreck ubuntu?
I tried the "exit" command, and a few others, out of desperation, the exit command just gave me a 3 second countdown and then put me right back where I was, and none of the other commands I tried helped either.

---

### Post by derrick81787 on 2010-03-01
It's not completely wrecked.  It sounds like something is just wrong with Grub.  I don't know much about Grub, though, so I'm not sure how to help you.  Just know that there is a good chance it can get fixed, and hopefully someone who knows more about Grub will post.

The issue can probably be fixed by booting from the LiveCD, mounting your hard drive, and then undoing the changes you made to 05_debian_theme.  You can either manually undo the changes or just completely replace it with the default.

However, you might want to wait and hear from someone who knows a little more about it than me.  I'd say that it's definitely fixable though.

---

### Post by huggs on 2010-03-01
I installed within Windows, using Wubi, so no live cd either. I dont know how to get back to anywhere that I could replace the theme file even if I had a default one. This sucks, I just got ubuntu just like I wanted it:cry:

---

### Post by derrick81787 on 2010-03-01
> **huggs said:**
> I installed within Windows, using Wubi, so no live cd either. I dont know how to get back to anywhere that I could replace the theme file even if I had a default one. This sucks, I just got ubuntu just like I wanted it:cry:

Humm... unfortunately, I know even less about Wubi than I do about Grub 2.  I've had problems where I've messed up my Grub settings in earlier versions of Ubuntu that used an earlier, and I think very different, version of Grub.  In those situations, I think I usually fixed it from the LiveCD, but at least once, I fixed it from the Grub recovery console.

Here are some links that I found that may or may not help.  I'd like to help more, but anything I do would just be guessing and would probably mess it up more.

[Wubi Guide]("https://wiki.ubuntu.com/WubiGuide")
[Recovering Ubuntu]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") - Note that I don't know how much this affects Wubi users, but it is closer to what I was talking about in my first post.
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=restore+grub+ubuntu+wubi")

Hopefully those will help or someone else will post who knows more about this than I do.

- Derrick

---

