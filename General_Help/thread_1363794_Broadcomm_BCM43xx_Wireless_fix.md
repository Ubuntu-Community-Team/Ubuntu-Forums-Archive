---
title: "Broadcomm BCM43xx Wireless fix"
date: 2009-12-24
forum: General Help
---

### Post by admiralspark on 2009-12-24
Hello all!
Thanks to my daredevil approach with experimenting in Ubuntu, I've managed to nuke the OS a few times. I've done things such as reconfigured the GRUB menu so that it accidentally wouldn't boot, mounted an mp3 player as one of the sda's (I believe; anyway, after I unplugged the thing and rebooted my laptop, it freaked because the harddrive couldn't be found). Anyways, moving on.
The only major flaw I've ever found in Ubuntu was the fact that my Broadcomm wireless card never worked in a fresh install. Following [alex_kent_18]("http://ubuntuforums.org/member.php?u=359707")'s instructions at [html]http://ubuntuforums.org/showthread.php?t=766560[/html], I was able to fix it, however I felt a need to make that half-hour process even shorter. Plus, I wanted to try my hand at putting together bash scripts into something useful.
I have the link to my project on my blog: [html]http://admiralspark.blogspot.com/2009/12/broadcomm-wireless-fix-package.html[/html]So, what I've done is basically taken his series of commands and run them together into seven separate bash files (for now). I tested them today following my included instructions, they worked perfectly for me.:guitar: 

The reason I'm writing here is because this is still a 7-step process. I want to eventually combine all of the scripts into one file which can be executed by a newbie with relatively little hassle. I know the 43xx series wireless cards are quite common, so this has the potential to be helpful to them. My questions:

1) How long can a bash (.sh) file be before it causes problems, or is there a limit?
2) If I was to list all the commands together, hitting enter after each one, will they go in order with no problems? Meaning, is there some other notation I don't know of yet that makes sure the processes run in order, not interfering with each other (like I've seen the && used, but I don't think that's useful here).

Basically, is there a how-to for writing bash scripts? Bourne Again SHell doesn't look too complicated, and if it's as easy as it seems I can see potential for automating several tasks.....

---

### Post by focwiz on 2009-12-24
Just download the Broadcom STA wireless driver from

[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

and all is well?

---

### Post by admiralspark on 2009-12-25
though it's off topic, that driver didn't work at all. I have a 4318, not one of the supported types (though one would assume it'd work fine).

---

