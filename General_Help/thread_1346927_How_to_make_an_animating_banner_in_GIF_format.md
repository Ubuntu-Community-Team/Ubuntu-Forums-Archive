---
title: "How to make an animating banner in GIF format?"
date: 2009-12-05
forum: General Help
---

### Post by MKVCrazy on 2009-12-05
Hi, I've recently moved to Linux Ubuntu 9.10 64-Bit. I am a little out of knowledge of linux apps which are alternatives of some Win apps. I have been using Selteco Banner Animator to create simple, yet professional looking animated banners in a few clicks. All I want to add in the banner is a simple 1 solid colour background and some texts flash in and out every few seconds so I can put more information in little pixel size (400x200).

Is there an alternative to that and as easy as it is?

These are the steps I take to do a banner, just an example how easy it was.

1. New file
2. Select Size
3. Type in texts and align
4. Choose animation types of each text and set intervals for each too
5. Save in .GIF and ready to use

EDIT

Please read my last reply. I've decided to install Windows in VirtualBox to use my old animator but I am stuck there. Need help.

---

### Post by fluffman86 on 2009-12-05
[http://www.gimp.org/tutorials/Simple_Animations/](http://www.gimp.org/tutorials/Simple_Animations/)

---

### Post by MKVCrazy on 2009-12-05
Thanks fluf, no idea why I didn't think of searching for a tutorial from its very own website. But I tried it for more than 20 minutes now, I still can't get an animating banner done. I am thinking to edit and reupload the newly banner like every 30 minutes, so if creating one will take 20 minutes I don't think it's so easy enough. Any more suggestions?

---

### Post by StuartN on 2009-12-05
> **MKVCrazy said:**
> I am thinking to edit and reupload the newly banner like every 30 minutes, so if creating one will take 20 minutes I don't think it's so easy enough. Any more suggestions?

ImageMagick tools do command line animation, with a lengthy tutorial at [http://www.imagemagick.org/Usage/anim_basics/](http://www.imagemagick.org/Usage/anim_basics/)

It will take you some time to create the command, and virtually no time to reuse it.

---

### Post by MKVCrazy on 2009-12-05
I decided I should give VirtualBox a try and use my old animator but I am stuck installing Windows in VirtualBox.

I have installed the non-open version of VirtualBox because I read that the open one doesn't have USB support. Now I am at all the up to starting the OS but I cannot find an option to load my .ISO files of Windows intead of booting from the CD/DVD ROM.

How can I make it load from the .ISO since there's no option for it? Or I am forced to use the OSE one?

---

### Post by MKVCrazy on 2009-12-06
Anyone? I'm stuck and I can't pass or do anything until I can find the "Load from ISO Image" option in VBox 3.1.0 for Karmic 64-Bit.

---

### Post by bacardiandwatermelon on 2009-12-06
If you click on cd/dvd rom, put a tick on mount cd/dvd drive, then click iso image file... It should act like a cd rom and you should be able to boot from it...

---

### Post by MKVCrazy on 2009-12-06
> **bacardiandwatermelon said:**
> If you click on cd/dvd rom, put a tick on mount cd/dvd drive, then click iso image file... It should act like a cd rom and you should be able to boot from it...
Can you please take a screenshot of that option? I cannot see anything like that around the CD/DVD ROM option. :(

---

### Post by bacardiandwatermelon on 2009-12-06
here ya go..

---

### Post by MKVCrazy on 2009-12-06
We are on different versions of VirtualBox. I'm using the closed-source version. Even though it's the closed-source, I don't see the ISO Image option.

May I know what OSE version you are using? I would like to try your version and see if it works for me.

Here are my screenshots

---

### Post by pbrane on 2009-12-06
gifsicle is a great command line tool for creating animated gifs from images.

---

### Post by MKVCrazy on 2009-12-06
Ok, I downloaded the latest version of VirtualBox OSE from repositories. I found the CD/DVD ROM Image and I selected my WindowsXP.iso for that. So I started the VM and I get the following error in a terminal window:

**FATAL: No bootable medium found! System halted.**

I've found many similar threads/topics on Google and when I follow them mine still will give this error. I've read and tried to follow at least 4 methods found on the internet to fixing this problem. All don't work.

I'm running Linux Ubuntu Desktop 9.10 64-Bit, if this matters. Please I really need help on this. I've got something to do on my computer which I am only good with a Windows app.

EDIT:

I will like to share what I did as this was the problem which took half of the day of my time today.

Check the followings,

- You are using the basic recommended settings
- You are not a corrupted ISO Image file like I did.

---

