---
title: "Wierd permissions / network manager problem."
date: 2010-11-27
forum: General Help
---

### Post by zozza on 2010-11-27
Hello,

I am trying to use a UK Vodafone K3570-Z USB as my mobile broadband.  I am using 10.04.

I think my problem is something to do with permissions - let me explain.

I put the device in the USB.  After a few seconds the light comes on.  Lsusb finds it. 

I run the "wizard" thing in Network Manager to set up a mobile broadband connection.  It gives me an APN.  All seems fine. 

When I click on the icon on the panel that allows me to select my networks I have the option of using wired, wireless, or VPN.  But there is nothing for the mobile broadband network I have setup.  Even after a reboot. 

The reason I think this is a permissions issue is because when I try to edit the settings in network manager I get the request for a password box which means root privileges are required.  When I click "details" the box shows:

Action: org.freedesktop.network-manager-settings.system.modify
Vendor: Network Manager

When I edit settings for wired, wireless, and VPN networks I am not asked for my password.

The only thing I can assume is that the permissions are preventing the icon on the panel from displaying an option to select mobile broadband.

I have been in contact via PM with other people using the same mobile broadband.  They all say that the mobile broadband option just appears in the menu with no problems.  

Any ideas?  Thanks.

---

### Post by andrewthomas on 2010-11-27
try adding your user to the plugdev and netdev groups

---

### Post by crf on 2010-11-27
Does it matter if you have chosen to make the connection available to all users (in the network manager edit connections dialog)?

---

### Post by zozza on 2010-11-28
> try adding your user to the plugdev and netdev groups


A "groups" request shows

zozza adm dialout cdrom plugdev lpadmin admin sambashare

When I do:

sudo usermod -a -G netdev zozza 

it seems to work but then "groups" shows the same as above (no netdev added)

Any ideas?  Thanks again!

> Does it matter if you have chosen to make the connection available to  all users (in the network manager edit connections dialog)? 	

No, it was available to all users from the start.

---

### Post by zozza on 2010-11-30
I am now a member of plugdev and netdev but still have the same problem - no opportunity to select in the menu my mobile broadband connection.

---

### Post by tpwfl on 2010-12-02
I had this same problem.  After doing the above group changes, I then had to apply a very Windows-ish problem solving methodology -- reboot a few times. This brought up the mobile broadband tab and allowed me to type some settings in.  Interestingly, the mobile broadband works under my account but my wife's account does not work.  However, wvdial works a treat for her.

---

### Post by zozza on 2010-12-02
I have rebooted dozens of times and I still can't see the connection option. 

Wvdial seems to check /dev/modem.  It doesn't work for me and I don't believe the mobile broadband is considered to be a /dev/modem device.

Can anyone help?  Or I will just give up!

---

### Post by tpwfl on 2010-12-02
I've looked at your groups more closely and there isn't a "dip" group.  According to 

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

you also need to be in the dip group

---

### Post by tpwfl on 2010-12-02
Got my wife's account to work. I had put too many '*'s in the phone number

---

