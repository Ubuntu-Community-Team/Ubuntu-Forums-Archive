---
title: "Synaptic Package Manager Won't recognize password"
date: 2011-05-23
forum: General Help
---

### Post by scientist434 on 2011-05-23
I am running Ubuntu 11.04 i386 and I installed the unity desktop by using sudo apt-get install ubuntu-desktop. However when I try to open the synaptic package manager it won't recognize my password. It just keeps asking me for the administrator password. I can open update manager which also needs the admin password. This is a fresh install all I have done is installed the ubuntu desktop. I am currently trying to install KDE desktop to see if it works on there. I also have had this problem on my laptop which runs 11.04 x64 desktop edition. Does anyone else have this problem or is it just me? and is there a fix? also what is the terminal command to launch the packet manager?

Thanks

edit.
It started working on my laptop a week or so ago after I did updates. So I'm not sure if the server version of unity or the packet manager is just behind? I have run the update manager on my server and it says its uptodate.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Did you reset your password yet?

sudo passwd (username)

---

### Post by scientist434 on 2011-05-23
> **linuxinstalledfromhdd said:**
> Did you reset your password yet?

sudo passwd (username)

Just tried that still no luck.

---

### Post by linuxinstalledfromhdd on 2011-05-23
If you can't change your password, then maybe you aren't the administrator perhaps?

---

### Post by scientist434 on 2011-05-23
> **linuxinstalledfromhdd said:**
> If you can't change your password, then maybe you aren't the administrator perhaps?

I can change the password. It just doesn't recognize the password when I try and open the packet manager. It recognizes it in all other places I have tried to use it.

---

### Post by linuxinstalledfromhdd on 2011-05-23
sudo apt-get remove synaptic
sudo apt-get clean all
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install synaptic

---

### Post by scientist434 on 2011-05-23
> **linuxinstalledfromhdd said:**
> sudo apt-get remove synaptic
sudo apt-get clean all
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install synaptic

Ok I ran all of the above commands in order and it still doesn't accept my password. 

I did figure out that I can launch the packet manager by using the following command from terminal. 
sudo /usr/sbin/synaptic
I just enter my password in the terminal window and it opens, it only doesn't work if I enter the password in the popup that comes up when I try and load the synaptic packet manager from applications list.

Edit
Just logged out and switched to KDE packet manager works fine and recognized my password. I switched back to unity and still doesn't work so its a glitch in unity.

---

### Post by linuxinstalledfromhdd on 2011-05-23
I have seen this problem before, not quite sure the workaround to resolve it.

BUMP

---

### Post by sisco311 on 2011-05-23
Run:
```
gksu-properties
```
and set the *Authentication mode* to **sudo**.

---

### Post by notiones on 2011-05-26
I ran a minimal install of Ubuntu 11.04 and then added Lubuntu desktop via apt-get and afterwards I could not authenticate in Synaptic. This worked for me. Thanks

---

### Post by sisco311 on 2011-05-26
You are welcome!

---

### Post by Gaspereau on 2011-05-29
I had the same problem on xubuntu 11.04 and it works for me as well.
Thank you Sisco!!:KS

---

### Post by sisco311 on 2011-05-29
> **Gaspereau said:**
> I had the same problem on xubuntu 11.04 and it works for me as well.
Thank you Sisco!!:KS

Cool! :)

---

### Post by 5760 on 2012-05-17
> **sisco311 said:**
> Run:
```
gksu-properties
```
and set the *Authentication mode* to **sudo**.


I had the same problem and tried this fix and it worked great.  Thanks for the help!

---

### Post by oldos2er on 2012-05-17
Old thread closed.

---

