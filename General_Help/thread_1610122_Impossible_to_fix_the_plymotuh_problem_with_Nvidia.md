---
title: "Impossible to fix the plymotuh problem with Nvidia drivers"
date: 2010-10-31
forum: General Help
---

### Post by Vegaxus on 2010-10-31
Hi everybody.

Recently i have installed Ubuntu 10.10 Maverick but unfortunately i have found some bugs as i personalized the system how i want (if u see, there will be some threat opened by me talking about those bugs).

Ok, the first of them is about the problem of the plymouth theme of ubuntu 10.10 when i have installed the nvidia drive.

Some Info:
- I went to Jockey app or System -> Administration -> additional devices (literal translation from spanish version. Sorry for this :( )
- I actived the most recent version: currently ver. 260.19.06
- Then, plymouth lost the resolution to 640x800 (i think) and the text "ubuntu 10.10" is not an image but a simple monospace text.


I googled a lot looking for a successful answers for this bug. I have changed the grub.conf, the 00_headers, the initramfs-tools/modules, etc unsuccessfully. The only one that currently made some changes is this:

- Installed the package "v86d"
- Add "uvesafb mode_option=1280×1024-24 mtrr=3 scroll=ywrap" at the /etc/initramfs-tools/modules
- echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
- sudo "update-grub" and "update-initramfs -u"

But the final result is this:

Load Screen boot (after brug/grub pick OS):
[IMG]http://img502.imageshack.us/img502/2330/perfectdesktopmavthumb.png[/IMG]

close Screen boot (after shutdown/reboot Ubuntu):
[IMG]http://www.hackourlives.com/wp-content/uploads/2010/05/Ubuntu-10.04-Lucid-Lynx.png[/IMG]

So, the bug persist in the load screen, no load the Ubuntu image and show the monospace text and it not center. Only the resolution 1280x800-24bits is work.

My graphic card: 8400M GS Nvidia.
OS: Ubuntu 10.10

regards.

---

### Post by Mike_tn on 2010-11-16
Not sure about your problem exactly but saw it. I used parts of this thread to help me. The main poster had your nvidias and screen problem.  My intro screen look like this too but I have an intel chipset.  I used the fix here and it worked.

> **garvinrick4 said:**
> 

```
sudo -i
```
```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 

```Hit ctrl/d

Entire thread it came from is here:
[http://wwww.ubuntuforums.org/showthread.php?t=1607030](http://wwww.ubuntuforums.org/showthread.php?t=1607030)

---

### Post by 3rdalbum on 2010-11-16
This is not a bug, this is intended behaviour. The official NVIDIA driver doesn't support the technology behind the nice start screen, so Ubuntu 'falls back' to the text one.

---

### Post by DinoT1985 on 2010-11-16
> **3rdalbum said:**
> This is not a bug, this is intended behaviour. The official NVIDIA driver doesn't support the technology behind the nice start screen, so Ubuntu 'falls back' to the text one.

I'm using the recommended NVIDIA driver and I can have the nice start screen so it is not that.

---

### Post by DinoT1985 on 2010-11-16
Try this [http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

---

### Post by Vegaxus on 2010-11-17
Tried and fail :(.

I must keep the nouveau drivers on yet.

---

### Post by Yougo on 2010-11-18
as 3d acceleration during desktop session is more important than a shiny bootsplash to me, i will keep my NVIDIA drivers...

...but do i really have to settle for that low res jumble then? (yes i know, i could go for "quiet nosplash" but that's no real solution now is it?) i managed to fix it for lucid, but that doesn't work anymore. what changed in Maverick to make this such a pain? :(

---

### Post by tad1073 on 2010-11-18
Forget about all that other junk, the fix that was given to me is much simpler. My native resolution is 1680x1050 so  just replace 1680x1050 with your native resolution.

[http://ubuntuforums.org/showthread.php?t=1498221](http://ubuntuforums.org/showthread.php?t=1498221)

---

### Post by Yougo on 2010-11-18
Hey, that's some new stuff! regardless if it works or not, you already earned yourselves a Darth Vader shaped cookie for not repeating the entire internet

[IMG]http://www.geekalerts.com/u/darth-vader-cookie.jpg[/IMG]

i'm gonna try this when i get home!

---

### Post by DinoT1985 on 2010-11-18
Have you tried reinstalling plymouth-themes and then doing the above links instructions?

---

### Post by tad1073 on 2010-11-18
> **DinoT1985 said:**
> Have you tried reinstalling plymouth-themes and then doing the above links instructions?

no, I have not.

---

### Post by Yougo on 2010-11-19
Ok, i got it up and running! just in a bit of a silly way.:redface:
previously to upgrading to Maverick i installed a custom Plymouth theme. in hindsight i think that the theme was broken, causing plymouth to fall back to low res. seems the biggest problem here was BKAC #-o

 after fiddling about i figured out the method in your link works almost the same as all the other stuff, but puts all the info right in the grub file rather than in various obscure /modprobe/... files. 
GFXMODE=keep just means it should take the resolution from the grub menu and use that for the boot splash. putting a resolution there will give plymouth its own resolution

in the end, i think both methods should work, but the one in your link is much cleaner.

---

### Post by stinkeye on 2010-11-19
> **tad1073 said:**
> Forget about all that other junk, the fix that was given to me is much simpler. My native resolution is 1680x1050 so  just replace 1680x1050 with your native resolution.

[http://ubuntuforums.org/showthread.php?t=1498221](http://ubuntuforums.org/showthread.php?t=1498221)

Thanks **tad1073**, on my nvidia system, simply adding 
```
GRUB_GFXPAYLOAD_LINUX=1680x1050
```
where 1680x1050 is my native desktop resolution, to /etc/default/grub
and running
```
sudo update-grub
```
Brought back the graphical Plymouth for me.

---

### Post by Vegaxus on 2010-11-22
No-one of thoses workround works for me :(. I am very tired trying to fix this bug i give up, i will wait it fixed next version 11.04 or upper.

---

### Post by DinoT1985 on 2010-11-30
> **Vegaxus said:**
> No-one of thoses workround works for me :(. I am very tired trying to fix this bug i give up, i will wait it fixed next version 11.04 or upper.

Try installing Ubuntu Manager and do the settings from there. After install its under System Tools

[http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html](http://www.ubuntugeek.com/plymouth-manager-simple-tool-to-change-splash-screen-themes.html)

---

