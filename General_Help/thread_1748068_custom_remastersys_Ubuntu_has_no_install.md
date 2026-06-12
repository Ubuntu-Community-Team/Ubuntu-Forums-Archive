---
title: "custom remastersys Ubuntu has no install"
date: 2011-05-03
forum: General Help
---

### Post by elliotn on 2011-05-03
hi I did a remaster of my installation. all went well, the CD boots well as livecd but it has no install icon on the desktop. the is the example folder. how do I install my custom Ubuntu

---

### Post by elliotn on 2011-05-03
bump

---

### Post by elliotn on 2011-05-03
anyone please help

---

### Post by elliotn on 2011-05-03
desperate

---

### Post by QLee on 2011-05-04
[QUOTE=elliotn]desperate[/QUOTE]
I've never used remastersys but it is popular around here so I have seen it mentioned in posts. I'm fairly sure that there is a menu item left to do what you are trying to do. I can't check it but try somewhere in the System-->Administration section of the live system you created, maybe there is something there.

---

### Post by mike555 on 2011-05-04
You needed to have ubiquity and ubiquity-frontend-gtk installed ........ I don't know if you can install it after making the iso while running it live ....... maybe, if it works please let us know.

---

### Post by bodhi.zazen on 2011-05-05
Remastersys is an easy way to make a live iso of your desktop, but, it is, IMO, not the best way to make a custom iso.

I know it is not exactly what you are asking, but, if you want to make backups, IMO there are better methods.

If you want to make a custom iso, you will need to do some reading, and not everything is well documented.

By far the easiest method, IMO, is to use the live-build scripts. Yes they have a learning curve to them as well, but the advantage is they are more versatile and easier to customize.

"Easier" here being somewhat relative, sometimes to make a modification you need to build a custom initrd, which means you need to know how to do that. Once you have extracted the initrd, and know the exact change you need to make, then the live-build scripts automate the build of the (custom) initrd.

References:

Good first read:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

This page in invaluable, you will want to at least be familiar with all or most of the options:

[http://manpages.ubuntu.com/manpages/natty/en/man7/live-build.7.html](http://manpages.ubuntu.com/manpages/natty/en/man7/live-build.7.html)

You can see there are both text and graphical installer included and an option to include (or not) the installer when running live.

See also:

[http://live.debian.net/manual/en/html/live-manual.html](http://live.debian.net/manual/en/html/live-manual.html)

---

### Post by Megaptera on 2011-05-05
> **elliotn said:**
> hi I did a remaster of my installation. all went well, the CD boots well as livecd but it has no install icon on the desktop. the is the example folder. how do I install my custom Ubuntu

Having booted in to my Remastersys backup CD/DVD - I go menu > system > control panel > install release. And that works for me.

---

### Post by bodhi.zazen on 2011-05-05
> **Megaptera said:**
> Having booted in to my Remastersys backup CD/DVD - I go menu > system > control panel > install release. And that works for me.

Thank you for posting that information.

---

### Post by Megaptera on 2011-05-05
> **bodhi.zazen said:**
> Thank you for posting that information.

You're welcome! 
:)

---

### Post by Jose Catre-Vandis on 2011-05-05
Or just reboot and pick "Install" from grub ;)

[EDIT]
>> Off topic >> I'll never post again, spooky bean count number achieved ;)

[ATTACH]191257[/ATTACH]

---

