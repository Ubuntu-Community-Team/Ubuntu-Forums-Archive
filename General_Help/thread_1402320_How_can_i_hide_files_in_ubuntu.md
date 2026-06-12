---
title: "How can i hide files in ubuntu"
date: 2010-02-09
forum: General Help
---

### Post by aviramof on 2010-02-09
say i  don't want to see windows 7 system files i want them to be hidden how do i do that?

also i have just finished installing ubuntu what do you recommend i  would download already downloaded rar and unrar and fix the problem with  url files what eles?

thanks in advance.

---

### Post by aviramof on 2010-02-09
how can i save screenshots and etc in other formats othr then png for exemple jpg?

---

### Post by Enigmapond on 2010-02-09
Well to hide files in Ubuntu you but a dot '.' in from of the file name.

It really all depends on what you are using the computer for or what you're trying to accomplish.

What other format do you want to save screenshot?

---

### Post by chillicampari on 2010-02-09
But please don't put a dot in front of your windows system files.

---

### Post by keya.nema on 2010-02-09
You can just specify the valid extension of the image type.  For eg.  Screenshot.jpg.

You can use gimp or any other image editing tool too change the format later, if required.

---

### Post by jamesisin on 2010-02-09
Why would you be seeing Windows system files in your Ubuntu installation?  Did you do a Wubi installation?

---

### Post by chillicampari on 2010-02-09
I used to see them when I had a dual boot and mounted the NTFS drive(s), but just ignored them.

---

### Post by rnerwein on 2010-02-09
hi
if you don't touch your windows files they are ignored.
if you don't want to see them - don't mount the windows file system(s).
if you want to see them - mount your windows filesystem 
see man: mount / unmout 
what is your problem ???
ciao

---

### Post by aviramof on 2010-02-09
ok about the dot infront of file i understand that i can't use with my windows 7 system files as for screenshot 
i'm use to jpg because it's not as heavy as png in i want to upload a screenshot of my background to my forum and i'm limited to  300KB i can't use 1.2mb png file i have to upload it somewhere eles which i did 

so just changing the name doesn't mean a lot to me i need the compression even that the quality in consider less good then png.

and [rnerwein]("http://ubuntuforums.org/member.php?u=972890") you need to understand that your seeing it all wrong i can't not mount my ntfs partition they are in fact the bulk of my computer less then a week ago i did not used ubuntu or any other os other then windows now i'm using ubuntu but i still have windows 7 installed and since my current version is alpah 10.04 i still need my seven for a lot of things so your looking it all wrong your if you know what i mean.

---

### Post by Morbius1 on 2010-02-09
You could do something like this:

(1) Create a mount point in /mnt, for example:

[B]sudo mkdir /mnt/Windows
[/B] 
(2) Create an entry in fstab that mounts the partition at boot, for example:

**/dev/sda1 /mnt/Windows      ntfs    defaults,umask=777    0    0**
 
It won't show up under "Places" in nautilus, it won't show up on the desktop, and with umask=777 not even root will be able to touch it.

---

### Post by amsterdamharu on 2010-02-09
NTFS in linux has no hidden or system option like in windows, the best you can do is hide the entire partition like previously mentioned.

Both Windows and Ubuntu by default (install) don't do a good job on separating system, user settings and produced files like documents and stuff. A good setup for Ubuntu would be to create a separate partition for /home. 

A good setup for windows would be to put documents and settings somewhere else than C: so the OS and installed programs do not get mixed up with your settings and documents/pictures/videos/...

This mix up is solved in Windows by making files hidden/system/read only and access permission but Linux does not support these things when mounting NTFS. A good admin usually has Windows using a network share for impotent folders in Documents and Settings. The system can allways be ghosted back but produced files and user preferences take work hours ($$$) to create.

Ubuntu solves it by putting all user specific stuff in /home but still mixes up settings and user created files, settings are then hidden by putting the dot as first character in the file/directory name.

---

