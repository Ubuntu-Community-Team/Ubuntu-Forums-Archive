---
title: "Portable needs OS..."
date: 2009-12-18
forum: General Help
---

### Post by Himself2007 on 2009-12-18
Hello

Please don't be hard with me!:)
One of my computer, an old Compaq LTE5300 with a P1-133MHz with 32 MB.Ram, 950MB HD, would be glad to receive a new OS!
So I need a reasonably light OS that supports network sharing functions and if possible...internet!
Internet access is not mandatory but it would be nice to have!
It has to be graphical UI like Ubuntu.
Any idea, anybody?
Thanks

Luc

---

### Post by Darael on 2009-12-18
Well, I would immediately suggest DSL ([www.damnsmalllinux.org](www.damnsmalllinux.org)) or Puppy ([www.puppylinux.org](www.puppylinux.org)). Alternatively, do a minimal install of just about anything (even Ubuntu, using the Alternate CD) and add a lightweight window manager such as Fluxbox or Enlightenment and some light apps for your purposes.

---

### Post by snowpine on 2009-12-18
Hi Himself, give the Ubuntu minimum system requirements a look and decide if you still think your project is realistic: 

> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection

---

### Post by Dark_Stang on 2009-12-18
Get a new computer if at all possible.

---

### Post by Darael on 2009-12-18
Don't be disheartened by those saying it can't be done - older computers can be made quite usable with a little work. Standard Ubuntu is out of the question, but I believe you'd realised that. DSL and/or Puppy should make the machine run pretty fast, and if you really wanted to make it fly there's other options, but they often require a lot more work.

---

### Post by Dark_Stang on 2009-12-18
> **Darael said:**
> Don't be disheartened by those saying it can't be done - older computers can be made quite usable with a little work. Standard Ubuntu is out of the question, but I believe you'd realised that. DSL and/or Puppy should make the machine run pretty fast, and if you really wanted to make it fly there's other options, but they often require a lot more work.

> **Himself2007 said:**
> P1-133MHz with 32 MB.Ram, 950MB HD
I'm sorry, but let's be real here.
32 MB of ram. What web browser, or modern application, can run on that? You can get away running DSL in command line, maybe even get X to start. But what are you going to do? Sit there and stare  at your cursor?

133Mhz Processor. Even DSL's recommended specs state 200mhz. And, again, being realistic... what modern application or web browser can run on this?

950MB HD. Okay, so this is probably the best part. Disregard the fact that in the United States this hard drive would be old enough to get a driver's license, it's big enough to install a minimalistic OS on.

