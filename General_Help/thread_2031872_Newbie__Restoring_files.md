---
title: "Newbie ? Restoring files"
date: 2012-07-22
forum: General Help
---

### Post by sktlsr7 on 2012-07-22
Hello, I am very new to linux and Ubuntu so please bare with me. 
 
I am working off a windows based tablet that crashed and the I dont want to risk repering the windows 7 so I used Ubuntu. I accidently deleted files from an internal hard drive while in Ubuntu that I need to put back. I had a lot of cables on the table and one hit deleted while I was reading another screen. They got moved to the Trash bin in Ubuntu. When I hit restore I get an error message: Error while moving file: Permission denied. I assume I need to have write access to the internal hard drive befroe I can restore the files. How can I accomplish this? Or how can I force the files in the trash bin to a USB.

---

### Post by Sandertje on 2012-07-22
Where in the hard drive would the files be going to? If they are going anywhere else than somewhere on your home folder, you won't get there without the right permissions.

Perhaps the easiest things you can do is type the following in a terminal

```
sudo nautilus
``` 

You will be asked for your password, upon which a file browser will launch. This will now have root permissions.

---

### Post by texpat on 2012-07-22
Hmm.. if those files can only be restored with root privileges, how did you manage to delete them in the first place?

Anyway, if you type ```
sudo nautilus
``` into a terminal, you'll get a file manager with root/superuser privileges and you should be able to restore from there.

---

### Post by oldfred on 2012-07-22
Better to use gksu nautilus.

You use sudo for text or command line tasks and gksu or gksudo for gui tasks. Sometimes it works, but others will not without the gksu.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)

---

### Post by ironic.demise on 2012-07-22
First of all, using ```
gksu nautilus
``` will give super-user priveleges, but a small warning, if you delete anything as root/super-user it will be deleted **forever**. secondly if you do use that command you want to go to the directory /home/whatevertheusernameis/.local/share/trash and your files will be there.

if you cannot see .local press ctrl+h to show hidden files.

or use this ```
sudo cp /home/$USER/.local/share/Trash/* ./
```
I'm pretty sure you don't *need* to change the user part in that last bit, but you can if it helps.

---

### Post by oldfred on 2012-07-22
+1 on ironic.demise warnings.

When in super user mode you can totally damage a system, only use gksudo nautilus for a specific task and immediately close it.

---

### Post by sktlsr7 on 2012-07-22
> **texpat said:**
> Hmm.. if those files can only be restored with root privileges, how did you manage to delete them in the first place?

Anyway, if you type ```
sudo nautilus
``` into a terminal, you'll get a file manager with root/superuser privileges and you should be able to restore from there.

I have no idea how it let me delete but I can't make any other changes to files on that drive. I'll try everyone's tips tomorrow and report back.

---

### Post by sktlsr7 on 2012-07-23
So I tried gksu nautilus and a window opened. I used that window to go to the "/media/Windows" drive than I looked in the .Trash-999 found my files. right click>copy paste on to a folder on the Ubuntu desktop and I get an error> Permission denied.

---

### Post by sktlsr7 on 2012-07-23
I should probably add that the only way for me to see the /media/Windows files is if I mount the drive in a non super user windows. The drive doesnt show in the super user window unless I mount before I start the SU session or mount from a non SU window.

---

### Post by sktlsr7 on 2012-07-23
So I learned how to mount the windows partition as a root user. I than did the gsu nautilus to open the explorer window to navigate to the drive. It still wont let me make changes to the partition. :(

---

