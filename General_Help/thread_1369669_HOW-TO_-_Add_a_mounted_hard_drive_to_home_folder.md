---
title: "HOW-TO - Add a mounted hard drive to home folder"
date: 2010-01-01
forum: General Help
---

### Post by Mad Ed on 2010-01-01
Hi all,

I am a new user and have installed Ubuntu 9.10 just now. Everything fine so far, but all my hard drives except the boot drive are accessible only after mounting manually. Okay i could live with that, but I try to add a folder on one hard drive to firefly in order to use it for Itunes on my Mac, but I cannot find the folder or the drive as such.

Further, I set up Netatalk to use my Ubuntu as a file server. Works great, but again I can only see the home folder on my Mac. I seem to make something wrong with the setup of the drives?! 

I already fromatted one drive into Ubuntu's ext4 and hoped that that would solve the issue, but it is the same as before when it was a NTFS drive system.

Can anybody help me?!

Thanks

Ed

---

### Post by SuperSonic4 on 2010-01-01
I suggest you add the drives to fstab to get them to mount on boot or whenever the following command is given ```
sudo mount -a
```

Something like
```
mkdir ~/Mac
```
```
/dev/sdb1 /home/ed/Mac ext4 defaults,user 0 0
```

---

### Post by Mad Ed on 2010-01-01
Hi Supersonic,

thanks for the answer. I got a permission denied after the last step. What does the line mean? 

My device is sdc1, that I changed in your line. 

/home/ed/Mac I guess I have to exchange ed with my user name, right?

The rest I kept as per your line and did not change anything.

What could be the problem?

Thanks for help...

---

### Post by Vishnu V on 2010-01-01
The last one is not a command add that code to the fstab file(by sudo gedit /etc/fstab)
Save it and reboot

---

### Post by SuperSonic4 on 2010-01-02
> **Mad Ed said:**
> Hi Supersonic,

thanks for the answer. I got a permission denied after the last step. What does the line mean? 

You have to paste the last time into /etc/fstab (which must be opened as root) ```
gksu gedit /etc/fstab
```

> 
My device is sdc1, that I changed in your line. 

Good move

> /home/ed/Mac I guess I have to exchange ed with my user name, right?

Yes - you cannot use ~ as fstab is read by root and the system would mount it at /root/Mac
Of course you can change the folder name too - Mac is just an example

---

### Post by Mad Ed on 2010-01-03
Tried that, but got following error message:

(gedit:3501): Gtk-WARNING **: cannot open display: 

Any idea?
Thanks

---

