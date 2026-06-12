---
title: "Before photoshop"
date: 2011-04-25
forum: General Help
---

### Post by Total Noob on 2011-04-25
I downloaded a nice photo of someone and put it into my pic library under Ubuntu 10.10.

When I came back to the library to reproduce the pic, the thumbnail that appeared was apparently the original pic, before it was cropped and possibly other changes made with Photoshop or some other program. Moments later the thumbnail changed to the final form of the pic.

I tried to get the whole thing again with Gimp and other programs, but all I was able to see after launching a program was the final changed version.

Is there a way to get an original pictures back as it was taken by the camera, ie, to de-photoshop it? Are the prior versions there, as with other kinds of datafiles?

This is important to me because I have to work with photographs that are supposed to be used as evidence, and it is crucial to know what was cut out of the picture and what was enhanced and when so I can spot phony evidence.

Thanks

---

### Post by zipperback on 2011-04-25
If you edited the image and saved it over the original, then no, the file has been altered.

My advice is to simply download it from your camera again, and make a backup of the image before you edit.

- zipperback
:popcorn:

---

### Post by cgroza on 2011-04-25
Well, you can GIMP or Photoshop it back, but if it was cropped, it is pretty much gone.

---

### Post by dragonfly41 on 2011-04-25
I don't know how to reverse your changes as the others have written .. but for evidence you can read the meta-tags of the image.

If you go to Synaptic Package Manager ..

install libimage-exiftool-perl

then run this command on your image

sudo exiftool <path_to_image>/image.jpg

[Credits: [http://forensiccop.blogspot.com/2009/09/experiment-10-on-analysing-fake-image.html](http://forensiccop.blogspot.com/2009/09/experiment-10-on-analysing-fake-image.html) ]


P.S. you might still have a copy of your original image in cache .. search by date

[http://learn--photoshop.blogspot.com/2010/01/quick-tip-23-clear-purge-cache.html](http://learn--photoshop.blogspot.com/2010/01/quick-tip-23-clear-purge-cache.html)

---

### Post by Total Noob on 2011-04-26
> **zipperback said:**
> If you edited the image and saved it over the original, then no, the file has been altered.

My advice is to simply download it from your camera again, and make a backup of the image before you edit.

- zipperback
:popcorn:


I suppose I wasn't sufficiently clear. The pic I downloaded was from the Internet. I also get pics from other people that may have been photoshopped.

I suppose the answer is the same as already given, but can the original image -- what I saw for a second or two before the final image settled in on file browser -- be retrieved under those circumstances? 

I have seen the metatags for that kind of stuff in Windows and in other programs. It is useful in that it that sometimes says when it was photoshopped if at all. But more important is the original image so I can tell if something has been added or deleted to phony up a claim.

This is why I try to use film: you can go back to the original negative.

Thanks.

---

### Post by dragonfly41 on 2011-04-26
Look in browser cache history .. as suggested earlier.

---

### Post by Maheriano on 2011-04-26
If you look at the EXIF data on the photo, it will usually tell you every Photoshop effect that was done to it. But if you want to restore it to its original, it's impossible. Unless you have the .XCF or .PSD files for it.

---

