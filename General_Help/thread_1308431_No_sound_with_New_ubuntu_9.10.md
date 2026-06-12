---
title: "No sound with New ubuntu 9.10"
date: 2009-10-31
forum: General Help
---

### Post by danielshewchuk on 2009-10-31
I have no sound since i downloaded Ubuntu 9.10. Please help

---

### Post by Esk1m0 on 2009-10-31
Yeah... i dont have any sound neither.. :(

im on a Fujitsu Siemens Lifebook S7020, quite old but still kickin' :)

---

### Post by rturner on 2009-10-31
It was probably just me, but after a clean install of final 9.10 I was pulling my hair out until I noticed that the speaker icon was set at 0.

---

### Post by danielshewchuk on 2009-10-31
i still need help. simple instructions would be great

---

### Post by bluedalek on 2009-10-31
I to now have no sound after updating to 9.10.  Ubuntu does not even recognize my sound card when going to system -> preferences -> sound preferences and selecting the 'hardware' tab.

---

### Post by danielshewchuk on 2009-10-31
Me neither. Can someone PLEASE help. Getting frustrated

---

### Post by autocrosser on 2009-10-31
Take a look at this Blog: [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)  That might fix things for you....

---

### Post by pickarooney on 2009-10-31
Did you overwrite the menus.lst file during installation? If not, check that you're booting to the correct kernel.

---

### Post by bluedalek on 2009-11-01
How do I check what kernel I am using?  the GRUB loader?

As for menu options, I believe I did allow the installer to overwrite all menu.list prompts

---

### Post by pickarooney on 2009-11-01
uname -a

---

### Post by AlanInVancouverBC on 2009-11-01
I've got no sound, either.
Strange how the kernel could be involved. Why?
With respect to kernels, I also don't understand why when I updated (vs clean install) to 9.10, the grub still shows 9.04 kernels. Yet I'm booting to 9.10!
So???\
Puzzled and Confused in Vancouver BC, Canada

---

### Post by AlanInVancouverBC on 2009-11-01
As to post directly above, here are my kernels. The first are the Kubuntu kernels, followed by the Ubuntu kernels. Note that the Ubuntu show 9.04, but both OSs are 9.10. My computer boots to Kubuntu, regrettably, so I edit in Kubuntu, using Kate, to edit Menu.lst.
And as this thread indicates, it is with Ubuntu that I can't get sound.

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		8b80c990-2229-481f-a2a3-408ab5e608e6
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=8b80c990-2229-481f-a2a3-408ab5e608e6 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		8b80c990-2229-481f-a2a3-408ab5e608e6
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=8b80c990-2229-481f-a2a3-408ab5e608e6 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		8b80c990-2229-481f-a2a3-408ab5e608e6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8b80c990-2229-481f-a2a3-408ab5e608e6 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		8b80c990-2229-481f-a2a3-408ab5e608e6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8b80c990-2229-481f-a2a3-408ab5e608e6 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		8b80c990-2229-481f-a2a3-408ab5e608e6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro single 
initrd		/boot/initrd.img-2.6.28-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro quiet splash vga=792 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7de512ec-9ced-4b67-882d-4c73bed39c13 ro single 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 9.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by pickarooney on 2009-11-01
I think the menu.lst has moved to /etc/boot or something along those lines. Have a look round, there are bound to be loads of threads on it. I haven't installed Karmic yet, but I did read that somewhere in a review.

---

### Post by bluedalek on 2009-11-01
> **pickarooney said:**
> uname -a
```

Linux dalek-desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux
```

---

### Post by autocrosser on 2009-11-01
That is the Jaunty kernel--you "should" be booting with 2.6.31-14 or so.....Jaunty's kernel will have sound problems in Karmic..

Go into Synaptic & remove the 2.6.28 kernels & MAKE SURE to reinstall the 2.6.31 kernels--verify with the terminal window open that update-grub is updating 2.6.31 kernels.

---

### Post by bluedalek on 2009-11-01
Great!

I now have sound.. however, upon launching Exaile, VLC or running WoW in Wine, the sound clips.  Any thoughts?

---

### Post by autocrosser on 2009-11-01
Did you look at the blog entry? [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)  there are several parts to the "fix" the kernel is just one......

---

### Post by AndiFant on 2009-12-21
Hi,

after installing Ubuntu 9.10 on an S7020 (new, clean hard disk), I had the same problem (no sound on Realtek HD audio chip).

I got it working the following way:

"Lanched Synaptic (System>Administration>Synaptic Package Manager) and then searched for pulseaudio.
Then right clicked on it and then marked it for Complete Removal.
Then searched for esound and then marked it for installation. If it is already installed, you may want to mark it for reinstallation."

(from [http://www.khattam.info/2009/09/09/solved-sound-problem-in-ubuntu-9-10-karmic-koala-alpha-4-due-to-pulseaudio/](http://www.khattam.info/2009/09/09/solved-sound-problem-in-ubuntu-9-10-karmic-koala-alpha-4-due-to-pulseaudio/))

Any objections against not using pulseaudio?

Andreas

---

### Post by AndiFant on 2010-02-08
> **AndiFant said:**
> 

Any objections against not using pulseaudio?

Andreas

Ok, meanwhile I took notice that not using pulsaudio may give some sound, however the support of adjusting the volume by the <Fn> keys gets lost.

Andreas

---

