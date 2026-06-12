---
title: "basic system imaging software"
date: 2010-02-12
forum: General Help
---

### Post by sdwinder on 2010-02-12
I am looking for a very basic system imaging software

I am trying to image a computer running xubuntu 9.10 and save the image file to a flash drive

the drive itself is about 120gb big, but the used space on it is only about 10 gb at most.

I want to make the image of the used space only so i can basically clone it to other computers..

I have tried many different ways of doing this and so far ive had no luck

I tried to use partimage, but when i boot up using a live cd and install partimage to run it, it tells me that the partition size is 120gb (basically it tells me the drive is full, when its not) i find this weird because partimage advertises that the only thing it can do is to save only the used space.

I have tried G4l (ghost for linux) but it does the same thing as well.

All i need is to make an image of the used space on this computer and save it, preferrably to an iso file or something, it can even be proprietary format, i dont care, at this point ill take anything.

thanks for any help you guys can provide

---

### Post by kaibob on 2010-02-12
Have you tried Clonezilla? It only includes used space in the image. It's very popular and has worked great for me. 

[http://clonezilla.org/](http://clonezilla.org/)

Be sure to use the Ubuntu-based version. It work's best with ext4.

---

### Post by sdwinder on 2010-02-12
I did try it, it also apparently only lets you use the entire disk, when i tried to save it, it showed the partition size to be the full 117 gb, I assumed it was only showing it for the sake of you being able to determine what it is, but ya...it was trying to save all of it from what i could tell. It told me that the temp file it tried to create in my flash drive did not have enough room (flash drive had 14gb of free space)

---

