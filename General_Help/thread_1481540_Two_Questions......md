---
title: "Two Questions....."
date: 2010-05-12
forum: General Help
---

### Post by kelpie_canada on 2010-05-12
I have two questions that ai need help with.

The first is about a download I did form Betty Crocker recipe site. They sent me an e-book of recipes for my birthday but when I downloaded it, it came up as gm_birthdayparties_unix.zip and I can't open it. I also received another e-book from them gm_cookiesbarscakes_pdf.zip which I have no problem opening. My question is how do I change the first one to a pdf or how do I open it as it sits?

Secondly, I uploaded to my system a dvd from my friend of her granddaughters first birthday and when I tried to put in on a dvd of my own I found that the file is to large for the disc. How do I compress the video to fit the disc?

As always Thank you for your help.

Katie

---

### Post by howefield on 2010-05-12
If you can open one zip file, you should be able to open the other.

Do you get an error when it fails ?

You could try Devede to make your dvd, if the data is in excess of the capacity of the disk, you can use the option "adjust disc usage" to make it fit.

What's the file format of your video ?

---

### Post by bredman on 2010-05-12
To test if the zip file is faulty or not...

Use the File Manager from the Places menu to open the folder which contains the file.

Right-click on the file and open with Archive Manager

If this works, select the menu item File/Test integrity.

Look at the last line of the result to see if any errors were found.

Let us know if you hit any errors along the way.

---

### Post by kelpie_canada on 2010-05-12
> **bredman said:**
> To test if the zip file is faulty or not...

Use the File Manager from the Places menu to open the folder which contains the file.

Right-click on the file and open with Archive Manager

If this works, select the menu item File/Test integrity.

Look at the last line of the result to see if any errors were found.

Let us know if you hit any errors along the way.


I did as you said and this is what I get"No errors detected in compressed data of /home/kpringle/Documents/Recipes/gm_birthdayparties_unix.zip."

When I click on open with archive manager I get two files:
nxtbookfx.swf    type Shockwave
readme.txt       type plain text document

The first brings up the movie player with and error message"failed to decode JPEG image"
The second brings up Open Office with the message"To load the digital publication, open the included .swf file in a 
web browser that has Adobe (formerly Adobe) Flash Player installed."

When I open the other e-book gm_cookiesbarscakes_pdf.zip with archive manager I get one file.
gm_cookiesbarscakes.pdf     type pdf document.
which then opens to a pdf format then I can read the book.

---

### Post by kelpie_canada on 2010-05-12
> **howefield said:**
> If you can open one zip file, you should be able to open the other.

Do you get an error when it fails ?

You could try Devede to make your dvd, if the data is in excess of the capacity of the disk, you can use the option "adjust disc usage" to make it fit.

What's the file format of your video ?

I don't know what Devede is or where the option "adjust disc usage is found. I think the file format is .iso.

---

### Post by achase79 on 2010-05-12
the swf is usually playabe within a web browser as long as the flash plugin is installed

---

### Post by kelpie_canada on 2010-05-12
> **achase79 said:**
> the swf is usually playabe within a web browser as long as the flash plugin is installed

I am sorry but I have no idea what this means. If I try to open the file in a webbrowser it asks me what I want to do with it ie: save or open with archive manager.

---

### Post by howefield on 2010-05-13
> **kelpie_canada said:**
> I don't know what Devede is or where the option "adjust disc usage is found. I think the file format is .iso.

Devede is an application for taking video files and writing them to a DVD which you can then play a standard dvd player.

It is installable via Synapatic Package Manager which you'll find in System > Administration > Synaptic Package Manager.

Load it up and type Devede in the Quick search field.

Click the check box to the left of Devede, and select Mark for installation, you may get a dialogue window advising of dependancies which are required to run Devede, in this case, accept them. Then press the apply button to the left of the Quick search field. Once installed you'll find it in Applications > SOund & Video.

Once loaded, you will be prompted for which type of disc you wish to create, svcd, dvd, ect, ect. See first Screenshot.

Select Video DVD, see screenshot 2.

Change the properties of the title to rename it as you wish, add the the video file, and press adjust disc usage if required.

---

### Post by howefield on 2010-05-13
Just to add if the "iso" is an iso of the original DVD, you may be able to right click the file and select Open with Brasero, and burn straight to a DVD.,

---

### Post by koanhead on 2010-05-13
> **kelpie_canada said:**
> I have two questions that ai need help with.

The first is about a download I did form Betty Crocker recipe site. They sent me an e-book of recipes for my birthday but when I downloaded it, it came up as gm_birthdayparties_unix.zip and I can't open it. I also received another e-book from them gm_cookiesbarscakes_pdf.zip which I have no problem opening. My question is how do I change the first one to a pdf...

If the two files were both encoded as PDF then all you need to do is change the name of the file to one that has a .pdf file extension.

> Secondly, I uploaded to my system a dvd ... and when I tried to put in on a dvd of my own I found that the file is to large for the disc.

If the file came from one DVD, then it should fit on another of the same type. If you are using GnomeBaker or Brasero to make the DVD, make sure that the program knows that the disk to which you are burning is a DVD and not a CD. (GnomeBaker has a bar at the bottom of its window indicating how much space the files will take on the disk. Next to this bar is a drop-down menu with a list of media types: 70 minute CD, 80 minute CD, DVD, etc. I don't know how Brasero handles this as I don't use it.)

---

