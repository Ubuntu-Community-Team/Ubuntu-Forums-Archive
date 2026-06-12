---
title: "gpodder default download folder"
date: 2010-10-08
forum: General Help
---

### Post by GrouchyGaijin on 2010-10-08
Hi,

I read that I can change the default download folder for gpodder by editing gpodder's config file.
The problem is I don't know they syntax to specify where I want to downloads to be stored.

I want them stored in a folder called podcasts which is on an external drive.  In Windows this drive has the letter e in Ubuntu it shows up as the drive label which is elements.  

I tried a couple of things and ended up with gpodder creating a folder called e in my home folder.

---

### Post by searchfgold6789 on 2010-10-08
When you see your disk in your Places menu at startup, your drive is "mounted". It is mounted at a location on your hard disk. (So if you click into the folder on your system hard disk where the drive you are talking about is mounted, you will see and can read from and write to the drive from the folder)
In order to correctly edit the config file, you have to find out at what location your drive is mounted, and then enter the name of the folder into your config file.
Common mounting locations are /mnt and /media.
"/" is your system partition.
FOR EXAMPLE.
I have a secondary hard disk that mounts at startup. It's label is sheetmusic. It's mounting location is /media/sheetmusic. When I enter into my file manager, I click on my system hard disk, which is "File System", (it shows up as "/"), then I double click the folder media and then sheetmusic, to see, add to, and open the contents of my secondary harddisk.

---

### Post by GrouchyGaijin on 2010-10-08
That did it - thanks.

---

