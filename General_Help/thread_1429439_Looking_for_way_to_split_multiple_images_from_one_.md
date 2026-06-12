---
title: "Looking for way to split multiple images from one image."
date: 2010-03-14
forum: General Help
---

### Post by lavinog on 2010-03-14
I am helping a friend who scanned a bunch of photos.  I have a couple of gigs of png files, each with 5-7 photos on each file.  Currently I am making 5-7 duplicates of the file, then opening each one in gimp, and cropping and saving each one...kind of time consuming.

Does anyone know of a program that will let me split an image into multiple slices?

---

### Post by mcduck on 2010-03-14
> **lavinog said:**
> I am helping a friend who scanned a bunch of photos.  I have a couple of gigs of png files, each with 5-7 photos on each file.  Currently I am making 5-7 duplicates of the file, then opening each one in gimp, and cropping and saving each one...kind of time consuming.

Does anyone know of a program that will let me split an image into multiple slices?

I can't say I'd ever hard of image slicing app for Linux.

However you're doing it in a bit more complicated way than you need to. Just open your big image (no multiple copies necessary!), crop it as you like (Shift-c), save as new file (Shift-Ctrl-s), undo to get back to the big image (Ctrl-z), crop the second one and again save as new file, undo back to big image and repeat until done... :D

Of course if all the big image files were exactly the same size and the images in them aligned in the same way you could use a simple Imagemagick script to do the slicing automatically. But since you said that you have 5–7 images per file that's probably not an option.

---

### Post by lavinog on 2010-03-15
I found a solution to divide scanned images:
[http://registry.gimp.org/node/22177](http://registry.gimp.org/node/22177)
It requires the gimp-deskew-plugin:
[http://www.cubewano.org/gimp-deskew-plugin/](http://www.cubewano.org/gimp-deskew-plugin/)

Unfortunatly the deskew-plugin needs to be compiled for 64bit, and running configure complains that my gimp version (2.6) doesn't meet the requirements (requires gimp2.0)
The deb package does work on my 32bit laptop, and will suffice to get this project done.

I might consider making my own version in python eventually.

---

### Post by lavinog on 2010-03-16
Well the above solution didn't work out as I was hoping, I had to go back and verify each image, and I noticed that it didn't complete the job.

So I made my own program (see attached)

---

### Post by lavinog on 2011-01-09
Updated script with a file selection dialog.

---

### Post by rewolff on 2011-08-23
Bravo!

I've been looking allover for something that would do this automatically, but the things I found didn't work well enough. (I tried it on a scan of 200 pages of about 500 pictures, and it extracted one photo correctly). 

Anyway, doing it by hand is do-able as long as it doesn't cost much time. I just did the 500 pictures in about an hour....

---

### Post by blurymind on 2012-08-12
thats very useful!!

Is there a way to modify the script so it overwrites the original image that you cropped upon closing the window?

---

### Post by prometheus2k on 2013-02-02
You have now Idea how many Years i've been searching for something like this!!! :popcorn:

I only registered here to download this Script and it is better then i was hoping. I used to scan all of our Family Photo Albums around 10 Years ago. Now i finaly found some time to split the Scans into a single File per Photo. 

Thank you very much! You've saved me a lot of work.

---

### Post by ikaps on 2013-02-23
I've been lokking for something like this for a long time  to split my scanned photos. Thank you, lavinog! =D>

---

### Post by ismael-b-e on 2014-01-28
What exactly do I do when i open the zip. Theres like a .txt file in it. I am a noob sorry

---

### Post by romain4 on 2014-05-17
> **lavinog said:**
> Updated script with a file selection dialog.


So perfect ! thank you so much !!!

---

### Post by k-veikko2 on 2014-07-24
My problem was solved by multicrop
[http://www.fmwconcepts.com/imagemagick/multicrop/index.php](http://www.fmwconcepts.com/imagemagick/multicrop/index.php)

This is also practical for patching.

---

### Post by zachary10 on 2014-09-29
WOW!  This is a great, simple tool!  I too am extremely happy to see this--it's so much faster than doing it manually in GIMP.  I too got an Ubuntu account just to download the file...Thanks!

---

