---
title: "How can you remove a dock from ubuntu 10.4??? PLease HELP!"
date: 2010-08-14
forum: General Help
---

### Post by nakamuraxxx on 2010-08-14
ok im new to this and i accidentally clicked on Cairo-dock and another just popped up behind and i want to remove it so i can only have one. im using ubuntu 10.4 and I see 2 docks. PLEASE can anyone help me out. :confused: i would really appreciate it.

---

### Post by Sef on 2010-08-15
Can you right click on the one you want to delete and delete it?

---

### Post by Sudo noob on 2010-08-15
Hi guys im new to the Ubuntu community and I am having some trouble to getting everything set up. Im trying to install DOCKY and this is the error I keep getting. 

If anyone can help me that would be great. 

chris@chris-desktop:~$ sudo apt-get install docky
E: Type 'in' is not known on line 2 in source list /etc/apt/sources.list.d/docky-core-ppa-lucid.list
E: The list of sources could not be read.

I also and having issues trying to find my home network, ( wireless )  but when i hardwire it its fine.

---

### Post by Smart Viking on 2010-08-15
> **Sudo noob said:**
> Hi guys im new to the Ubuntu community and I am having some trouble to getting everything set up. Im trying to install DOCKY and this is the error I keep getting. 

If anyone can help me that would be great. 

chris@chris-desktop:~$ sudo apt-get install docky
E: Type 'in' is not known on line 2 in source list /etc/apt/sources.list.d/docky-core-ppa-lucid.list
E: The list of sources could not be read.

I also and having issues trying to find my home network, ( wireless )  but when i hardwire it its fine.

That file is not present in my installation of ubuntu, but docky is still available in the repos, so i assume it is safe to remove it.

```
sudo rm /etc/apt/sources.list.d/docky-core-ppa-lucid.list
```then try again:
```
sudo apt-get install docky
```

EDIT: It is only in the 10.04 repos, not earlier versions. It would be nice to know what version of ubuntu you are using: [http://wiki.go-docky.com/index.php?title=Installing](http://wiki.go-docky.com/index.php?title=Installing)

---

### Post by Sudo noob on 2010-08-15
Ok so i did what you said .... and this is the error that I am getting now. I have the ISO disk that I DL'd from Ubuntus website. 

chris@chris-desktop:~$ sudo rm /etc/apt/sources.list.d/docky-core-ppa-lucid.list[sudo] password for chris: 
chris@chris-desktop:~$ sudo apt-get install docky
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Smart Viking on 2010-08-15
> **Sudo noob said:**
> Ok so i did what you said .... and this is the error that I am getting now. I have the ISO disk that I DL'd from Ubuntus website. 

chris@chris-desktop:~$ sudo rm /etc/apt/sources.list.d/docky-core-ppa-lucid.list[sudo] password for chris: 
chris@chris-desktop:~$ sudo apt-get install docky
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

That means some other process is using it. Are you installing updates, or installing something else? If so, you must wait until it is finished. :)

---

### Post by Sudo noob on 2010-08-15
Im using the 10.4 LTS edition

---

### Post by Sudo noob on 2010-08-15
Im not installing anything else that im aware of. I just installed UBUNTU and restarted it and tried the sudo apt-get install docky command and recieved that error

---

### Post by Smart Viking on 2010-08-15
> **Sudo noob said:**
> Im not installing anything else that im aware of. I just installed UBUNTU and restarted it and tried the sudo apt-get install docky command and recieved that error

First do this:

```
sudo apt-get update
```
then try again
```
sudo apt-get install docky
```

If that doesn't work, restart your machine and try again. That will most likely solve the problem you are having. :)

---

### Post by Sudo noob on 2010-08-15
ok so  now i have an error message on the top of my screen that is a red circle with a white line that says " this usually means that your installed packages have unmet dependencies

---

### Post by Sudo noob on 2010-08-15
I have tried to restart my machine a few times and still get that message. this is the new message i get from the code u gave me 

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Smart Viking on 2010-08-15
Interresting. Have you tried updating the system? If not, update your system and try again.

---

### Post by Sudo noob on 2010-08-15
okso it started to unpack the file so i will try will it be in my system pane? and and how do i make it 3D to look more like the mac dock?

---

### Post by Sudo noob on 2010-08-15
ok i got it working ........ ty for ur help and now im curious any ideas on the whole why i cant find my wireless network?

---

### Post by sikander3786 on 2010-08-15
> **nakamuraxxx said:**
> ok im new to this and i accidentally clicked on Cairo-dock and another just popped up behind and i want to remove it so i can only have one. im using ubuntu 10.4 and I see 2 docks. PLEASE can anyone help me out. :confused: i would really appreciate it.

Select one of the docks for automatic startup via Right Click >>> Cairo Dock >>> Start automatically on start up and then Right Click >>> Exit both of them. Then reboot. You'll have only one dock left.

Regards.

---

### Post by sikander3786 on 2010-08-15
Glad you got it working. Start a new thread for wireless.

---