In all seriousness, your only possible suggestion *may* be menuet.
[http://www.menuetos.net/index.htm](http://www.menuetos.net/index.htm)
But this would be a miserable existence as a primary OS.

As I stated in my last post. If at all possible, get a new computer.

---

### Post by Himself2007 on 2009-12-18
> **snowpine said:**
> Hi Himself, give the Ubuntu minimum system requirements a look and decide if you still think your project is realistic:
According to what I wrote in my first post, I don't think so!:lolflag:

H2007

---

### Post by jerrrys on 2009-12-18
how bout

[http://www.junauza.com/2009/04/5-best-bsd-distributions.html](http://www.junauza.com/2009/04/5-best-bsd-distributions.html)

---

### Post by Chronon on 2009-12-18
Check out Tiny Core Linux

[http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

> Tiny Core Linux is a very small (10 MB) minimal Linux GUI Desktop. It is based on Linux 2.6 kernel, Busybox, Tiny X, and Fltk. The core runs entirely in ram and boots very quickly. Also offered is Micro Core a 6 MB image that is the console based engine of Tiny Core. CLI versions of Tiny Core's program allows the same functionality of Tiny Core's extensions only starting with a console based system.

It is not a complete desktop nor is all hardware completely supported. It represents only the core needed to boot into a very minimal X desktop typically with wired internet access.

---

### Post by arvevans on 2009-12-18
I had similar issues with installing Linux on an older 700 MHz computer.  I went the usual route of trying many "tiny Linux" versions, and trying to strip down Ubuntu, use Ubuntu Server and adding Gnome, etc.  Several of these stripped-down systems worked acceptably, but also had problems that I was not willing to live with.

Finally, I installed Debian Linux with Gnome, and now my older computers are quite happy.  It does take a long time to install.  Booting the latest Debian on an older computer does take several minutes, but once it is up and running, the X-window manager with Gnome seems quite responsive.  Some larger applications (browsers, Open Office, etc.) still take a while to open the first time they are used, but once they are loaded into core they run quite well.

Not sure if this will work for everyone, but I found that a conventional install of Debian Linux is adequate for those 600 to 700 MHz older computers with 256+ MB of RAM, and at least 4 GB of HD.  Try makingg Swap space so that  Swap plus RAM totals around 1 GB, as this seems to be a viable compromise between swap speed (old hard drives are slower) and how much you need to have in-core at any one time.

Now, what does this say about Debian...probably that the slowness of current Debian on older machines is due to what Ubuntu has added to Gnome and the Debian OS, and not due to slowness of the bare Debian OS.  This could provide some clues for future Debian development directions, that they might want to look at cutting some of the overburden...or at least make it's installation and activation an option for the installer & user.
_._

---

### Post by Himself2007 on 2009-12-18
> **Darael said:**
> Don't be disheartened by those saying it can't be done - older computers can be made quite usable with a little work. Standard Ubuntu is out of the question, but I believe you'd realised that. DSL and/or Puppy should make the machine run pretty fast, and if you really wanted to make it fly there's other options, but they often require a lot more work.

Hello Darael

Thanks for you support. You understand me!;)
Before all I have to explain something here.
I don't want to revive this old computer because I can't afford a new one or something.
It's not a matter of death or life!
I actually have five with different machines with different configs and multi-booted for different OS'es. 
Ubuntu is one of them and runs really really well!
The main reason is that it's fun to test new things like new OS'es and solve multiple problems based on limitations.
Some like me consider this as a hobby.
You see? Sometimes speed is not the ultimate prime factor.
I already have very fast computers when needed.
But it's a matter of choice you'll say and I agree.

You see? Right now I just forgot to mention something important.
I don't have a USB port, no CD-Rom and no possible (?) way to access my network card from my network.
So how will I be able to install?
Maybe the com port? Or a king of gismo to get in the RJ-45?
I think I will have fun!!! Good!
Let's get into this!

Luc

---

### Post by Darael on 2009-12-18
Some distributions (Debian for one, you'd have to check about others) have a netboot floppy image, if that's any help. Otherwise, you'd have to do something like installing with the hard drive in another machine and moving it across...

---

### Post by Darael on 2009-12-18
Once you've got a system of some sort installed, you may want to read some of the posts on *Motho ke motho ka botho* - a blog whose author appears have a particular fondness for giving suggestions on getting super-lightweight terminal apps going, including for such things as web browsing and even getting MPlayer going *in the console* on a machine with only slightly higher specs than the one you're looking at. It's at [http://kmandla.wordpress.com/](http://kmandla.wordpress.com/) if you want to take a look.

---

### Post by Himself2007 on 2009-12-18
> **Darael said:**
> Some distributions (Debian for one, you'd have to check about others) have a netboot floppy image, if that's any help. Otherwise, you'd have to do something like installing with the hard drive in another machine and moving it across...

Darael

You inspire me.
Yes you are right.
I only have to take the HD out of the portable and put it inside one of my removable rack/drive on a computer.
This HD has a DOS 300MB partition, another one with 300 MB storage and an empty 600 MB partition.
I only need an adaptor cable from IDE to small HD.
And few other bug to solve naturally.

Luc

---

### Post by Himself2007 on 2009-12-18
By the way...
If anybody have a "software" way to access my network port for uploading that big file on my computer, it will surely be appreciated!
As it is really cold outside and I just don't want to shop for this adaptor!:)
This computer has a working DOS 6.22 and nothing else!!!
So experts...be advised that if you can help, you're welcomed.
Take the challemge with me! Where are the real experts???
Let's get this MS-DOS based oldie rockin' on my network.
:guitar:

Luc

---

### Post by Darael on 2009-12-18
Well, if your computer supports booting from its network card, you really should consider a netboot floppy from some distro or other or setting another of your machines up to support loading the installer over the local net. I know that's not exactly what you've asked for, but it's as close as I know how to do...

---

### Post by deadalus.globalnode on 2009-12-18
Personally I would go with Slackware although it takes quite a bit of learning. I have a computer with similar specs ( although a bit more ram ) and it does Slackware just fine. but as it was mentioned before go with fluxbox, or IceWM. as for internet you could use a text based browser. you wouldn't get flash but expecting that in the first place would be a little much.

---

### Post by Himself2007 on 2009-12-18
> **Darael said:**
> Well, if your computer supports booting from its network card, you really should consider a netboot floppy from some distro or other or setting another of your machines up to support loading the installer over the local net. I know that's not exactly what you've asked for, but it's as close as I know how to do...

No way to boot from network port...forget it.
That's a quite new feature if I don't mistake.

Luc

---

### Post by Darael on 2009-12-18
Yes, booting straight off a network port would be a relatively new feature, but a netboot floppy boots from the floppy and then gets the installer over the network, so it might still work...

---

### Post by Himself2007 on 2009-12-18
> **Darael said:**
> Yes, booting straight off a network port would be a relatively new feature, but a netboot floppy boots from the floppy and then gets the installer over the network, so it might still work...

Darael

...netboot floppy...
It just seems interesting.
What is this?
_Please_ explain and show available ressources if you can.
I think I'll get to bed much wiser tonite!
Thanks

Luc

---

