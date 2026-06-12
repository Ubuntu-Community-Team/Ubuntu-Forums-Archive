---
title: "Anyone using ubuntu 11.04 WITH ATI Radeon 6770 graphics card?"
date: 2011-10-02
forum: General Help
---

### Post by pkhamidar2com on 2011-10-02
Hello, before i install ubuntu, i want to see if anyone else has my problem or has a fix or is doing the same thing as me. 

Basically i have a 6770 graphics card, i tried the live CD version of ubuntu and it was fine, except the resolution was out. It was at a 5:4 or something resoltuion. 

So im wondering, does anyone here who is using a 6 series, specifically 6770 ati graphics card, have been able to achieve different resolutions such as 16:9 or 16:10, im using a 1440x900 monitor. 

anyways thanks :)

---

### Post by wanderingarticfox on 2011-10-02
I am not using a 6770, however I am using an ATI V4800 Workstation card. After about two weeks of contacting ATI I finally found out that they only write Proprietary Drivers for Gnome. There are ways to get the Catalyst Proprietary drivers of the latest version, I however choose to use the ones  that have been tested and deemed stable by the Ubuntu Staff. You can go to

[http://www.amd.com/us/products/desktop/graphics/amd-radeon-hd-6000/Pages/amd-radeon-hd-6000.aspx](http://www.amd.com/us/products/desktop/graphics/amd-radeon-hd-6000/Pages/amd-radeon-hd-6000.aspx)
 
and read up on things like the latest driver and previous drivers. Also look at these links:

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

The first has a warning notice but both have links to more information.

I use the System>Administration>Additional Drivers I use the Gnome desktop. It is the simplest way to get the last tested and stable Drivers for ATI. If you are more advanced than I am you can look at
 
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

Good Luck:cool:

---

### Post by pkhamidar2com on 2011-10-02
i really want that really cool mac like design 11.04 has, that unity thingy, what is gnome?

---

### Post by SeijiSensei on 2011-10-02
> **wanderingarticfox said:**
> I am not using a 6770, however I am using an ATI V4800 Workstation card. After about two weeks of contacting ATI I finally found out that they only write Proprietary Drivers for Gnome.

I doubt that's correct; it sounds more like a clueless customer support response.  I had no trouble installing the ATI proprietary driver from the Additional Drivers application in Kubuntu on my daughter's HP laptop with a Mobile Radeon 67xx card.  (I did have to upgrade the BIOS to get the video adapter to run in "fixed" mode, but that's a whole different issue.)

The video driver works with the kernel and X; the desktop environment should have nothing to do with it.

@OP
GNOME is one of the various "desktop environments" that run on top of Linux.  It's the one distributed with all versions of Ubuntu prior to 11.04, when Unity was introduced.  I use Kubuntu with the K Desktop Environment (KDE).  Unlike Windows, Linux doesn't have a monolithic desktop; like most other Linux and open-source offerings you have choices.

---

### Post by pkhamidar2com on 2011-10-02
ok so your saying that my 6770 should work fine, and i should be able to achieve resolutions of 1440x900 yes?

also i still dont reallyunderstand what it does. 

Whats the difference between unity and gnome and kde and everything?

and... will unity work on my 6770?

thats all. Ill be installing tomorow, really didnt have time today, too much studies :'( dunno if i will have time tomorow but hopefully will :)

---

### Post by SeijiSensei on 2011-10-02
> **pkhamidar2com said:**
> ok so your saying that my 6770 should work fine, and i should be able to achieve resolutions of 1440x900 yes?

Yes.  It may work correctly "out-of-the-box," but you're better off running the Additional Hardware application in Ubuntu to install the proprietary driver for your video card.

> also i still dont reallyunderstand what it does.

The driver translates commands from the operating system into code the video card uses to display objects on the screen.

> Whats the difference between unity and gnome and kde and everything?

[http://lifehacker.com/5762081/wtf-desktop-environments-gnome-kde-and-more-explained](http://lifehacker.com/5762081/wtf-desktop-environments-gnome-kde-and-more-explained)

> and... will unity work on my 6770?

I don't know; I don't use Unity.  The best answer I can give is "probably."  Maybe someone else can help, or you could just give it a try.  The best way to learn about Linux is via experimentation.

---

### Post by larrypg on 2011-10-02
I have the 6770 and the fans will run fast out of the box.  Install additional drivers and no more high speed fans. Unity will work fine with both drivers.

---

### Post by wanderingarticfox on 2011-10-03
> **SeijiSensei said:**
> I doubt that's correct; it sounds more like a clueless customer support response.  I had no trouble installing the ATI proprietary driver from the Additional Drivers application in Kubuntu on my daughter's HP laptop with a Mobile Radeon 67xx card.  (I did have to upgrade the BIOS to get the video adapter to run in "fixed" mode, but that's a whole different issue.)

The video driver works with the kernel and X; the desktop environment should have nothing to do with it.

@OP
GNOME is one of the various "desktop environments" that run on top of Linux.  It's the one distributed with all versions of Ubuntu prior to 11.04, when Unity was introduced.  I use Kubuntu with the K Desktop Environment (KDE).  Unlike Windows, Linux doesn't have a monolithic desktop; like most other Linux and open-source offerings you have choices.

I never said I was a Guru I only wrote what was sent to me by ATI Linux Development team. I think you should temper your voice friend, maybe even follow the path backward to ATI before insulting someone![-X  I did have trouble in Kubuntu because I could not access the ATI Catalyst Control centre and change the default resolution for my CRT Monitor; I'm sure an LCD laptop would handle a 1900 by resolution, a CRT does not. Well it does but the icons are really small and all the adjustments I made with Icon and Fonts still had me leaning forward in my chair.

---

### Post by ZmoAndre on 2011-10-19
Hi there,

i have a Radeon 6770 . and you can acheive high resolution in ubuntu... but i'm having trouble enabling the 3d graphics capability... but if you are just installing ubuntu to surf the web and not play any game you are fine.

---

