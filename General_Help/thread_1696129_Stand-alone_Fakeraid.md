---
title: "Stand-alone Fakeraid?"
date: 2011-02-26
forum: General Help
---

### Post by Aceninja on 2011-02-26
Hi,

I'm a newbie to Linux and Ubuntu (just downloaded and installed Ubuntu 10.10 64bit desktop version). Here is my system setup at the moment:

1 Sata hdd running Windows 7 64 bit
1 sata hdd running Ubuntu 10.10 64 bit

Two 2 TB sata hdd's for storage/standalone using Intel Matrix Raid Manager on Windows. It is to my knowledge a Fake Raid system that uses the onboard motherboard chip along with the software in Windows to implement the RAID.

Now my question is, how can I get Ubuntu to recognize this fake raid that is not used for booting (just storage as i have dedicated drives for booting up both Win and Linux) in Ubuntu?

I have tried the fake raid how to, but it's geared towards ***installing*** Ubuntu on a fake raid setup, not recognizing a pre-existing (in Windows/BIOS ROM anyway) RAID array. The 2TB hdds do have lots of data, so I cannot afford a format/fresh setup, as it is already working in Windows.

Can someone please help? Thank you in advance :):popcorn:

---

### Post by ronparent on 2011-02-27
Boot your Ubuntu and open a terminal. Install dmraid - ie 'sudo apt-get install dmraid'. Test that it has activated the raid with 'sudo dmraid -ay'. A positive out put would tell you that your raids were activated. You should then be able to open the raid partitions with nautilus.

Althought dmraid is installed by default if you are installing to a raid drive it is not automatically installed otherwise. Post if you have a problem.

---

### Post by psusi on 2011-02-27
You do not have to do anything; it is recognized by default these days.

---

### Post by ronparent on 2011-02-28
psusi - my experience has been that if you install to a non raid drive that dmraid is not installed with it - you have to install it after. If you are saying it shouldn't be that way I tend to agree with you. Except then you are automatically subject to unintended consequences when the user has left unused RAID meta data on a drive from prior use! So I am undecided about what correct raid behavior should be. ;)

---

### Post by Aceninja on 2011-03-01
Ok I already have dmraid and I tried the steps you mentioned:


Reading state information... Done
dmraid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aceninja@aceninja-System-Product-Name:~$ [COLOR="DarkRed"]sudo dmraid -ay[/COLOR]
RAID set "isw_dcigeeddia_Raid 1" was not activated
aceninja@aceninja-System-Product-Name:~$ 

For some reason it did not work. When i click on "Computer" it shows the two 2 TB hdds separately. In windows I have no problems with it and is properly configured as Raid 1. In fact there is a BIOS bootrom that configures it in RAID mode as well. Can it be something else?

Thank you once again for the help.

---

### Post by Aceninja on 2011-03-01
Here is what I got when i typed:


aceninja@aceninja-System-Product-Name:~$ [COLOR="DarkRed"]sudo dmraid -r[/COLOR]
/dev/sdd: isw, "isw_dcigeeddia", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sdc: isw, "isw_dcigeeddia", GROUP, ok, 3907029166 sectors, data@ 0

---

### Post by psusi on 2011-03-01
The volume name "Raid 1" has a space in it, which I think is a no-no.

---

### Post by Aceninja on 2011-03-01
Fixed! Thank you for your help! That certainly worked! The raid is automatically detected by Ubuntu now :) Thanks a ton guys!

---

