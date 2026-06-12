---
title: "Avast Antivirus"
date: 2012-07-15
forum: General Help
---

### Post by BondFF on 2012-07-15
Hey guys,

I recently installed Avast on Ubuntu 12.04.  Upon registering and updating the virus definitions, I received an "Invalid Argument" error when I tried to load Avast.  

I found a forum on google that showed me the following command:
[B]sudo sysctl -w kernel.shmmax=128000000
kernel.shmmax = 128000000[/B]Well after I input the command, avast ran fine.  The problem is that when I restart the laptop it resets the values and I have to do it all over again.

I guess I'm suppose to edit the  '/etc/sysctl.conf' file, but I have no idea how to go about this.  

Thanks in advance!  I'm a Ubuntu noob and have already had one problem solved on this forum today.  :D

---

### Post by azmyth on 2012-07-15
sudo nano /etc/sysctl.conf

add the

kernel.shmmax = 128000000

to a line and make sure there isn't a # at the front of the line

Once you're done editing do a ctrl+x then say yes to save.

Please note, I haven't ever done this type of edit to this file as I'm just giving you the steps on how to edit.

---

### Post by BondFF on 2012-07-15
Thanks dude!  Worked like a charm.

---

### Post by ImConfused on 2012-09-19
This worked for me.  I also saw the original post but yours really worked well for me also.  Thanks ever so much.

---

