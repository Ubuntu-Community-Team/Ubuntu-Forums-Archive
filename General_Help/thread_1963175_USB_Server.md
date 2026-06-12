---
title: "USB Server"
date: 2012-04-22
forum: General Help
---

### Post by Vinger on 2012-04-22
Hello,

I have a small usb server to share an external harddisk on the network.
This works fine in a normal windows environment. The harddisk is coupled as an USB device via a small program.

I want to couple the harddisk now to my Kubuntu 11.10 installation and to a windows7 installation in Virtualbox. Both do not work. 
The win7 in Virtualbox does use the program, the program does couple the harddisk but i don't see any new usb device.
The Kubuntu install, i don't even know how to begin. 

Does anybode has some help for me?
Already thanks!

gr.

---

### Post by mastablasta on 2012-04-22
usb server? what kind of operating system does the server have?

you could sue samba to connect to it if the server is on windows... 

i think a package in KDE could be missing again called kde network or soemthing liek that. try installing it to see if it works. disk should show up in dolphin.

---

### Post by Vinger on 2012-04-22
I don't know what os the server has...
It is a little box that connects USB on an IP network. 

I'll try Samba...

gr.

---

### Post by ki4jgt on 2012-04-22
If you don't mind everyone on the network having access to it, I'd just use the python http server module. You just type it into the command line (within the folder you want shared) and it hosts the files via the IP address of the computer on the network. So if you were hosting a folder called share in your home folder, you would just cd share, start python, and then issue the server command.

---

