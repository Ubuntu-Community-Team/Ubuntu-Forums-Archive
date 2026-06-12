---
title: "ubuntu 10.04 internet woes"
date: 2010-07-15
forum: General Help
---

### Post by paranj on 2010-07-15
Okay I just installed 10.04. Let me tell you people that I am a Linux noob. I have had a bit of experience with previous distros but I am pretty much a newbie. So I setup 10.04 but I can't get my net to connect. It's working fine on Win7 (posting from it). It's a dsl connection. I use an ethernet wire to connect to the net.

I opened terminal and used the 'sudo pppoeconf' command and followed the instructions. This is how I used to get my net working on previous distros but it dosen't seem to work in 10.04. The terminal says that my connection is active but it isn't. The network manager icon isn't visible on the top panel.

I really want my net working. Any solutions ?

---

### Post by silencej on 2010-07-15
I don't know about PPPoe. But if you are urgent to get a solution, i would recommend wicd for you:
```
sudo apt-get install wicd
```

It's a wonderful tool better than the default one i think.

---

### Post by paranj on 2010-07-15
Can we use the apt-get install command when we are offline ?

---

### Post by Deadite81 on 2010-07-15
No you can't do apt-get offline.  You can go [here]("http://packages.ubuntu.com/search?keywords=wicd&searchon=names&suite=lucid&section=all") in Windows to download the .debs, put them on a thumbdrive, shared FAT partition or whatever, then install them in Ubuntu.

Wicd may be a viable solution, but if you're using ethernet you may want to try using "eth0" instead.  

Try running
```

nm-applet
```
in the terminal and see if it pops up in the panel.  If it does, right-click it and choose "Edit Connections".  Then connect to "auto eth0".  This may solve your problem.

---

### Post by Deadite81 on 2010-07-15
I should mention that your connection matters.  If you are hooked directly to the modem eth0 may not work.  It sounds as if you may be, but if you're hooked through a router you need to use eth0 rather than PPPoe.

---

### Post by paranj on 2010-07-15
First of all thanks to you all people... will try out the solutions in a couple of hours.

Secondly, my ethernet wire is directly plugged into a modem and not a router.

---

### Post by paranj on 2010-07-15
EDIT ---

I tried the nm-applet command but it says that one instance of nm-applet is already running but I can't see it in the panel!

---

### Post by paranj on 2010-07-15
installed wicd... 

Now when I used to open Firefox before I installed wicd, it used to straight away gimme a 'server not found' screen and after installing and running wicd, Firefox just keeps loading the page but nothing happens and it just stays blank. Same with all other internet apps. No packets are transferred, nothing happens.

---

### Post by paranj on 2010-07-15
BUMP

Anyone ? Or do I just re-install it ?

---

### Post by dineshs on 2010-07-15
I havent tried wicd.I think the following will work
```
sudo gedit /etc/network/interfaces
```
The file should contain only this
```
auto lo
iface lo inet loopback
```
Note :You may backup the file before editing for safety
Now restart the machine.If NM icon has reappeared, configure the connection via the DSL tab in NM as follows
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the DSL tab- click add - Enter username and password-tick available to all users-apply(connection name =DSL connection by def)

To connect DSL click on NM icon click `DSL connection'
Do not attempt pppoeconf command further

---

### Post by paranj on 2010-07-16
Hey thanks a lot! Lemme boot into Ubuntu and try :).

---

### Post by paranj on 2010-07-16
It didn't work but nevermind. I just installed Ubuntu 9.10 and everything's fine. Posting from it :)

---

### Post by tumelo on 2010-10-22
I have this same problem. I just upgraded to 10.04 from 9.10 and my wirless symbol disapeared from the panel. I can't connect to the internet and when I type nm-applet in the terminal is say:
 
The program 'nm-applet' can be found in the following packages:
     * network-manager-gnome
     * mythbuntu-diskless-client
Try: apt-get install <selected package>
 
but of course I don't have a connect to do apt-get. 
I have tried several solutions that i have found from the internet and none have worked. 
I downloaded the deb file(not sure if it was the right one. there were a lot) to a flashdrive and tried to download it on my ubuntu computer and it told me to check my connection like I need the internet.
Maybe I didn't do some thing right with the deb file

---

### Post by tumelo on 2010-10-22
> **paranj said:**
> It didn't work but nevermind. I just installed Ubuntu 9.10 and everything's fine. Posting from it :)
 
How did you go back to 9.10? cause I lost my cd. is there way to install 9.10 without the cd?

---

