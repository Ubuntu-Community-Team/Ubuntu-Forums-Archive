---
title: "Using FTP or Telnet to transfer files"
date: 2010-07-30
forum: General Help
---

### Post by weasker on 2010-07-30
Hey guys i'm new to ubuntu but i have taken a basic networking class that involved both XP and fedora. I was recommended to use ubuntu though because it's easier to use :) anyways i have a world of warcraft folder on a windows vista running computer and was wondering how i could use either telnet or FTP to get that ~20GB folder over to my linux desktop. Can anyone help me out please? I installed 10.04 and have installed WINE (which i'm still trying to figure out how to work).

---

### Post by Raymond2201 on 2010-07-30
Hey weasker,

Just remove the hard drive from the Windows machine and chuck it in your Ubuntu box as a slave drive, this should auto mount the hard drive and give you access to your files from the Ubuntu install. you can simply copy the wow folder there.

:)

Using networking to copy 20gig is torture, have done it many times and it is just easier to swap the drives about.


failing that just set samba up on your Ubuntu install and that will allow you to copy files between your 2 OS's.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by prodigy_ on 2010-07-30
You could enable ssh server on your Ubuntu box: ```
sudo apt-get install ssh
``` and then use a compatible client like [FileZilla](http://filezilla-project.org/) to connect to it using SFTP protocol. Of course there are many other methods, but this has always been the fastest and the easiest for me.

---

### Post by weasker on 2010-07-30
thank you guys so much for the quick help! I won't be able to do the hard drive swap because the vista is a laptop (under warranty still :() and Ubuntu is a desktop but i will try that samba and filezilla when i get home from work.

---

### Post by Raymond2201 on 2010-07-30
ah then the quick and dirty method aint going to work :)

Just get yourself a good book whilst the wow folder is copying either using samba or ssh server hehe

---

