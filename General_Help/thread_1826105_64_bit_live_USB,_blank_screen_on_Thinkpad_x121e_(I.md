---
title: "64 bit live USB, blank screen on Thinkpad x121e (Intel)"
date: 2011-08-16
forum: General Help
---

### Post by MorrisseyJ on 2011-08-16
Hi all,

I have just received my new laptop - a Thinkpad x121e, with Intel (Core i3).

I am trying to put ubuntu on it, but i am having some problems with the 64 bit live USB.

When i run the USB i get i get a GRUB-looking screen, with options to:
> 1. Try Ubuntu without installing
2. Install Ubuntu
3. Check the disk for errorsWanting to repartition my hard drive (using GParted) so that i can dual boot, i > Try Ubuntu without Installing, at which point the screen goes blank and nothing happens. I am then forced into a hard reboot. I get the exact same result when i pick > Check the disk for errors from the GRUB-like screen

To check the live USB, i tried it on my old laptop (32bit, Celeron M). When i did so i got a purple screen with an image of what looks like a keyboard and a man at the bottom, and then a message telling me to try a kernel which matches with my machine's architecture.

I then tried a live USB with 32 bit ubuntu and the live USB works fine - i am sending this email from this live instance running on my new Thinkpad. The same can be said for a 32 bit Mint live usb which also worked on the Thinkpad.

So i am not sure what is going on. If anyone could tell me why the 64bit live USB is not working, it would be great as i'd like to get it up and running. The only thing i could think of was that i have downloaded the amd64.iso, and this is an intel machine. Having said that i see that all the sites on the web suggest that this shouldn't make a difference (if it does, where might i get an 64 bit version for intel). In addition i am not sure why, if this was the problem, my old celeron laptop brings up the error message while the new machine just hangs.

As always, any and all help is very much appreciated.

Thanks,
[COLOR=#888888]
[/COLOR]

---

### Post by MorrisseyJ on 2011-08-18
I posted this question on launchpad and from there stumbled across a solution.

Process is detailed here: [https://answers.launchpad.net/ubuntu/+question/168297/+index](https://answers.launchpad.net/ubuntu/+question/168297/+index)

---

### Post by paolonicolai on 2011-09-04
Hi, I've read your post and it is the only one I can find with reference to the Lenovo x121e on Intel CPU.  I am undecided between buying the AMD and Intel versions of this laptop.

Would you be able to tell me if the desktop effects (compiz?) work on the Intel GPU your laptop has.  I'm pretty sure they work fine on the AMD version (which has a Radeon GPU), but I'd like to know your opinion on the Intel version.

Please do let me know.

Thanks.

---

### Post by MorrisseyJ on 2011-09-05
paolonicolai: 

i am not the most sophisticated computer user, so i don't know how in-depth i can be here. 

That said, the short of it is that the machine works well for the most part. I have been warned against new machines and linux but most things work here. 

All compiz effects work, even have dual monitors working pretty well just using the monitor switcher application.

Pretty much all the shortcuts work and the only issue is that suspend is dodgy, both when going into hibernation on battery and when closing the lid. This is a bit of a hassle as it detracts from the portability of the device, which is a central feature of it. That said, i am hoping that something will be worked out on subsequent kernels. 

The other problem is with the wifi and bluetooth, but i have detailed all that here: [http://ubuntuforums.org/showthread.php?t=1761472](http://ubuntuforums.org/showthread.php?t=1761472). I have yet to resolve this and it doesn't prove a problem unless i remove the battery. 

if you have any specific questions, or want me to run any tests, let me know and i'll do my best.

---

