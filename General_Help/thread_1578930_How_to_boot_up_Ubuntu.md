---
title: "How to boot up Ubuntu?"
date: 2010-09-21
forum: General Help
---

### Post by Pazaz on 2010-09-21
I installed it fully, And Now I just have  boot it up... How do I do that?

---

### Post by Joe of loath on 2010-09-21
... Turn it on?

---

### Post by Pazaz on 2010-09-21
T.T, Example, I installed the disk with full installation. Now I want to use it. I reset my computer, So what do I do to turn it on, I.E. Open up Bootup menu/Select OS...

---

### Post by Joe of loath on 2010-09-21
Does it not boot into Ubuntu automatically?

---

### Post by Pazaz on 2010-09-21
Nope, Should It?

---

### Post by TNT1 on 2010-09-21
> **Pazaz said:**
> I.E. 

? 

You dual booting I presume?

---

### Post by TNT1 on 2010-09-21
> **Pazaz said:**
> Nope, Should It?

Yip, if it installed, it should. Are you dual booting? when you switch the pc on, what does the screen say?

---

### Post by Pazaz on 2010-09-21
> **TNT1 said:**
> ? 

You dual booting I presume?

? No, That's the question I'm asking, How to dual boot. Sorry If I didn't make that clear.

---

### Post by Joe of loath on 2010-09-21
It should boot into Ubuntu automatically, and if you're dual booting, display the OS menu first.

---

### Post by Pazaz on 2010-09-21
? It says Loading Windows, Why? goes through the acer screen loading thing for about 1 second, Then for 5 seconds says Press f2 and etc. Buttons for the functions, You know. I just want to know how.

---

### Post by Pazaz on 2010-09-21
-.-, But Exactly, HOW to view the OS menu, Sorry If I'm too annoying, I'm 17, What do you expect?

---

### Post by Joe of loath on 2010-09-21
Did you install Ubuntu first, then windows? If so, windows overwrites the ubuntu bootloader, so that windows always starts first.

Pazaz - I'm 17 too :p

---

### Post by Pazaz on 2010-09-21
> **Joe of loath said:**
> Did you install Ubuntu first, then windows? If so, windows overwrites the ubuntu bootloader, so that windows always starts first.

Pazaz - I'm 17 too :p

Not So sure about what you mean about the Ubuntu first then windows? I bought this computer as a windows...

---

### Post by TNT1 on 2010-09-21
> **Pazaz said:**
> ? It says Loading Windows, Why? goes through the acer screen loading thing for about 1 second, Then for 5 seconds says Press f2 and etc. Buttons for the functions, You know. I just want to know how.

So you can boot into windows, but not ubuntu?

Spin up your live cd again and reinstall GRUB to the MBR.

---

### Post by Pazaz on 2010-09-21
> **TNT1 said:**
> So you can boot into windows, but not ubuntu?

Spin up your live cd again and reinstall GRUB to the MBR.

First Off, Idk what Grub is, Second, I don't have a cd drive. Netbook.

---

### Post by ronnielsen1 on 2010-09-21
I think this may be the problem

> **BIOS is not set to boot from CD or DVD drive**

 Some  computers are set to boot directly from the hard drive.  This should be  as simple as entering the BIOS, enable booting from the CD-ROM drive,  and making sure that the CD-ROM is before the hard drive in the boot  order. 
The  most common way to enter the BIOS is to press the DELETE key when the  computer is first booted(this seems to be becoming standard).  On other  systems it could be a different key, or combination of keys like ESC,  F1, F2, F10, F12, Ctrl-Esc, Alt-Esc, Ctrl-Alt-Esc, Ctrl-Alt-Enter, Ins  or even others.  You might have to press, press and hold, or press  multiple times. The best way to find out the details of that is to look  in the users manual or search the manufactures website

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by TNT1 on 2010-09-21
> **Pazaz said:**
> First Off, Idk what Grub is, Second, I don't have a cd drive. Netbook.


How'd you install ubuntu? usb flash disk? How did you create the usb install disk? From Windows?

---

### Post by ronnielsen1 on 2010-09-21
> First Off, Idk what Grub is, Second, I don't have a cd drive. Netbook.

You posted while I was posting

You could use unetbootin to create a live usb that you could boot your netboot from

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

> UNetbootin allows you to create bootable Live USB drives for Ubuntu,  Fedora, and other Linux distributions without burning a CD. It runs on  both Windows and Linux.

or instlinux (Haven't tried it}
[http://sourceforge.net/projects/instlux/](http://sourceforge.net/projects/instlux/)

---

### Post by Pazaz on 2010-09-21
> **TNT1 said:**
> How'd you install ubuntu? usb flash disk? How did you create the usb install disk? From Windows?
A mounting program. Why?

---

### Post by Pazaz on 2010-09-21
I'll try that program out. It says I can do it without a usb? True?

---

### Post by Pazaz on 2010-09-21
First program works perfectly so far. Going to finish trying it out by rebooting.

---

### Post by Pazaz on 2010-09-21
This'll take a while to finish extracting on the program though, Eh?

---

### Post by TNT1 on 2010-09-21
> **Pazaz said:**
> A mounting program. Why?

Make a new liveusb with unetbootin, and try again.

---

### Post by DrMelon on 2010-09-21
Say, when you were installing Ubuntu, did it ask you where to install it? As you may have just installed it onto the very same USB drive you were using, instead of onto the internal hard drive.

---

### Post by Pazaz on 2010-09-21
> **TNT1 said:**
> Make a new liveusb with unetbootin, and try again.

I did the correct one right: I made a Ubuntu Live one, Is that the one?

---

### Post by Pazaz on 2010-09-21
> **DrMelon said:**
> Say, when you were installing Ubuntu, did it ask you where to install it? As you may have just installed it onto the very same USB drive you were using, instead of onto the internal hard drive.
And It said Where to install it, I chose C:/

---

### Post by DrMelon on 2010-09-21
> **Pazaz said:**
> And It said Where to install it, I chose C:/

Did it ask you if you wanted to install it alongside Windows? ("Split the hard drive between the two")

---

### Post by TNT1 on 2010-09-21
> **Pazaz said:**
> And It said Where to install it, I chose C:/

It did? Ubuntu doesn't use that naming convention for drives. It should have read hda1 or something like that.

---

### Post by Joe of loath on 2010-09-21
Maybe he used wubi?

---

### Post by TNT1 on 2010-09-21
> **Joe of loath said:**
> Maybe he used wubi?

Maybe.

---

### Post by Phrea on 2010-09-21
So sorry to be off-topic, but this is such an entertaining thread.

I think he indeed did a Wubi install, that's the only way I know of that will actually install Ubuntu on the C: drive.

---

### Post by Pazaz on 2010-09-21
Heh. I dd use Wubi, But alls fine, I used that Live cd thingy, And Now I got UBUNTU up and running! Thanks! Now if you would tell me a link for some apps and games?

---

### Post by Pazaz on 2010-09-21
o.e Why is everything so fast on ubuntu compared to windows? It scares me.

---

### Post by Pazaz on 2010-09-21
Fun games and apps. I found one website, But I forgot the name... Crap....

---

### Post by Pazaz on 2010-09-21
Oh Yeah, [https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games)

---

### Post by Phrea on 2010-09-21
> **Pazaz said:**
> Heh. I dd use Wubi, But alls fine, I used that Live cd thingy, And Now I got UBUNTU up and running! Thanks! Now if you would tell me a link for some apps and games?

Try the Ubuntu Software Center under Applications.

---

