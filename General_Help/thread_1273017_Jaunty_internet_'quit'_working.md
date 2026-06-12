---
title: "Jaunty internet 'quit' working"
date: 2009-09-22
forum: General Help
---

### Post by DougieFresh4U on 2009-09-22
Ok, I am gonna try to get this solved I hope.
For some reason internet quit working on my Jaunty partition. This is a multi-boot system with Karmic 64 & 32 bit and Windows 7 as well as Jaunty. All my other partitions boot perfect whether I am using wireless or wired. When I am in Jaunty I edit the addresses but just doesn't seem to see any kind of connection. I do not really know what the terminal output I am posting is telling me. Please any other output you may need please provide the codes and I will boot into Jaunty and run the commands and reboot to Karmic and post
```
dougie@DougiesLeanMachine:~$ sudo /etc/init.d/networking restart
[sudo] password for dougie: 
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan1 ; Invalid argument.
 * if-up.d/mountnfs[wlan1]: waiting for interface pan0 before doing NFS mounts
                                                                         [ OK ]
dougie@DougiesLeanMachine:~$ 

```

---

### Post by DougieFresh4U on 2009-09-25
Anybody??

---

### Post by DougieFresh4U on 2009-09-27
I really miss using my Jaunty! :(

---

### Post by paradigm2 on 2009-09-27
When you say "edit the addresses" what exactly do you mean and what are you doing?  It seems that it worked before right?  So what configuration changes did you make, if any, prior to it messing up?

The message in question seems to have to do with setting the key.  One possibility is not having the proper permissions (sudo).

---

### Post by DougieFresh4U on 2009-09-27
> **paradigm2 said:**
> When you say "edit the addresses" what exactly do you mean and what are you doing?  It seems that it worked before right?  So what configuration changes did you make, if any, prior to it messing up?

The message in question seems to have to do with setting the key.  One possibility is not having the proper permissions (sudo).

My room mate has the router set to where I have to manually edit connections and I add all the correct , 192.168.2.xx then 255.255.255.0 then 192.168.2.1 ect. I then click apply but still not seeing any connection. I do think that I saw messege a while back that 'networking not enabled' 
Yes it worked before, then updates came along with reboot and nothing since. Internet works on my other 3 partitions.

---

### Post by paradigm2 on 2009-09-27
> **DougieFresh4U said:**
> My room mate has the router set to where I have to manually edit connections and I add all the correct , 192.168.2.xx then 255.255.255.0 then 192.168.2.1 ect. I then click apply but still not seeing any connection. I do think that I saw messege a while back that 'networking not enabled' 
Yes it worked before, then updates came along with reboot and nothing since. Internet works on my other 3 partitions.

Where are you editing this information?  Clicking where or typing what commands?

It seems highly probable that a file got messed up in the edit.

---

### Post by DougieFresh4U on 2009-09-27
> **paradigm2 said:**
> Where are you editing this information?  Clicking where or typing what commands?

It seems highly probable that a file got messed up in the edit.

Edit Connections, this is the one in my Karmic, which is exactly the same in Jaunty

---

### Post by DougieFresh4U on 2009-09-28
Never mind, guess this is a dead issue. Gonna save partition for the next testing version after Karmic. As I have always jumped on board from the very beginning.
Begone with Jaunty!!!

---

