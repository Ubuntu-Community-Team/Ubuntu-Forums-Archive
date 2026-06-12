---
title: "help please i can boot in to ubuntu 10.10 using a usb"
date: 2010-10-10
forum: General Help
---

### Post by penguin1029 on 2010-10-10
hello,
i need some help, i try to boot in to Ubuntu 10.10 using a usb flash drive i have used different flash drives and the Ubuntu usb creater (that came with Ubuntu 10.04) and unetbootin and then i get some error that says something like: busy box can not start unknown key error or something like that please help me
 :confused: :confused: :confused:
i am even considering another ubuntu like XUbuntu

---

### Post by JackNocturne on 2010-10-10
Use **USB **Creator, its the simplest.

After you have created the USB boot disk with it, **modify **the following in the disk.


Go to root of USB flash disk to the folder **/syslinux **and find the file **syslinux.cfg**

Edit the file with a text editor; under the line 

```
ui gfxboot bootlogo
```  change to  ```
gfxboot bootlogo
```then save. 

Reboot to test it now

---

### Post by penguin1029 on 2010-10-10
Thank you so much it worked!!! i just installed ubuntu 10.10 and its the best os!! thank you thank you!!
:)

---
typed on ubuntu 10.10

---

### Post by trentscott on 2010-10-10
Thanks this worked for me. I've added this here:

[http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/](http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/)

(Credits to JackNocturne)

---

### Post by henkk78 on 2010-10-11
Doesn't work for me. 

I now get the error: 

> Unknown keyword in configuration file: gfxboot

Info:

I'm using the Netbook edition on an Acer Aspire One ZG5. 

The flashdisk was created using pendrive (but had to choose custom ISO, as the Netbook edition for 10.10 was not listed).

I then edited syslinux.cfg on Mac OS X (using Smultron)

---

### Post by trentscott on 2010-10-11
> **henkk78 said:**
> Doesn't work for me. 

I now get the error: 



Info:

I'm using the Netbook edition on an Acer Aspire One ZG5. 

The flashdisk was created using pendrive (but had to choose custom ISO, as the Netbook edition for 10.10 was not listed).

I then edited syslinux.cfg on Mac OS X (using Smultron)

Similar issues have been reported (with Asus EEEPC's) on Netbook Remix.

---

### Post by M4T1A5 on 2010-10-11
Anyone figured this one out yet? I would really like to boot up the netbook edition (Asus EEEPC)

---

### Post by 3_aces on 2010-10-12
[SIZE=2]Worked [/SIZE][SIZE=2] perfectly [/SIZE][SIZE=2]for me :).. 10.10 is just gr8.. postin right now from live usb 10.10 boot..will install [/SIZE]*Maverick* Meerkat[SIZE=2] now

Thanks for solution buddy

and people dont forget 

you have to use **startup disk creator** not unetbootin[/SIZE]

---

### Post by Tommy on 2010-10-13
> **M4T1A5 said:**
> Anyone figured this one out yet? I would really like to boot up the netbook edition (Asus EEEPC)

I had a similar problem with my Asus EeePC 900 trying to load the netbook remix. I got the unknown keyword error, hanging at a "boot:" prompt with no mention of which keyword is the problem. 

I am creating the USB images using Ubuntu 9.10.

I found this other solution -- upgrade syslinux to 4.01:

[http://www.khattam.info/solved-syslinux-unknown-keyword-in-configuration-file-2010-09-01](http://www.khattam.info/solved-syslinux-unknown-keyword-in-configuration-file-2010-09-01).

I just tried BOTH solutions and on my EeePC 900... BOTH worked on mine. I just looked at the /syslinux/syslinux.cfg file on the image with syslinux 4.01 and it has the original keywords, so I don't know the source of the regression.

---

### Post by trentscott on 2010-10-13
> **Tommy said:**
> I had a similar problem with my Asus EeePC 900 trying to load the netbook remix. I got the unknown keyword error, hanging at a "boot:" prompt with no mention of which keyword is the problem. 

I am creating the USB images using Ubuntu 9.10.

I found this other solution -- upgrade syslinux to 4.01:

[http://www.khattam.info/solved-syslinux-unknown-keyword-in-configuration-file-2010-09-01](http://www.khattam.info/solved-syslinux-unknown-keyword-in-configuration-file-2010-09-01).

I just tried BOTH solutions and on my EeePC 900... BOTH worked on mine. I just looked at the /syslinux/syslinux.cfg file on the image with syslinux 4.01 and it has the original keywords, so I don't know the source of the regression.

Very odd! This is absolutely one of the weirdest things I've ever seen.

---

### Post by Tommy on 2010-10-13
> **trentscott said:**
> Very odd! This is absolutely one of the weirdest things I've ever seen.

I just created Bug 660061 [https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/660061](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/660061)

---

### Post by o----o on 2011-01-09
> **Tommy said:**
> I had a similar problem with my Asus EeePC 900 trying to load the netbook remix. I got the unknown keyword error, hanging at a "boot:" prompt with no mention of which keyword is the problem. 

I am creating the USB images using Ubuntu 9.10.

I found this other solution -- upgrade syslinux to 4.01:

[http://www.khattam.info/solved-syslinux-unknown-keyword-in-configuration-file-2010-09-01](http://www.khattam.info/solved-syslinux-unknown-keyword-in-configuration-file-2010-09-01).

I just tried BOTH solutions and on my EeePC 900... BOTH worked on mine. I just looked at the /syslinux/syslinux.cfg file on the image with syslinux 4.01 and it has the original keywords, so I don't know the source of the regression.


Works for me too :) thanks to all.

---

### Post by Lovek on 2011-01-11
Thanks alot!
this worked for me with 10.10 netbook version, on an Asus EEE
very nicely

---

