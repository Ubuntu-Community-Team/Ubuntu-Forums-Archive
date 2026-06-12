---
title: "Where do I begin?"
date: 2011-05-11
forum: General Help
---

### Post by MatthewCrow on 2011-05-11
My company won't pay for a new Windows Server so I am trying to see how hard it will be to setup and manage a Ubuntu Server. The trouble is I am a complete newb. I have an old Pentium D workstation with 2 gigs of ramm I am using as my test bed. 

I downloaded the .iso of Ubuntu Server 11.04 and burned it to a disc. 

I then booted to the disc and followed the installation instructions. 

I installed Samba file server and print server. The installation completed and the system ejected the disc and then rebooted. 

I have no idea where to go from here. The computer has brought me to a text based log in screen. I am looking for articles / books / tutorials on what I am to do next. I thank you in advance for your help.

---

### Post by WorMzy on 2011-05-11
Yes, the server doesn't come with a Desktop Environment; presumably because most servers are run headless (without a monitor), and the extra space a Desktop Environment takes up is completely wasted if you can't even use it.

You can install a Desktop Environment if you wish to; simply run
```
sudo apt-get install ubuntu-desktop
```
for the GNOME/Unity desktop. You can replace ubuntu-desktop with kubuntu-desktop for the KDE desktop, xubuntu-desktop for the Xfce desktop, or lubuntu-desktop for the LXDE desktop.

This [guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") may be of assistance to you if you decide to try to get by without a desktop; and you also may need it to set up networking (if you didn't configure it during the installation (you'll need to be connected to the internet to download the Desktop Environments, I don't think they're included on the installation CD.)

Alternatively, you could install the desktop version of Ubuntu. The desktop version comes with a Desktop Environment right out of the box.

---

### Post by dragonfly41 on 2011-05-11
To add to the above post ..

Rather than jumping into ubuntu server you can start by installing ubuntu desktop and then installing LAMP PHP + MySQL + Apache2.  This installs on port 80 but you can change port.  

[http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/](http://surferzworld.com/2010/10/installing-lamp-linux-apache-mysql-php-server-ubuntu/)

Or if you prefer Java apps you can install tomcat server.

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

Or for some applications have apache2 linked to tomcat6

Then you have to network to your clients.

---

### Post by Frogs Hair on 2011-05-11
Having no GUI has to be a bit of a shock when you're not used to it. here are a couple links that may help.

[http://www.filestube.com/t/the+official+ubuntu+server+book+pdf](http://www.filestube.com/t/the+official+ubuntu+server+book+pdf)

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by MatthewCrow on 2011-05-11
Thank you all for the help. I am not interested in using this machine as a web server or anything. It will purely be a file server and backup server. I wanted something with a little more ability than freeNAS. 

Can you please point me towards some tutorials or links on how to setup a RAID array in Ubuntu? As well as Samba help? 

Thanks!

---

