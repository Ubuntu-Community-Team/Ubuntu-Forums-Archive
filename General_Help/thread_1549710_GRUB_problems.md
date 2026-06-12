---
title: "GRUB problems"
date: 2010-08-10
forum: General Help
---

### Post by 71GA on 2010-08-10
Hello i started my computer today and it loads my mainboard screen, post terminal is OKê but after that i get a black screen! 

What could this be? Could it be my GRUB is gone??? --> So because this is my only explanation i tried to reinstall grub. I start linux 10.04 and follow instructions [here]("http://ubuntuforums.org/showthread.php?t=224351") . 

AND IT THEN GETS COMPLICATED...

I type:"sudo grub"
 [COLOR=Blue]it states that grub feature is not installed.[/COLOR]

I type: apt-get install grub [COLOR=Blue]
i install grub to fix upper problem.[/COLOR]

I type:"sudo grub" 
[COLOR=Blue]this is OK i get in >grub marker.[/COLOR] 

I type:"find /boot/grub/stage1" and i get[COLOR=Blue] 
error 15 file not found[/COLOR].

I type: "root (hd0,0)" looks to be ok i get 
[COLOR=Blue]root (hd0,0)

[/COLOR]I type: "setup (hd0)"
[COLOR=Blue]Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists... no[/COLOR]

WHAT IS GOING ON????? I AM CONFUSED!

I allso did a memtest and it is OK!

---

### Post by Elmer Fudd on 2010-08-10
> **71GA said:**
> Hello i started my computer today and it loads my mainboard screen, post terminal is OKê but after that i get a black screen! 

What could this be? Could it be my GRUB is gone??? --> So because this is my only explanation i tried to reinstall grub. I start linux 10.04 and follow instructions [here]("http://ubuntuforums.org/showthread.php?t=224351") . 

AND IT THEN GETS COMPLICATED...

I type:"sudo grub"
 [COLOR=Blue]it states that grub feature is not installed.[/COLOR]

I type: apt-get install grub [COLOR=Blue]
i install grub to fix upper problem.[/COLOR]

I type:"sudo grub" 
[COLOR=Blue]this is OK i get in >grub marker.[/COLOR] 

I type:"find /boot/grub/stage1" and i get[COLOR=Blue] 
error 15 file not found[/COLOR].

I type: "root (hd0,0)" looks to be ok i get 
[COLOR=Blue]root (hd0,0)

[/COLOR]I type: "setup (hd0)"
[COLOR=Blue]Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists... no[/COLOR]

WHAT IS GOING ON????? I AM CONFUSED!

I allso did a memtest and it is OK!

After sudo apt-get install grub

```
sudo update-grub
```

then reboot.

---

### Post by drs305 on 2010-08-10
If you are getting the Grub menu and then end up with a "grub" or "rescue" prompt it is probably Grub-related. If you get a blank screen with just a cursor, you probably are having other problems.

If it's Grub-related, posting the results of this script should give us the information we need to troubleshoot it. Place the contents with "code" tags, which you generate by pressing the # icon in the post's menu.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Note: You very well could be using Grub2, whose package is "grub-pc" and is installed differently than legacy grub. We'll know when we see the script results.

---

