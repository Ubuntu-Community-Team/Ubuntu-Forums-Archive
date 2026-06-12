---
title: "Formatting a floppy?"
date: 2009-08-07
forum: General Help
---

### Post by davethewave83 on 2009-08-07
==SOLVED==
Ubuntu is fairly old, I am wondering why there still is not yet implemented the simple option of formating a floppy disk via UI? 

instead of having to research the command online, it would be nice to have a simple click-format option within Ubuntu. :D

Edit* 
and for those "You still use floppy?" no i do not personally, it is for my sister. She obtained some really old laptop and I require a floppy to set up an OS.

I ended up using gfloppy, which worked but it was not user friendly to get to like a right-click format option. :D
==SOLVED==

---

### Post by HermanAB on 2009-08-07
What is a floppy?
;)

---

### Post by brodeur235 on 2009-08-07
It's VERY common for os developers to create floppy images for their OS's since a floppy image is just a simple flat binary with a .img extension. Anyways, it's very, VERY simple to install these things. I have a GUI application called "Floppy Formatter" but I have never used it... You might want to research that if you're dead set on a GUI app. However, installing the OS to a floppy can be done very simply with just a hex editor... Here you go for your CLI instructions:

1.) Open your hex editor (I use hexcurse; it's very good. Don't use GHex; it won't work).
2.) From within your hex editor open your floppy disk image file (it probably has a .img extension)
3.) Copy the contents of this file to the clipboard
4.) From within your hex editor, open your actual floppy disk (probably /dev/fd0 or something) and paste the contents from your clipboard onto the very start of the floppy and save. 

You should hear the floppy drive rev up and overwrite the contents of the floppy with the OS. But yeah... That's all that is required; a simple copy, paste, and save. Then it's up to you to know how to get your computers boot menu up and select "boot from floppy"

Alternatively, you can just use a emulator to run the OS directly from the floppy image (free ones include VBox (use this if you like GUIS) and Bochs (use this if you're into CLI) )

I hope I helped,

Brodeur235

---

### Post by davethewave83 on 2009-08-07
Thanks, I think we are missing the point though ;) 

Ubuntu is supposed to be "Linux for Human Beings" 

for example, my mother, she is a human being. She would have no clue what a hex editor is, or how to use a terminal to use fdformat etc. 

She would expect, as a human being, to right click and format. 

I understand myself how to format a floppy, and if I do not know how then at least I know how to do the research and ask the community (and what a wonderful community it is :D) for help, but others like my mother would not know how to troubleshoot it quite as well. 

that is all I am saying, a simple click-format is very handy. Even if floppies are ancient and out dated they still come in use at times.

---

### Post by lildigiman on 2009-08-07
You're mother is a human being, therefore _able to learn_. If she can learn, she can find out what a Hex Editor is and learn how to use the terminal...

---

### Post by ke4ram on 2009-08-19
I cannot believe a ugly reply like I just read! The individual asked a relevant question. All that was necessary was

Goto Preferences -> Main Menu 
Next Click System Tools
Check Floppy Formatter
Close

Goto Applications -> System Tools -> Floppy Formatter

Now format your disk!!!

---

### Post by elliotn on 2009-08-19
Format is needed in ubuntu, instead of using gparted to format flash drive or a new haddrive, why the developers dont just add the format  option when u right click on that drive, or make a simple terminal command like the c:/format d: in windows

---

### Post by angry_johnnie on 2009-08-19
there is an app that does this, called gfloppy.  just hit alt + f2 and type gfloppy.

---

### Post by 3rdalbum on 2009-08-19
> **davethewave83 said:**
> Ubuntu is fairly old, I am wondering why there still is not yet implemented the simple option of formating a floppy disk via UI? 

The first version of Ubuntu was in 2004, floppy disks were dead by 2000.

There isn't a lot of point to dedicating developers to allowing Gnome to detect that a disk is a floppy disk, provide a menu item, etc when there are more pressing things to work on. Gparted and Gfloppy are programs that can format floppies in the extremely rare event that anyone would want to use a floppy disk.

For your particular use case, you are formatting a floppy disk so you can install an operating system on an old computer. This isn't something that computer-illiterate people do.

---

### Post by davethewave83 on 2009-08-20
> **3rdalbum said:**
> The first version of Ubuntu was in 2004, floppy disks were dead by 2000.

There isn't a lot of point to dedicating developers to allowing Gnome to detect that a disk is a floppy disk, provide a menu item, etc when there are more pressing things to work on. Gparted and Gfloppy are programs that can format floppies in the extremely rare event that anyone would want to use a floppy disk.

For your particular use case, you are formatting a floppy disk so you can install an operating system on an old computer. This isn't something that computer-illiterate people do.

I am not claiming to be computer-illiterate, I know my way around computers of any OS quite well. I am not always around my mother however to show her how to format a floppy, many instructions I do tell her she often forgets. Adding the code for the developers should be a piece of cake as they have the experience and coding abilities to do so pretty much on the fly as professionals, it should take them under an hour at most to implement it, which would not hinder their more pressing matters much at all. 

After reading older forums I saw that the right-click format option was actually implemented at one point, which would suggest that they actually made an effort to remove it for whatever reason.

However, I have just created a link to Gfloppy for this use and this topic is now solved.

ke4ram please do not worry about other posters making ugly comments, it is quite expected on the internet. People tend to become trolls online, even though in person they may be very delightful individuals. lildigiman was probably only experiencing an internet ego-trip (I am guilty of the same at times) 

"smart" people are often stupid because they expect everyone else to have the same level of intellect on the matter as they do, and when the person does not, the belittling and mockery begins (which is actually worse than being computer illiterate).

 Mother was not born in the age that I was nor in an environment in which technology was prominent, therefor it is only natural that she may be a bit slow with it and need assistance. 

regardless of the ego maniacs, Ubuntu still has a wonderful community of support. So thank you all for your contributions to this matter, I am most grateful.

---

