---
title: "Problems holding me back from full time usage"
date: 2009-10-16
forum: General Help
---

### Post by maflynn on 2009-10-16
I've been using Ubuntu now for a few months and I would love to make the jump to 100% usage but have been hindered so far.

So here's a list of issues that I'm hoping some folks can help me resolve in some way.

1. Printer driver support for canon pixma pro9000, I see a driver for the pixma pro9500 but no 9000.  Any recommendations on a compatible printer driver

2. iTunes, what player is compatible to play my DRM-less .m4a music. 

3. LightRoom user, I need an app that can organize and non-destructively edit my images.  I tried running LR under wine but it doesn't run.  Other alternative is to virtualbox and a copy of winblows - kind of defeats the purpose that I'm intending though

4. Backup/Restores.  My lack of knowledge here is probably the cause.  I use two applications for backup/restore.  The Apple delivered/provided Time Machine that does hourly backups onto an external drive.  This allows multiple time points to restore from.  A full system restore is possible but incredibly slow (8+ hours)  Because of that, I also use Carbon Copy Cloner, a free app that does a block by block cloning and its restore is much quicker.  I'd like something similar with Ubuntu

My current usage of Ubuntu is to connect to my work network remotely and work from home.  I'd like to be able to use Ubuntu for everything else.  #1 & #3 are the major issue, I can work around issues 2,4 but without being able to manage my images, Ubuntu isn't a viable solution for my main environment.

I need to manage and print my photos

---

### Post by lavinog on 2009-10-16
> **maflynn said:**
> 
1. Printer driver support for canon pixma pro9000, I see a driver for the pixma pro9500 but no 9000.  Any recommendations on a compatible printer driver

according to this site:
[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_Pro9000](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_Pro9000)
your printer driver isn't included yet, and turboprint may be your only option:
[http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_Pro9000](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_Pro9000)


> 
2. iTunes, what player is compatible to play my DRM-less .m4a music. 

Pretty much anything should be able to play them once you install the restricted extras:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


> 
3. LightRoom user, I need an app that can organize and non-destructively edit my images.  I tried running LR under wine but it doesn't run.  Other alternative is to virtualbox and a copy of winblows - kind of defeats the purpose that I'm intending though

It looks like there is no solution for getting lightroom to work on linux at the moment.
I have never used lightroom, but it sounds similar to picasa which does work on linux.

There are many backup solutions available that do what you want,  I don't know which ones to recomend because I just use rsync.  Rsync is not easy to learn at first, but it gives you a lot of control.  

The os can be reinstalled pretty easily.  for drive imaging there is partimage, and clonezilla.

---

### Post by rmockler on 2009-10-16
My reply deals with your image management and editing concerns.  Post #2 referred to Picasa.  I have a close friend who is a professional photographer, half dozen high tech cameras, who swears that PhotoShop is the only way that he can get the results he needs, and Gimp just doesn't match it.  But he uses Picasa to manage his vast photo collection. So I installed Picasa on my  Ubuntu system, and I can clearly see why he uses it.  Although the photo editing doesn't match up with PhotoShop or even Gimp, it is completely adequate for my amateur use, and now I am a big Picasa advocate. So, I would suggest that you give it a try, and if it doesn't satisfy you, you can just uninstall it.

---

### Post by maflynn on 2009-10-16
Thanks, I'll look at picassa

I like LightRoom (Apple's aperture is the same way) because the edits are non-destructive.

---

### Post by KlinerDraken on 2009-10-16
I would have to suggest "Back in Time" as a back up client. I think it uses rsync as a back end. 

```
sudo apt-get install backintime
```

---

### Post by Giblet5 on 2009-10-16
As for the printer, I purchased a license for TurboPrint drivers for my Pixma MP830.

I can reliably print to printable CDs/DVDs now, and borderless photos work as expected. Those are the toughest tests.

I also sent a complaint email to Canon for not supporting Linux.

---

### Post by Giblet5 on 2009-10-16
> **KlinerDraken said:**
> I would have to suggest "Back in Time" as a back up client. I think it uses rsync as a back end. 

```
sudo apt-get install backintime
```

I think it's ```
sudo apt-get install backintime-gnome
``` these days, old-timer... ;)

---

### Post by KlinerDraken on 2009-10-16
> **Giblet5 said:**
> I think it's ```
sudo apt-get install backintime-gnome
``` these days, old-timer... ;)

:oops: thanks for the correction :oops:

---

