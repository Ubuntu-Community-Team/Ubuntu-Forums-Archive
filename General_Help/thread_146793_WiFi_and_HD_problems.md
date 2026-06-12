---
title: "WiFi and HD problems"
date: 2006-03-19
forum: General Help
---

### Post by discus rapidus on 2006-03-19
I have a couple of problems that I hope some of you can help me out with...

I have an HP laptop and I tried installing the ndiswrapper with the Windows bcmwl5 drivers.  When I type ndiswrapper -l, ubuntu does show that the bcmwl5 is installed and the hardware is present.  However if I type iwconfig, there is no wlan0 and nothing has extensive information.

"root@ubuntu:/etc/ndiswrapper/bcmwl5# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
"

I have no idea what sit0 is?   Where do I go from here... all the wiki stuff I've read says that I should be able to configure the wireless card in the network panel.  There is nothing to configure there (no wlan0).
WHAT DO I DO? :( :(  I know I am using the correct drivers - I have used these drivers to get the wireless card working in SuSE - but for some odd reason it won't work in Ubuntu :(.  

Also... I have an external hard drive that is formatted with NTFS and I have a second NTFS partition (the windows partition) on the main internal hard drive.  I also have a third FAT32 partition for Data in my internal hard drive.  The two NTFS partitions I can't even read when I'm logged in as a regular user (I am admin).  It seems the only way I can read the NTFS partitions is to log in as root in the terminal.  Is there any way I can allow my regular user (admin, but not root) to read from these two drives?  The regular user can read the FAT32 drive.  I'm not sure if the problem is connected to NTFS vs FAT32... it was just a pattern I noticed.

Thanks in advance, Your help is much appreciated

Discus Rapidus, a future linux user.

---

### Post by mwaddoups on 2006-03-19
Have you tried modprobe?
```

sudo modprobe ndiswrapper
iwconfig #if wlan0 shows up, continue. If not, post.
sudo iwconfig wlan0 essid *<essid name>* key *<WEP key (if used)>*
dhclient wlan0 #if dhcp is used

```
To run it at bootup, go to System >> Administration >> Networking  and then configure wlan0 correctly. Then it should run at startup.

---

