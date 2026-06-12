---
title: "accessing ubuntu through vmware in windows"
date: 2010-09-17
forum: General Help
---

### Post by kurusoo on 2010-09-17
I'm a windows 7 user and i intalled ubuntu recently using wubi executable installer, after some time i installed vmware player in windows. can anyone help me access my ubuntu in the vmware player in windows. all the articles i've read are about running a new installation in vmware player, but i already have ubuntu installed on my machine

---

### Post by Lateralis on 2010-09-17
Virtual machines are there so that you can run two operating systems for the price of one by virtualising one OS in a separate application.  As far as I know, there isn't a way of getting a virtual machine to run an OS which is already installed on a separate partition.  Much less get a VM to recognise a Wubi install.

---

### Post by kurusoo on 2010-09-17
Does that mean i'll have to run a new installation of ubuntu through the vmware player?

---

### Post by Lateralis on 2010-09-17
Yes.  If you want to run a virtual machine with Ubuntu/Linux whilst in Windows, then you will need to install a fresh version of Ubuntu into the virtual machine.

Alternatively, you can make use of Wine to run (some) Windows programmes within Ubuntu.  [WineHQ]("http://appdb.winehq.org/") has a database of Windows applications which run under Wine with user generated feedback on their experiences of these applications in Wine.

---

