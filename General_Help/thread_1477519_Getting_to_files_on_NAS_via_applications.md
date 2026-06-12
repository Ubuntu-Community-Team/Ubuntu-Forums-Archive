---
title: "Getting to files on NAS via applications"
date: 2010-05-08
forum: General Help
---

### Post by louis_mallow on 2010-05-08
This is a real newb's question. I can't get to my files on a NAS once I'm in an application.

Example: 
I have a text/graphic file to open from the NAS. I can see it in Nautilus, and can double-click there to open in OpenOffice/Gedit/Gimp. 

Once I'm working I want to open another file so in my application I go File > Open

From there I can't see the NAS. (Interestingly I can see a locally-connected USB hdd).

Do I really have to go through Nautilus every time I want to open something from the NAS?

---

### Post by The Real Dave on 2010-05-08
Perhaps the easiest way is to make a bookmark. Most applications will show these on the left hand side of their "Open File" dialogs. To do this, go to the directory you want in Nautilus, in the menu bar, click the "Bookmark" tab, then click "Add Bookmark". You should now see it in the bookmark list below the drive list on the left hand side. It'll also appear in your "Places" menu.

To find out where your NAS is actually located, go to it in Nautilus, and click the button just below the back button on the left hand side. The tab navigator should change to an address bar, showing you the location of your NAS eg /media/NAS

When opening a file, you can usually type that into the Open File dialog, to be taken to that directory.

---

### Post by dcstar on 2010-05-08
> **louis_mallow said:**
> This is a real newb's question. I can't get to my files on a NAS once I'm in an application.
........
Do I really have to go through Nautilus every time I want to open something from the NAS?

There are HOWTOs on mounting network devices on boot, it would be better to search them out for detailed instructions.

Essentially the /etc/fstab file has an entry for each network device and automatically mounts it at boot time, then you just have that resource in your filesystem like any other.

Currently your NAS may appear in /media once accessed by Nautilus (I am not sure on this).

---

