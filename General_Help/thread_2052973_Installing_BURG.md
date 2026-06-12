---
title: "Installing BURG"
date: 2012-09-04
forum: General Help
---

### Post by newb85 on 2012-09-04
So, I want to install BURG according to the directions at [http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/).  The directions are a little unclear at one point.  They say to 
```
 sudo burg-install "(hd0)"
```
and say
> Remember to substitute ‘hd0&#8242;  with the drive on which your MBR is installed.
Now, if drives are assigned letters (e.g., sda, sdb, etc.) and partitions are assigned numbers (e.g., sda1, sda2, sdb1, etc.), what exactly should I be substituting for 'hd0'?

---

### Post by cortman on 2012-09-04
> **newb85 said:**
> So, I want to install BURG according to the directions at [http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/).  The directions are a little unclear at one point.  They say to 
```
 sudo burg-install "(hd0)"
```
and say

Now, if drives are assigned letters (e.g., sda, sdb, etc.) and partitions are assigned numbers (e.g., sda1, sda2, sdb1, etc.), what exactly should I be substituting for 'hd0'?

If it's your primary drive, it's probably /dev/sda. No number (which would indicate a partition).
But I would advise against installing burg- its concept is very cool, but in reality its a bit sub-par, and the project appears to be dead (last update to the mailing list was 2 years ago).
Try the [grub-customizer]("http://ubuntuforums.org/showthread.php?t=1664134") instead.

---

### Post by 2F4U on 2012-09-04
If you read the comments, someone ask almost the same question as you do. The answer is to replace "hd0" with "/dev/sda", given that /dev/sda is the disc where the MBR is installed.

---

### Post by newb85 on 2012-09-04
> **2F4U said:**
> If you read the comments, someone ask almost the same question as you do. The answer is to replace "hd0" with "/dev/sda", given that /dev/sda is the disc where the MBR is installed.
Thanks!  I probably should have read the comments more carefully.

---

### Post by newb85 on 2012-09-04
> **cortman said:**
> If it's your primary drive, it's probably /dev/sda. No number (which would indicate a partition).
But I would advise against installing burg- its concept is very cool, but in reality its a bit sub-par, and the project appears to be dead (last update to the mailing list was 2 years ago).
Try the [grub-customizer]("http://ubuntuforums.org/showthread.php?t=1664134") instead.

Thanks for the advice.  I don't usually like jumping onto dead projects.  How exactly is it "sub-par"?

I've tried grub-customizer, and wasn't overly impressed.  It works great for controlling the displayed entries, playing with colors, and adding a background image, and not much else.  Playing with fonts never yielded the fonts I selected, and rendered several characters as ?'s.

---

### Post by cortman on 2012-09-04
> **newb85 said:**
> Thanks for the advice.  I don't usually like jumping onto dead projects.  How exactly is it "sub-par"?

I've tried grub-customizer, and wasn't overly impressed.  It works great for controlling the displayed entries, playing with colors, and adding a background image, and not much else.  Playing with fonts never yielded the fonts I selected, and rendered several characters as ?'s.

It doesn't do resolution correctly. Maximum is something like 1280x1024 (IIRC), which looks bad with widescreens.

---

### Post by newb85 on 2012-09-04
I'm befuddled.  I tried following the directions, and apparently, the PPA didn't add correctly.  

> E: Unable to locate package burg
E: Unable to locate package burg-themes

Now, when I try to use add-apt-repository to remove it again, 

> Error: 'deb [http://ppa.launchpad.net/n-muench/burg/ubuntu](http://ppa.launchpad.net/n-muench/burg/ubuntu) precise main' doesn't exist in a sourcelist file
Error: 'deb-src [http://ppa.launchpad.net/n-muench/burg/ubuntu](http://ppa.launchpad.net/n-muench/burg/ubuntu) precise main' doesn't exist in a sourcelist file

This is really odd, since I can still go to /etc/apt/sources.list.d and find a file n-muench-burg-precise.list, which contains

```
# deb http://ppa.launchpad.net/n-muench/burg/ubuntu precise main
# deb-src http://ppa.launchpad.net/n-muench/burg/ubuntu precise main

```
I noticed that the lines are commented out.  I tried uncommenting them, but that didn't seem to change anything.

---

### Post by cortman on 2012-09-04
> **newb85 said:**
> I'm befuddled.  I tried following the directions, and apparently, the PPA didn't add correctly.  



Now, when I try to use add-apt-repository to remove it again, 



This is really odd, since I can still go to /etc/apt/sources.list.d and find a file n-muench-burg-precise.list, which contains

```
# deb http://ppa.launchpad.net/n-muench/burg/ubuntu precise main
# deb-src http://ppa.launchpad.net/n-muench/burg/ubuntu precise main

```
I noticed that the lines are commented out.  I tried uncommenting them, but that didn't seem to change anything.

Did you run

```
sudo apt-get update
```

between adding the PPA and trying to install burg?

---

### Post by newb85 on 2012-09-04
> **cortman said:**
> Did you run

```
sudo apt-get update
```between adding the PPA and trying to install burg?

Boy, do I feel sheepish.

Initially, I did run apt-get update.  However, after I discovered that the file in /etc/apt/sources.list.d was all commented out, I un-commented it, but didn't apt-get update again.

That did the trick.

Anyone know why add-apt-repository left the file commented out like that?

---

### Post by newb85 on 2012-09-04
@cortman,
Perhaps I should have heeded your advice and steered clear of burg.

