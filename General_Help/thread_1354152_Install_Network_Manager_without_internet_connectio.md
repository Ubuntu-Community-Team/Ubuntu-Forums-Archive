---
title: "Install Network Manager without internet connection"
date: 2009-12-13
forum: General Help
---

### Post by supmah5 on 2009-12-13
I wanted to switch back from WICD Network Manager to the original Network Manager. I was prompted to uninstall WICD first, but now I have no internet connection and thus can't install Network Manager. 

I'm running Eeebuntu on my mini EeePC with no CD-player. 

Hope someone can help me get my connection back..!

---

### Post by RedSingularity on 2009-12-13
Well you can get the network manager .deb from a computer that has internet and save it to a flash drive.

PS:  Do you have ubuntu installed on the flash drive?

---

### Post by supmah5 on 2009-12-13
Ok. I'm a bit new to Linux...where can i get the network manager .deb file from? 
Found this page: [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/)
But which file is it that I'm looking for? 

Ps. Don't have it installed on a flash drive.

---

### Post by RedSingularity on 2009-12-13
Ok what version of Ubuntu are you running?

---

### Post by supmah5 on 2009-12-13
Hm..where do i check that?

---

### Post by supmah5 on 2009-12-13
Eeebuntu
Release 3.0 (eb3)
Kernel Linux 2.6.29-1-netbook
Gnome 2.26.1

---

### Post by RedSingularity on 2009-12-13
Can you uninstall wicd?

sudo apt-get remove wicd

---

### Post by supmah5 on 2009-12-13
Nope...get a message that it's not installed.

---

### Post by RedSingularity on 2009-12-13
Ok then it probably is not........[here]("http://packages.ubuntu.com/karmic/net/network-manager") is the package you want.  Save it to a flash drive or something.  

After you put that on put [this]("http://packages.ubuntu.com/karmic/net/network-manager-gnome") on.

Reboot

---

### Post by supmah5 on 2009-12-13
Get this error message trying to install the first file: Dependency is not satisfieable: libgnome-bluetooth7(>=2.27. 8)

---

### Post by RedSingularity on 2009-12-13
This is what we call "Dependency Hell".  You have to manually track down all the necessary dependencies and install them as well.  It MORE trouble than its worth BELIEVE ME!  Cant you track down a wired connection to use temporarily?  If you could get a wired connection we could install the network manager right away.

---

### Post by supmah5 on 2009-12-14
Tried that too, but the system doesn't even recognize that I plug in the internet cable. :( Oh...why did i uninstall wicd, this is really a hell! Is it easier to reinstall wicd in some way?

---

### Post by ushills on 2009-12-14
You can set up your network from the command line without network manager.

If you can connect with a wired connection it is easier but you can also do wifi.

You need to create or amend the file ```
/etc/network/interfaces
```

for wired put in the line 

```
auto eth0
iface eth0 inet dhcp
```

then connect ethernet cable and run

```
sudo /etc/init.d/networking restart
```

You should now have a wired connection working, if not then you need to add a dns server with

```
sudo nano /etc/resolv.conf
```

add, opendns server addresses for ease.

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

then

```
sudo /etc/init.d/networking restart
```

again

---

### Post by supmah5 on 2009-12-15
Would be great if that worked... But when i put in the following code i get Permission denied:

 	Code:
 	/etc/network/interfaces

---

### Post by 3rdalbum on 2009-12-15
> **supmah5 said:**
> Would be great if that worked... But when i put in the following code i get Permission denied:

 	Code:
 	/etc/network/interfaces

No; /etc/network/interfaces is a file that you edit, not a command. Try this:

```
gksudo gedit /etc/network/interfaces
```

and make the edits as described.

---

### Post by supmah5 on 2009-12-16
Wow it works!! Many thanks, you got me out of a nasty, sticky situation :)

---

### Post by llawwehttam on 2009-12-16
Right guys, just for people who are new to ubuntu you cannot edit files in /etc or similar as a normal user. These are the equivalent of windows system files. To edit them in the command line type 'sudo' before the command to run it as root ( the windows equivalent of administrator) or 'gksu' to run it in graphical mode.

I'm sure this is all explained in the documentation.

---

### Post by nostra16 on 2010-01-03
I've been looking for more than an hour and tried many many things before landing here.

Many thanks to llawwehttam! It worked perfectly, I now have Network Manager installed and running. Such a nice feeling!

Thank you, and many thanks to the countless Ubuntu Members for the help and support I always find!

---

### Post by ilikedginger on 2010-02-11
> **nostra16 said:**
> I've been looking for more than an hour and tried many many things before landing here.

Many thanks to llawwehttam! It worked perfectly, I now have Network Manager installed and running. Such a nice feeling!

Thank you, and many thanks to the countless Ubuntu Members for the help and support I always find!

I just wanted to say thank you as well. I looked all over for a solution to the problem and this was the quickest, most straight forward post I've found regarding the topic. Fixed me right up!:KS

---

### Post by mpc755 on 2010-09-02
> **ushills said:**
> You can set up your network from the command line without network manager.

If you can connect with a wired connection it is easier but you can also do wifi.

You need to create or amend the file ```
/etc/network/interfaces
```for wired put in the line 

```
auto eth0
iface eth0 inet dhcp
```then connect ethernet cable and run

```
sudo /etc/init.d/networking restart
```You should now have a wired connection working, if not then you need to add a dns server with

```
sudo nano /etc/resolv.conf
```add, opendns server addresses for ease.

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```then

```
sudo /etc/init.d/networking restart
```again

Worked great. Thanks.

---

### Post by unit145 on 2011-05-23
Although this is marked as [SOLVED], I am still replying in case someone googled this thread (like I did) is search for a different solution, because others have not worked. 

I managed to reinstall Network Manager in Ubuntu without internet (after having stupidly uninstalled it through the package manager). I downloaded (using another OS with a working connection) the following four files from the official [package repository]("http://packages.ubuntu.com/lucid/net/")

network-manager_0.8-0ubuntu3_i386.deb           
network-manager-gnome_0.8-0ubuntu3_i386.deb     
network-manager-pptp_0.8-0ubuntu3_i386.deb      
network-manager-pptp-gnome_0.8-0ubuntu3_i386.deb

Then I put then into /var/cache/apt/archives/ of my Ubuntu and ran the command 

sudo dpkg -i /var/cache/apt/archives/network-manager*.deb

Ater rebooting the NM was back to normal.
Hope this helps someone.

---

