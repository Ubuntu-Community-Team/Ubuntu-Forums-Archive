---
title: "grub rescue prompt, how to fix?"
date: 2010-08-20
forum: General Help
---

### Post by DragonDon on 2010-08-20
Greetings all,

Been wandering around Google to figure out how to fix this issue and am at a loss.  Found some direction on how to get more info that someone here may be able to understand and use to help me get through this.

Background:

Dell Dimension 1100
1GB of Ram
2.8GHz Celeron D
Ubuntu 10.04 LTS
250GB HD (sda1)
160GB HD (sdb1 I believe)

Everything was seemingly working 'ok' (had other issues...like Flash really sucking for playback....'marginal' in FF, crappy in Chrome...) but then FF started acting wierd.  As in not responding to clicks despite being able to click anywhere else on the system.  So I rebooted and lo and behold, the 'grub rescue' prompt appeared.

I eventually found my way to the Grub 2 wiki but that only got me to a point then left me hanging dry.  Specifically:

"- Now you need to edit the /etc/default/grub file to fit your system"

So I opened up the file, expecting to see something that I might be able to understand where I can edit but I didn't.  The wiki gave no help where to go from here.  Ugh.

So I found a thread on 'ubuntu-ky.ubuntuforums.org' that mentioned using boot_script_info.  So I Dl'd it and ran it with the hopes that someone can take a look and help me understand what I need to do to fix this.

[http://pastebin.ubuntu.com/480763/](http://pastebin.ubuntu.com/480763/)

Oh yeah, when this all happened, the system absolutely refused to boot into any live CD at all!  I had 10.04LTS, 8.04 and PUppyLInux and the CD started booting then once the main splash screen went by (if it ever got to that....) nothing else would happen.  No blinking lights, no HD activity, no CD Rom buzzing...nada.  On a whim, I decided to try a LiveCD again (10.04LTS) and now that it at least working.

Also, I have noted some bad sectors(2) but that has not gotten any worse that I am aware of over the last few weeks.  Just checked, still the same 2 bad sectors.

What is truly annoying is that all I need is for this system to last me 4 or 5 more weeks than I am getting rid of it when I move to Korea.  Between selling my house and cars, I really don't need this little headache right now.  So any/all help is appreciated!

Don

---

### Post by oldfred on 2010-08-20
I do not see anything out of place in  your results.txt.

Have you tried reinstalling grub2 to the MBR?

Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Or can you manually boot from rescue prompt?

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hd0,1)
      linux /vmlinuz root=/dev/sda1 ro
      initrd /initrd
      boot

---

### Post by lovinglinux on 2010-08-20
For the flash issues, see these:

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by DragonDon on 2010-08-20
I reinstalled GRUB and that did the trick.  Thanks!

> **oldfred said:**
> I do not see anything out of place in  your results.txt.

Have you tried reinstalling grub2 to the MBR?

Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda


---

### Post by DragonDon on 2010-08-20
Thanks for the tips.  Tried them, seems to be working better.  Maybe the simple act of remove/reinstall did the trick.

> **lovinglinux said:**
> For the flash issues, see these:

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

