---
title: "Need to create backup install disc"
date: 2012-05-01
forum: General Help
---

### Post by rollin77 on 2012-05-01
I currently have Ubuntu 10.04 installed on a system, but I want to install VMware ESXi on this system and then re-install Ubuntu as a VM.  I'd rather not do a completely new Ubuntu install though, so if possible I'd like to backup my Ubuntu system so that it can be installed as a VM running on top of ESXi.

Is this possible?  Or would it be better to just do a fresh install as a VM?

I haven't used ESXi, and I'm not real great with Linux either so hopefully someone can help me out :)

---

### Post by Frogs Hair on 2012-05-01
This may be of interest . [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by Cheesemill on 2012-05-01
Do bear in mind that you need a Windows machine to administrate and create new VM's using ESXi.
 
Also you need a remote machine to access the desktop of the VM's, you can't use the ESXi host to view the desktop of running VM's.

---

