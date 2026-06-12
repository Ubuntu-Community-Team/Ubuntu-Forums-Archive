---
title: "Monitor goes &quot;Out of Range&quot;"
date: 2012-01-29
forum: General Help
---

### Post by hotbeef on 2012-01-29
I recently installed Ubuntu 10.4 onto an older computer. Upon trying  to boot off the live CD, my monitor would go "out of range" (screen would turn black  and display a hardware error message "out of range"). I was able to  select the nomodeset option (F6 -> select nomodeset at boot options)  to fix the issue temporarily, and then successfully install Ubuntu.
 
However, I cannot get around the "monitor out of range" problem when  booting Ubuntu from my HD. I have tried both adding "nomodeset" to the  kernel options after "quite splash" (boot -> hold shift -> edit  kernel -> ctrl + x to boot) as well as replacing "quite splash" with  "nomodeset". I read to do this from a few other forum posts, and I  believe I am entering these terms in the correct fashion, though i could  be wrong.

I also went ahead and booted into the linux 'recovery mode', and successful added:
```
GRUB_CMDLINE_LINUX="nomodeset"
``` to /etc/default/grub after changing the file's write permissions.


 I don't understand how "nomodeset" fixed the problem when booting off  the livecd, but doesn't fix the issue when trying to boot of the freshly  installed OS. This leads me to believe that I am not editing the kernel  options properly, but I cant figure out what exactly I'm not entering  or entering incorrectly.
 
The video card installed on the machine (no onboard video) is a  nVidia FX 5500 and the monitor is a old LCD that runs (IIRC) 1024x768  native resolution.
 

[http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/](http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/)
This is the guide i was following to try and remedy my problem.

 I also ask this question here:
[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/185526](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+question/185526)
but I couldn't find a solution and they said to try this forum for help.

---

### Post by Hedgehog1 on 2012-01-30
This issue is that grub is using a frequency higher than your monitor can display.

Please do this to force it to match your LCD:

```
gksudo gedit /etc/default/grub
```

[COLOR="Red"]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR="red"]to this:[/COLOR]

GRUB_GFXMODE=1024x768

[COLOR="red"]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```


***The Hedge***

:KS

---

### Post by hotbeef on 2012-02-10
> **Hedgehog1 said:**
> This issue is that grub is using a frequency higher than your monitor can display.

Please do this to force it to match your LCD:

```
gksudo gedit /etc/default/grub
```[COLOR=Red]and change this line:[/COLOR]

#GRUB_GFXMODE=640x480

[COLOR=red]to this:[/COLOR]

GRUB_GFXMODE=1024x768

[COLOR=red]Then save and exit the document.[/COLOR]


Then do:

```
sudo update-grub
```
***The Hedge***

:KS

"gksudo gedit" and "sudo gedit" produce the error "Warning: Cannot open Display."

I tried manually adding the line GRUB GFXMODE=1024x768 with a normal "sudo nano", followed by sudo update-grub.

This all seems to have processed, but I am still receiving a monitor out of range error.

---

### Post by pqwoerituytrueiwoq on 2012-02-10
```
sudo apt-get hwinfo;sudo hwinfo --frwmebuffer
```
please post output of that and what is your monitors recommend resolution?

---

