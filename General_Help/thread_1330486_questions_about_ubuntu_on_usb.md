---
title: "questions about ubuntu on usb"
date: 2009-11-18
forum: General Help
---

### Post by aCsbD6N5xj on 2009-11-18
Hi.

I recently came across **LiLi USB Creator **that offers a relatively easy, i guess, installation of ubuntu on a flash drive. (I haven't tried it yet btw)

So in their FAQ, when it comes to persistence, it says: 

> What you can't do on a persistent system :
 
[LIST]
[*]updates core files (kernel etc) = no full system updates
[/LIST]
Does that mean it won't save  secuity updates or any other update on my flash drive? If yes, is there a workaround for that? I'd just like to be able to have those updates just for the sake of security and being up-to-date. I don't plan on using ubuntu usb that much anyways, it's more of a just-in-case option. And it's not like the machine(s) i'll be using that on will be uber-vulnerable if I don't have these updates right?

Thx.

---

### Post by undecim on 2009-11-18
I don't think core system updates are very much of a security issue for something that you aren't going to be running a lot.

First of all, there are no services running by default that have open ports, so the only way you are going to be attacked is if you use internet applications like Firefox on networks or websites that aren't trustworthy.

But still, Firefox and your other apps should update because they can be saved to the persistent system (the kernel can't do this because it has to be loaded before the persistent filesystem can be read)

Moreover, most of the security issues with the kernel are privilege escalation, which simply allow someone who ALREADY HAS ACCESS to the computer to become root.

---

### Post by aCsbD6N5xj on 2009-11-18
> **undecim said:**
> I don't think core system updates are very much of a security issue for something that you aren't going to be running a lot.

First of all, there are no services running by default that have open ports, so the only way you are going to be attacked is if you use internet applications like Firefox on networks or websites that aren't trustworthy.

But still, Firefox and your other apps should update because they can be saved to the persistent system (the kernel can't do this because it has to be loaded before the persistent filesystem can be read)

Moreover, most of the security issues with the kernel are privilege escalation, which simply allow someone who ALREADY HAS ACCESS to the computer to become root.

so, concerning the untrustworthy networks, i guess i should even avoid using that ubuntu usb in cybercafes? because even though i wont be using this alot, cybercafes would be the place of choice for me to use it, so i don't have to deal with a potentially unsafe windoze network (keyloggers, trojans, open ports etc...).

but apart from that, thx alot for ur answer.

---

### Post by bit mad on 2009-11-18
I looked at the LiLi website ( [http://www.linuxliveusb.com/en/](http://www.linuxliveusb.com/en/) ) and it appears that it will always run Ubuntu via a VirtualBox, whether you boot from the USB key or not. This means it's not likely to be the quickest possible way to run Linux, like a normal install, or even a "live CD/USB". Quick enough for many uses, but not for demanding tasks like video editing, for example.

If you're happy to be running from a VirtualBox, then that's fine - but why not just set up a VirtualBox anyway, or a PortableUbuntu ( [http://portableubuntu.demonccc.com.ar/](http://portableubuntu.demonccc.com.ar/) ) which can be put on a USB key...?

I guess it has its uses, but it hasn't quite reached the Holy Grail stage of providing a simple to setup, full speed, persistant USB install for a Windows User who doesn't want to meddle with partitions and boot processes :D

---

### Post by aCsbD6N5xj on 2009-11-18
> **bit mad said:**
> I looked at the LiLi website ( [http://www.linuxliveusb.com/en/](http://www.linuxliveusb.com/en/) ) and it appears that it will always run Ubuntu via a VirtualBox, whether you boot from the USB key or not. This means it's not likely to be the quickest possible way to run Linux, like a normal install, or even a "live CD/USB". Quick enough for many uses, but not for demanding tasks like video editing, for example.

If you're happy to be running from a VirtualBox, then that's fine - but why not just set up a VirtualBox anyway, or a PortableUbuntu ( [http://portableubuntu.demonccc.com.ar/](http://portableubuntu.demonccc.com.ar/) ) which can be put on a USB key...?

I guess it has its uses, but it hasn't quite reached the Holy Grail stage of providing a simple to setup, full speed, persistant USB install for a Windows User who doesn't want to meddle with partitions and boot processes :D

It does use VirtualBox when running windows but when booting from USB it is still "a live system on which there is an overlay that is writable." Where did you see it say it uses VirtualBox when booting from USB? 

I'll also check the PortableUbuntu website you gave and see which is the best solution

---

### Post by bit mad on 2009-11-18
> **BucketBob said:**
> Where did you see it say it uses VirtualBox when booting from USB?

No idea :oops: but that's the impression I got :P
If there's definite proof either way I'd be interested to hear it!

---

### Post by dcstar on 2009-11-18
> **bit mad said:**
> No idea :oops: but that's the impression I got :P
If there's definite proof either way I'd be interested to hear it!

Rubbish, it says you can RUN Linux from inside Windows.

Booting the Linux USB is totally different.

---

### Post by bit mad on 2009-11-19
"Rubbish" and "Regards" in one post? Curious mix :)

Well, if you're so sure, then maybe I'll give it a try.
Ta.

---

### Post by aCsbD6N5xj on 2009-11-19
so how about my cybercafe scenario? :KS

---

### Post by bit mad on 2009-11-20
Cybercafes and public wifi access points aren't 'safe', period.

---

### Post by bit mad on 2009-11-21
Interesting article on it here
[http://maketecheasier.com/how-to-create-your-own-usb-linux-distro-with-lili/2009/09/29](http://maketecheasier.com/how-to-create-your-own-usb-linux-distro-with-lili/2009/09/29)

:)

---

### Post by bit mad on 2009-11-21
Well I've tried it, and it worked like a charm. The install, that is. It's not the quickest process in the world, but bearable. Dead simple User Interface, did exactly what it promised. Result - one fully functional bootable USB Key, with persistence, with a Linux run-speed that is streets ahead of VirtualBox or other emulations. It plays video at full speed.

However, I tried it to test Linux Mint 7, and it won't let me change away from an appalling 60Hz refresh rate, and the Mint Update downloads too much stuff to fit on the 2GB USB stick I've used... and things get hopeless with 0 bytes free - so it's a waste of time :cry:
My lack of success: [http://forums.linuxmint.com/viewtopic.php?f=18&t=36264](http://forums.linuxmint.com/viewtopic.php?f=18&t=36264)

---

### Post by aCsbD6N5xj on 2009-11-23
> **bit mad said:**
> Interesting article on it here
[http://maketecheasier.com/how-to-create-your-own-usb-linux-distro-with-lili/2009/09/29](http://maketecheasier.com/how-to-create-your-own-usb-linux-distro-with-lili/2009/09/29)

:)

interesting indeed. i'll just have to get a larger flash drive than my 2gb one.

and yeah i'll just stay away from cybercafes like i usually do and just play with that ubuntu usb at home.

---

