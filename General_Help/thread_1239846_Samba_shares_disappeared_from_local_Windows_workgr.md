---
title: "Samba shares disappeared from local Windows workgroup"
date: 2009-08-14
forum: General Help
---

### Post by muranternet on 2009-08-14
Running a Mythbuntu 9.04 server, all shares worked perfectly up to yesterday.  Now none of the shares are visible from any XP or Vista boxes on the network (Vista doesn't really matter, I just had one lying around and tried it).  Restarting Samba does not help, uninstalling and reinstalling Samba does not help.  None of my smb.conf or fstab files have changes.  I'm fairly clueless about troubleshooting this, so anyone run into this or hanve any suggestions where to start?

I read in another thread that Wine was a culprit, but Wine has never been installed on this server and I confirmed it was not on it.  Also note that the box itself has normal connectivity and all other boxes on the network can shell into the box and Mythweb is available on the LAN, so the connection exists.

---

### Post by swerdna on 2009-08-14
Check that Samba is still running with ```
sudo /etc/init.d/samba status
```Then try turning off the UFW firewall, just to test if it's a culprit:```
sudo ufw disable
``` and ```
sudo ufw enable
```Then check the workgroup name and netbios names are correct with ```
testparm -s -v | egrep "workgroup|netbios name"
```

That's a start

---

### Post by muranternet on 2009-08-14
```
etc/samba$ sudo /etc/init.d/samba status
 * nmbd is running
 * smbd is running
```

ufw disable had no effect
 
```
/etc/samba$ testparm -s -v | egrep "workgroup|netbios name"
Load smb config files from /etc/samba/smb.conf
Processing section "[recordings]"
Processing section "[videos]"
Processing section "[music]"
Processing section "[pictures]"
Processing section "[videos2]"
Loaded services file OK.
Server role: ROLE_STANDALONE
        workgroup = BUNNY
        netbios name = MYTHBOX2

```
All correct.
 
Did another reinstall of samba from synaptic, no effect.

---

### Post by swerdna on 2009-08-14
Check if the Ubuntu server can see itself using Samba. What is returned when you run this:```
smbtree -N
```

---

### Post by muranternet on 2009-08-14
Update:  came home and the box had crashed (heat I think, someone had moved the keyboard over a vent and it's hot).  After a reboot, I couldn't see it at all on the network, it could ping out but could not see the HDHomerun tuner.  Seemed fishy so I turned off UFW again and rebooted, and magically everything was working.  I find this very strange, but I guess ufw could have been updated automatically (I only have security updates enabled).  I'd like to turn it back on as my next project is to open the box via SSH for remote use of Mythweb, but for now it's working.  I'll investigate what may have changed with ufw.

---

### Post by swerdna on 2009-08-14
There's a method for letting Samba through UFW here: [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubusambaserver.html#firewall")

And it should work just as well for ssh, just add the ssh port: TCP 22 with```
sudo ufw allow proto tcp to any port 22 from x.y.z.a/24
```

---

### Post by muranternet on 2009-08-18
Spoke too soon.  Disappeared again, and rebooting the server with ufw turned off did not work (which is what I thought fixed it the first time).  smbtree -N returns nothing.  /etc/init.d/samba status show that nmdb and smbd are running.  So it looks like my samba installation may be corrupted?

Update:  From XP I can browse the machine by manually entering the address in an explorer address bar, but the share still does not appear when I try to look at workgroup computers (from XP).  Strange, but minimally usable.

---

### Post by swerdna on 2009-08-18
If running it with ufw off doesn't work: are there any firewalls on windows? Turn them off. Are there any other firewalls on Ubuntu, like firestarter?

---

