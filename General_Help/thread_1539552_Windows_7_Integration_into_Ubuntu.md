---
title: "Windows 7 Integration into Ubuntu"
date: 2010-07-26
forum: General Help
---

### Post by inulled on 2010-07-26
Hi all,

Does anybody know how to take a windows 7 install and intergrate it into linux. i like that wine integrates into the windows manager. but of course wine simply doesn't do what i want. i love linux because of complete customization. i like windows 7 because it runs the programs i use on a daily basis properly. i know there has to be some way this can be done. im getting tired of using windows 7 inside a virtual machine for varius reasons. i know there has to be someway i can combine linux and windows normally. any help?

thanks in advance
 - michael

---

### Post by wilee-nilee on 2010-07-26
If you figure it out let us know. You have several options you know of, either OS, as a host or guest in a virtual environment. A real dual boot separate OS on separate partitions, or Ubuntu inside of Windows as wubi.

---

### Post by jerenept on 2010-07-26
Well, if you install Virtualbox Guest Additions, you can run Win7, and when it has booted up, select "Seamless Mode" in the File menu.

That's about the best I can offer, other than WINE.

---

### Post by inulled on 2010-07-26
what i think im gonna do is create a live FAT partition table and install windows 7 on it. use it as a second primary table and resize the partition to the exact size of the installed windows environment. then i will lock the table for read only under the linux environment. this way windows 7 will be permanently stored on the hdd and can then be manipulated with a peace of mind. next figure out how to work windows into gnome. im sure there are api's and/or kernels available which provide a means of communicating with the windows environment. all i need is a way to communicate with windows. then i can write a few python scripts for Nautilus and gnome which can grab the data i need from 7 and bam im done. i dont know how wine goes about doing this. but im sure its similar to my schema. if i can get this working, there are allot of things i can build for my advantage.

---

### Post by inulled on 2010-07-26
id like to be able to build a system that i have complete control over. windows is great in all, but you cant do anything to the source code. ive got programs that i need windows to run. but i like linux because of its customization. if i can get this going, ill be able to customize windows to do what i want it to do. id love to be able to store programs i install through the windows 7 partition into virtual hdd. id need to place a customized database on each vhd i make to store the data used by the programs installed on that vhd. remember that the partition is locked as read only. the custom db will hold all the windows data and have the windows 7 system use the vhd's db for read/write modes. this way i can have a secure and stable way to work with windows. i hate having to reinstall windows every month. hopefully this will end that problem. good idea huh ? i think so too. :D

---

### Post by jerenept on 2010-07-26
If you wanted an open source version of Windows, why didn't you ask? 
[http://www.reactos.org/]("http://www.reactos.org/")

It is a bit behind Microsoft, but is an interesting OS nonetheless.

---

### Post by MaxIBoy on 2010-07-26
Well, if you have an installer disk for Windows 7, you can install it in VirtualBox. 
[http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/](http://www.intowindows.com/how-to-install-windows-7-on-virtualbox/)

There are two versions of VirtualBox. The VirtualBox Open Source Edition is missing USB support and some other stuff (so your virtualized Windows won't be able to see flash drives if you plug them in,) but if you feel it's important to use open source software when possible, then choose that one. (But if you feel that way, why do you want Windows? :p)

---

