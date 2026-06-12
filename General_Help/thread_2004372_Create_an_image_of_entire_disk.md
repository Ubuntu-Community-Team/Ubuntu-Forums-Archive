---
title: "Create an image of entire disk"
date: 2012-06-15
forum: General Help
---

### Post by bdemers on 2012-06-15
I must swap out my internal drive.  I'd like to take the 200 or so GB of space and image that to an external drive using the Ubuntu 12 cd. The drive is formatted using ext4. Read many issues around Brasero, any suggestions to make this transfer both ways (to/from external from/to internal) a bit less painless, or am I over reacting to what's been posted?  I am aware of home folder backups, but in this case I want complete apps, drivers, confs, etc to be transported.  Push button, walk away. Once. 

I am aware of Clonezilla.

---

### Post by kanikilu on 2012-06-15
Will Clonezilla not work for you? If not, there's always dd.

[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

---

### Post by dbrooke on 2012-06-25
Bedemers,
What did you end up doing?

Here are the issues I've ran into:

** Note: I'm a bit of a newb **

I tried using the SystemRestoreCD method based off of this as a guide:

[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)

The problem that I found with using partimage is that it does not support ext4 fs type, which is a pain because partimage, compared to clonezilla, allows one to copy only the non-free space from a partition.. where clonezilla you need to have a drive (to copy the image to) at least the size of the partition being copied.

So the question remains in my mind.. What is the best way for Ubuntu 12.04 Server administrators to create easy disk images?

I have to admit, I am used to VMWare where it is as simple as pressing a button to create a snapshot of the entire machine. I don't expect that, but I do expect to be able to find resources for ext4 formatted (Ubuntu 12.04), best practices for creating disk images.

Any comments?
Thanks,
Donovan

I haven't found that so far.

---

### Post by bdemers on 2012-06-25
Well, I ended up with Clonezilla, as a matter of convenience. In my case I have a large external drive and a clone of the existing hd was easily accommodated by the external.  In fact I have 3 different machines on that 1 external. 

I quite honestly did not pursue this any further as all I wanted to do was get in and then out. Perhaps not the most scientific approach, but gosh, at some point you gotta choose your battles.

---

