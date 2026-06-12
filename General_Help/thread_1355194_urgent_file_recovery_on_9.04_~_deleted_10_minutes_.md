---
title: "urgent file recovery on 9.04 ~ deleted 10 minutes ago from trash"
date: 2009-12-14
forum: General Help
---

### Post by DachaArh on 2009-12-14
Can anyone help please..
Using ubuntu 9.04, just 10 minutes ago one of my folders got deleted, and I did not know that, so I did empty trash can.. :(
It were my photoshop graphic works, over 10 great .psd files there, and over 200 .jpg, .png images, .... 
For one .psd file I had over 12 hours of work... :(

Can I recover that ?

please help....

---

### Post by DGortze380 on 2009-12-14
> **DachaArh said:**
> Can anyone help please..
Using ubuntu 9.04, just 10 minutes ago one of my folders got deleted, and I did not know that, so I did empty trash can.. :(
It were my photoshop graphic works, over 10 great .psd files there, and over 200 .jpg, .png images, .... 
For one .psd file I had over 12 hours of work... :(

Can I recover that ?

please help....

shutdown the machine immediately to avoid overwriting possibly recoverable data.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by DachaArh on 2009-12-14
thank you very much for your reply, I will try it now.. but I can't shutdown, because It is this machine.. and I don't have another computer, to put this hard disk in .. :(

so my only option is to try this application now...

---

### Post by DachaArh on 2009-12-14
sorry for double post.. don't know how to install this...

tar.bz archive, and no configure, make or other files of that fie.. lucky me ... :(

---

### Post by rbc on 2009-12-14
As long as this computer has internet access, boot up the Ubuntu Live CD, enable the universe reposistory, then open terminal and type:
sudo apt-get install testdisk

 Photorec, though, is going to want some other medium (hard drive, thumb drive) to write the recovered files to, since you don’t want to be overwriting files that you are trying to recover. Here’s one suggestion and then a caveat. Use the Advanced “tab”, to select only the file types you are interested in, so that you don’t have to sort through loads of “junk”, which brings me to the caveat. Photorec is a datacarving tool, so it is going to look for files, not folders (directories). 

To start the application, open terminal:

sudo photorec

Here’s a great tutorial from the omniscient Ubuntu guru, psychocats, if you need help, or post back
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Good luck

---

