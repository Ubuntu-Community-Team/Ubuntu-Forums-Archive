---
title: "Palm IIIc howto connect"
date: 2010-02-07
forum: General Help
---

### Post by rapattack1 on 2010-02-07
Hi I only just got this old palm that connects via a serial cable. I went to connect it with gnome-pilot but got the error seen in the attachment. I don't know where the permissions are on the device so can anyone tell me how to find that?

---

### Post by gmargo on 2010-02-07
Your best bet is to change **/dev/pilot** to **/dev/ttyS0** (or 1,2,3).  There are probably 4 serial port devices defined: **/dev/ttyS0**, **/dev/ttyS1**, **/dev/ttyS2**, and **/dev/ttyS3**.  Try each of those devices, since we're not sure which serial port it's plugged into.  If the permissions are ok, then hit the button on the cradle to try to start the transfer.  Try each of the ttyS[0123] devices until you find the right one.

If permissions are still a problem, open a terminal and check the permissions on the devices as well as your own group memberships.

```

$ ls -l /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 Feb  7 01:38 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 Feb  7 01:38 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 Feb  7 01:38 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 Feb  7 01:38 /dev/ttyS3
$ id
uid=1000(gmargo) gid=1000(gmargo) groups=4(adm),20(**dialout**),24(cdrom),46(plugdev),107(lpadmin),115(admin),120(sambashare),1000(gmargo)

```Here you can see that the ttyS* devices are not writable to all, so you have to be a member of the "dialout" group in order to use them.

If you need even more debugging, you can install the **pilot-link** package to get all the command-line tools.

---

### Post by rapattack1 on 2010-02-07
Hmmmm well ttyS0 seems to be the go even though the damn thing is not turning on today. There is no light and nothing is on the screen. Despite this I was able to press syn and get it working with the app.
I might just do a reboot and see what happens.

---

### Post by rapattack1 on 2010-02-07
Seems like there is a power connection problem that i have to look closer at when i have time. The cable that plugs into the serial plug is unstable. Might have to clean the connector itself. Not sure....will report back later for further info....thanks!!!!

---

### Post by rapattack1 on 2010-05-29
I have given this away to someone. Too time consuming and i ended up scoring a really well working PalmOne Tungsten T5. Haven't tried to sync it but it mounts as a flash drive so i am happy with that right now. In the future i would like it to back up the calender and contacts

---

### Post by celem on 2010-06-04
In shell do ls -l >a
then press sync on the Palm
then, in shell enter ls -l >b
then enter diff a b

Whatever port your Palm is creating will be disclosed. If you see nothing, you probably need to load the visor module with:
sudo modprobe visor

The Palm will probably create /dev/ttyUSB0 or /dev/ttyUSB1. This the port that you will need to select.

If the visor module works for you, make the choice permanent with:

sudo gkedit /etc/modules

add visor to the end of the list, save.

By the way, more modern Palms are available very cheap on eBay. I use the very nice Sony PEG-SJ22/U ($20 on eBay). Syncs perfectly with Ubuntu gpilot, kpilot or jpilot.

---

### Post by rapattack1 on 2010-06-05
I got this
```
carla@carla-desktop:~$ ls -l >a
carla@carla-desktop:~$ ls -l >b
carla@carla-desktop:~$ diff a b
2c2
< -rw-r--r--  1 carla carla       0 2010-06-05 14:54 a
---
> -rw-r--r--  1 carla carla    4435 2010-06-05 14:54 a
9c9
< -rw-r--r--  1 carla carla    4435 2010-06-05 14:52 b
---
> -rw-r--r--  1 carla carla       0 2010-06-05 14:55 b

carla@carla-desktop:~$ 

```
Not sure what this means.
I made two attempts.

I had a Sony PEG N70 i think a year back. It synced but would erased all my data. All my calender entries and contacts. I think i had either UBuntu or Debian...not sure.

---

