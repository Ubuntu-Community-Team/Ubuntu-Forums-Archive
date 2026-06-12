---
title: "Grub Causing Problems Again"
date: 2010-02-08
forum: General Help
---

### Post by JasonSilver on 2010-02-08
I start up my laptop this morning (dual boot to Vista - blech) and was promptly faced with a grub screen:

---
GNU GRUB Version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word....
---

There is no opportunity to select a kernel.

This is the second or third time something like this has happened to me. Normally, I actually have three kernels that won't even boot... I have to go back to 14 in order to get into Ubuntu.

I've tried the directions on
[http://ubuntuforums.org/showthread.php?t=1325901](http://ubuntuforums.org/showthread.php?t=1325901)
"My Grub Nightmare Won't End"

but it gets me no where. I just see "partition not found"

Here's what set produces:
?=1
color_highlight=
color_normal=
loop=loop0
pager=
prefix=(hd0,2)/boot/grub
root=loop0
show_panic_message=false

Here's what ls produces:
(loop0) (hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1)

I don't have a CD drive to boot from-- I installed by downloading the image files in Vista.

What do I do? (speak slowly I'm a newb)

Thanks!
Jason

---

### Post by JasonSilver on 2010-02-08
bump

---

### Post by Kir_B on 2010-02-08
> **JasonSilver said:**
> I start up my laptop this morning (dual boot to Vista - blech) and was promptly faced with a grub screen:

---
GNU GRUB Version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word....
---

There is no opportunity to select a kernel.

This is the second or third time something like this has happened to me. Normally, I actually have three kernels that won't even boot... I have to go back to 14 in order to get into Ubuntu.

I've tried the directions on
[http://ubuntuforums.org/showthread.php?t=1325901](http://ubuntuforums.org/showthread.php?t=1325901)
"My Grub Nightmare Won't End"

but it gets me no where. I just see "partition not found"

Here's what set produces:
?=1
color_highlight=
color_normal=
loop=loop0
pager=
prefix=(hd0,2)/boot/grub
root=loop0
show_panic_message=false

Here's what ls produces:
(loop0) (hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1)

I don't have a CD drive to boot from-- I installed by downloading the image files in Vista.

What do I do? (speak slowly I'm a newb)

Thanks!
Jason

Sorry to hear that you are having such a horrible time.

Correct me if I'm wrong. Are you running ubuntu via windows and wubi?

I'll await further info

Good luck. Kir_b

---

### Post by Kir_B on 2010-02-08
Also, are you running a ubuntu live cd right now?

---

### Post by JasonSilver on 2010-02-08
I believe it's through wubi, yes... and no live CD is possible since there is no working CD drive on this laptop.

---

### Post by JasonSilver on 2010-02-08
I've been trying 

set root=(loop0)
linux  /boot/vmlinuz-2.6.14-generic root=/dev/sda11  
initrd   /boot/initrd.img-2.6.14-generic
boot

but it only gets a little way through the boot process and chokes. I have no idea what I'm doing.

It goes to hi res, and says "Waiting for root file system..." and stops.

It "Gave up waiting for root device"

---

### Post by r_s on 2010-02-08
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by JasonSilver on 2010-02-08
Thank you- that looks promising!

Do I risk losing everything in my Linux set up?

Is there anyway to remove Vista?

---

### Post by Kir_B on 2010-02-08
> **JasonSilver said:**
> I believe it's through wubi, yes... and no live CD is possible since there is no working CD drive on this laptop.
 
[COLOR=Magenta]**_OUCH!!!_**[/COLOR]

I'm sorry to hear that. How does a person install an operating system on your box? USB?

---

### Post by Kir_B on 2010-02-08
Can you get your hands on a cd containing your windows OS along with an external cd drive?

---

### Post by JasonSilver on 2010-02-08
I installed Ubuntu using WIndows-- downloading wubi and going from there.

The CD drive needs to be replaced that's all.

SO, GREAT NEWS! It is now booting successfully into 19, so we've made progress!

Thanks SO MUCH for your help. 

The ONE THING that I hadn't considered in doing my Google search for help was the Wubi element. I hope future sufferers can get around this problem more easily.

THANKS!
Jason

---

### Post by Kir_B on 2010-02-08
The reason I was asking if you had a USB cd, was because, when this happened to us there were literally zero answers concerning this type of problem with the wubi, which left us exhausting all options within a very short period of time. The only alternative we had, was to completely reinstall our windows xp. We started the process and chickened out part of the way through, only because I was researching the reinstallation process when I realised that we would be needing the product key, which was long ago lost. So we reset the machine and low and behold our windows xp booted up with both the Ubuntu and Windows xp options. We tried the Ubuntu several times to no avail, but the windows xp booted up fine. We did eventually get Ubuntu running again through the wubi, but if I remember correctly we ended up losing the contents though. I think the only reason that we lost the original Ubuntu wubi installation was because we wanted to setup a dual boot, but we still had a Ubuntu entry at boot up, which meant to us that it might be wise to completely uninstall it {I remember this being a trial and error process that involved booting into the live cd also}. The one thing that we learned about wubi was this: The more that Ubuntu is altered in a wubi installation, the higher the odds are that something bad is going to happen. My advice to anyone running wubi is this: The wubi is only there to try out Ubuntu and is definitely not to be used long term. Another tip would be to avoid installing new kernels and Headers.

                   Peace all. Kir_b

---

### Post by Kir_B on 2010-02-08
> **JasonSilver said:**
> I installed Ubuntu using WIndows-- downloading wubi and going from there.

The CD drive needs to be replaced that's all.

SO, GREAT NEWS! It is now booting successfully into 19, so we've made progress!

Thanks SO MUCH for your help. 

The ONE THING that I hadn't considered in doing my Google search for help was the Wubi element. I hope future sufferers can get around this problem more easily.

THANKS!
Jason

Glad to hear that you're back in business. 
                                         Have a great day. Kir_b

---