I could live with the resolution, but I'm not sure how to fix two things:
Icons - The Ubuntu Icon is loaded for Lubuntu, and a question mark is used for Peppermint.  Is it using a set of icons made specifically for burg?
List - The list currently has too many entries for Ubuntu.  This problem actually occurred in the normal GRUB, but I hoped (foolishly) that it would go away when I installed burg.

---

### Post by cortman on 2012-09-04
> **newb85 said:**
> @cortman,
Perhaps I should have heeded your advice and steered clear of burg.

I could live with the resolution, but I'm not sure how to fix two things:
Icons - The Ubuntu Icon is loaded for Lubuntu, and a question mark is used for Peppermint.  Is it using a set of icons made specifically for burg?
List - The list currently has too many entries for Ubuntu.  This problem actually occurred in the normal GRUB, but I hoped (foolishly) that it would go away when I installed burg.

Burg development probably ceased before the advent of Peppermint. I don't know where it gets its icon sets...
I was a big fan of Burg back in the day (which is why your post caught my eye) but I wasn't completely pleased with it.
If you're interested in removing burg you can use [these instructions]("http://ubuntuforums.org/archive/index.php/t-24113.html") to reinstall Grub to your MBR.

---

### Post by mcduck on 2012-09-05
> **cortman said:**
> It doesn't do resolution correctly. Maximum is something like 1280x1024 (IIRC), which looks bad with widescreens.
This is not correct. I use BURG on my laptop, running at 1920x1080, with 24-bit colors. Works just fine. :)

...and there should be plenty of widescreen resolutions available even if your display's full resolution isn't supported, so going for any smaller wide-screen resolution available should at least give you decent image with correct aspect ratio.

---

### Post by mcduck on 2012-09-05
> **newb85 said:**
> @cortman,
Perhaps I should have heeded your advice and steered clear of burg.

I could live with the resolution, but I'm not sure how to fix two things:
Icons - The Ubuntu Icon is loaded for Lubuntu, and a question mark is used for Peppermint.  Is it using a set of icons made specifically for burg?
List - The list currently has too many entries for Ubuntu.  This problem actually occurred in the normal GRUB, but I hoped (foolishly) that it would go away when I installed burg.

The icons are not magically brought to BURG from your installed operating systems, BURG simply has pre-made themes with whatever graphics the theme designer used. So if you want different icons you need to switch to different BURG theme, or edit one to fit your preferences.

What comes to the amount of Ubuntu ebtries in Grub/BURG, that's simply a question of how many kernel version you have installed on your machine. (As you might knwo, kernel updates will not overwrite the old kernel, but instead install new version alognside the old one). BURG has the option to hide the extra entries and only show the latest kernel version, but the best solution (with any bootloader) is to uninstall the old kernel versions you aren't using any more. This will automatically remove them from the bootloader, and of course also frees some disk space for you...

---

### Post by newb85 on 2012-09-05
> **mcduck said:**
> What comes to the amount of Ubuntu ebtries in Grub/BURG, that's simply a question of how many kernel version you have installed on your machine. (As you might knwo, kernel updates will not overwrite the old kernel, but instead install new version alognside the old one). BURG has the option to hide the extra entries and only show the latest kernel version, but the best solution (with any bootloader) is to uninstall the old kernel versions you aren't using any more. This will automatically remove them from the bootloader, and of course also frees some disk space for you...

Actually, I didn't know that.  Now that you mention it though, I have seen entries stack up like that in the past.  I've just never cared, because I only ever wanted the top one (the latest kernel for Ubuntu) or on very rare occasions, the one for Windows.  Now that I have multiple Ubuntu variants installed, it makes things more complicated.  I will try to remove the old kernel versions.

---

### Post by cortman on 2012-09-05
> **mcduck said:**
> This is not correct. I use BURG on my laptop, running at 1920x1080, with 24-bit colors. Works just fine. :)

...and there should be plenty of widescreen resolutions available even if your display's full resolution isn't supported, so going for any smaller wide-screen resolution available should at least give you decent image with correct aspect ratio.

My bad. Although I never got it to display correctly, it was apparently more my fault than Burg's. Thanks for the clarification!

---

### Post by mcduck on 2012-09-05
> **cortman said:**
> My bad. Although I never got it to display correctly, it was apparently more my fault than Burg's. Thanks for the clarification!

No worries, it could be related to something like graphics card as well. (my old laptop wasn't able to get correct resolution with Burg, based on what I found out because the firmware of the card was missing identifier for the correct resolution.).

..and, to be honest, Burg is quite slow with high resolutions anyway, so I recommend using smaller resolution with correct aspect ratio instead.

---

### Post by dcstar on 2012-09-06
> **newb85 said:**
> So, I want to install BURG according to the directions at [http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/).  The directions are a little unclear at one point.  They say to 
```
 sudo burg-install "(hd0)"
```
and say

Now, if drives are assigned letters (e.g., sda, sdb, etc.) and partitions are assigned numbers (e.g., sda1, sda2, sdb1, etc.), what exactly should I be substituting for 'hd0'?

You should actually use:
```
sudo dpkg-reconfigure burg-pc
```
And you will be given a list of valid places to install the bootloader.

As well, read this:

[http://ubuntuforums.org/showpost.php?p=12220971&postcount=6](http://ubuntuforums.org/showpost.php?p=12220971&postcount=6)

---

