---
title: "ISP Configuration Help?"
date: 2006-03-05
forum: General Help
---

### Post by bonyicecream on 2006-03-05
Hi, I'm a bit of a linux newb. I had one machine running as a server for my webpage, but I took that down and just signed up for a server plan on some website for simplicity.  
Now I'm trying to turn that machine into an ISP, but I'm having a bit of trouble, being the noob that I am.  I am using the directions [here](http://www.howtoforge.com/perfect_setup_ubuntu_5.10), and I have finished the first two pages(the easy part, installation of the OS), and now I am stuck on the configure the network step.  I cannot figure out how to edit /etc/network/interfaces through the DOS-like setup(there is no visual desktop interface due to the setup).  When I type in "edit /etc/network/interfaces", I get the message 
"Warning: unknown mime-type for"/etc/network/interfaces" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

What I assume is the problem is that there is no default editor set for this file, but I don't know how to do anything about it.  
Any help would be greatly appreciated...

---

### Post by 4dz0 on 2006-03-05
try doing:

sudo gedit /etc/network/interfaces

---

### Post by bonyicecream on 2006-03-05
sudo: gedit: command not found

I got some help from a friend, and now i can view the contents of the file by typing "cat /etc/network/interfaces"
but when I do that, it comes up different from the one on the directions site, starting from:
#The primary network interface

mine says: iface eth0 inet dhcp

the one on that site says:
iface eth0 inet static        
address 192.168.0.100        
netmask 255.255.255.0        
network 192.168.0.0        
broadcast 192.168.0.255        
gateway 192.168.0.1

and the hardware is connected properly to the network
now I don't know what to do next :S

---

### Post by 4dz0 on 2006-03-05
The article is different because they have changed /etc/network/interfaces to configure their primary network interface to use a static IP address. You'll need to configure your network interface to do the same if you want your router to be able to find your server.

You'll need to make some changes to the file - use the details in the articles /etc/network/interfaces configuration as a basis for your own.

If you would like to install gedit to make editing the file easier execute the following command:

sudo apt-get install gedit

---

### Post by bonyicecream on 2006-03-05
ok so i did that, and near the end of the installation it said "W: Couldn't stat source package list [http://us,archive.ubuntu.com](http://us,archive.ubuntu.com) breezy/main Packages (var/lib/apts/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_packages - stat (2 no such file or directory) and did stuff liek that 6 times, then it syas to run apt-get update to correct the problems, then it does the W: thing again and says i should run apt-get update to correct these problems...

and when i do "sudo gedit /etc/network/interfaces", it says 
"(gedit:7905): Gtk-WARNING **: cannot open display: "

---

