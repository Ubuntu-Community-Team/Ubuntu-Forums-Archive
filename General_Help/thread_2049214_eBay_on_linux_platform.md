---
title: "eBay on linux platform"
date: 2012-08-28
forum: General Help
---

### Post by Ycanti on 2012-08-28
OK we all know Skype sucks on any linux platform. Now eBay does as well.

I can't sell items on ebay when i use the linux platform. No link to upload photos and it keeps asking me to get a paypal account which i already have. Switching over t****o Win7 NO problem. Straight forward?

Any ideas? Is it a MS conspiracy?

---

### Post by MARP1961 on 2012-08-28
I use eBay with Linux and Firefox browser. When I try to upload photographs before selling it offers an alternative uploader which always works. Not sure if this is a browser or Linux problem.

---

### Post by Ycanti on 2012-09-03
problem solved.

was browser. not sys. Sorry Linux

Now how do i label it solved?

---

### Post by jmate24 on 2012-09-03
in the Thread Tools menu up above the first post in the right hand corner.

---

### Post by uschmuntu on 2012-12-26
I cannot use ebay on linux, and can therefore cannot use ebay at all, as I will never again in this lifetime use microsoft windows or a mac.

 firefox does not work properly,  I cannot find my picture files even though they are there in the file manager. It's as if the files have an unknown extension, but they absolutely do not. 

Ebay supports only three browsers, firefox, safari and internet explorer.

---

### Post by kaldor on 2012-12-26
> **uschmuntu said:**
> I cannot use ebay on linux, and can therefore cannot use ebay at all, as I will never again in this lifetime use microsoft windows or a mac.

 firefox does not work properly,  I cannot find my picture files even though they are there in the file manager. It's as if the files have an unknown extension, but they absolutely do not. 

Ebay supports only three browsers, firefox, safari and internet explorer.


That's odd. Check a couple of things:

- Check to see if there is an alternative uploader; some sites use one, and using a fallback/basic option almost always works.

- Try using a different browser (grab Chromium from the repos)

- Ensure that you have Flash and Java installed

---

### Post by uschmuntu on 2012-12-27
I have been at this all day.
when the canon powershot a2200 is connected, the built in file manager opens atgphoto2://[usb:002,009]/ but cannot create thumbnails and also when double-clicked the built in picture viewer opens but has a blank screen. Once the photos are copied onto the computer they can be viewed but not retrieved from within ebay site on firefox. There is no hidden attribute or hidden extension.

---

### Post by uschmuntu on 2012-12-27
ok "basic uploader" works so ebay's "standard uploader" must be using flash which fails to even find the files.
It's a flash problem. Even though the files are viewable, ordinary .jpg files right there on my desktop, flash cannot find them.
 I can still find no option whatsoever in chromium or epiphany to upload my own photos at all.

Now I just have to spend another day figuring out how to rotate the photo which already appears rotated when opened in editors but is wrong orientation on ebay.
So now all photo apps show the photo the right way, but I am supposed to rotate them? re-save them? none of these image programs make it clear whether you are applying the rotation to the image or just for viewing.

ok so I found gthumb program, which presented the photo the same way ebay wanted to. Then I  clicked "reset EXIF orientation" and rotated it although I'm not sure if I needed to or not. I am still confused.
How am I supposed to know if a photo needs to be rotated or not(and which way) when all the image viewers rotate it automatically?

---

### Post by paulie-m on 2012-12-27
I use opera with xubuntu 11.10 and  no problems with ebay.

---

### Post by ArminasAnarchy on 2012-12-27
Personally I have no problem using Skype. What's your issue?

---

### Post by uschmuntu on 2012-12-27
Here is my summary of the various technical/software failures for just  this particular wasted day trying to do something which should have  taken only five minutes:

 **Canon** powershot 2200 camera supports mass storage standard, as does linux(**gphoto2**).  Only problem with standards is that they are anything but. In my case  the folder is mounted but thumbnails are absent and when image files are  double-clicked the image viewer(**GPicView**) opens with an empty screen. ***FAIL***.  
Workaround  is to copy files to the computer after which they are then thumbnailed  and open correctly. This is no good though because I do not want to copy  the entire contents of my camera to the computer, and need the  thumbnails to identify which photos I actually need. So I had to install  more software just to get the photos from the camera. After **F-spot** failed to do anything but crash instantly, Shotwell did the trick.

**Ebay** uses **Flash**  software, presumably to resize photos before uploading them, thus  saving time and data and improving compatibility with their website.  Only problem is it doesn't work properly if at all. In my case when  browsing the computer for the image file the **Canon** jpg files were simply not there. Invisible. ***FAIL***. 
Workaround  is to use Ebay's fallback "basic uploader" except that the images are  in the wrong orientation even though Ebay is getting the entire file  including the EXIF data which describes the correct orientation. ***FAIL***.
Now  image files have a top, a bottom, a left and a right. And since the  advent of orientation detection inside of digital cameras you would like  to think that problems of incorrect orientation were a thing of the  past. But instead of using this orientation detection to create portrait  and landscape mode jpg images, this **Canon** camera instead uses an  EXIF standard which merely tags images whilst leaving the jpg image  uncorrected. Thus image viewing programs which can be bothered to read  the EXIF data will present the image correctly, but when sending the  image to others such as uploading to ebay the user must remember that  all portrait mode images could end up being viewed with incorrect  orientation as is the case with ebay. ***FAIL***.

---

