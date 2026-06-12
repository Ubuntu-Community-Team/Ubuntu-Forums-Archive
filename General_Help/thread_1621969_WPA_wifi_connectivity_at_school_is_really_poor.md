---
title: "WPA wifi connectivity at school is really poor"
date: 2010-11-14
forum: General Help
---

### Post by lue42x on 2010-11-14
I keep getting dropped from the WPA wifi at school, and when I am dropped from the network, I am often not able to re-connect for a long, long time.  

I'm not sure what to do ... I kind of need to be able to connect at school so I can use google docs to study with friends for exams

Edit: I should mention that I'm on 10.04 LTS

---

### Post by lue42x on 2010-11-15
I installed kubuntu-desktop, going to school today in an hour or so, hopefully it makes a difference

---

### Post by lue42x on 2010-11-15
no luck...

---

### Post by pqwoerituytrueiwoq on 2010-11-15
what is your wireless card?
```
hwinfo --wlan
```
you may need to install hwinfo for that 
```
sudo apt-get install hwinfo
```

---

### Post by lue42x on 2010-11-15
I'm not quite sure why ... but I got this message.  Should I try the apt-get -f install command it suggests?


adel@adel-laptop:~$ hwinfo --wlan
The program 'hwinfo' is currently not installed.  You can install it by typing:
sudo apt-get install hwinfo
adel@adel-laptop:~$ sudo apt-get install hwinfo
[sudo] password for adel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  akonadi-server: Depends: libakonadiprivate1 (>= 1.1.0) but it is not going to be installed
                  Depends: libboost-program-options1.40.0 (>= 1.40.0-1) but it is not going to be installed
  hwinfo: Depends: libhd16 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by lue42x on 2010-11-15
THis is the info for my wlan:

56: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: y9sn.JsGId2s67K7
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.0/0000:02:00.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "iwlagn"
  Driver Modules: "iwlagn"
  Device File: wlan0
  HW Address: 00:23:14:a2:ad:44
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #30 (WLAN controller)

---

### Post by owners4life5 on 2010-11-15
edited for ignorance

---

### Post by lue42x on 2010-11-21
Would using Endiswrapper work? I heard about this program a long time ago but never tried it out.  If I can find the Windows driver and use Endiswrapper with it, will that maybe solve the problem? If it doesn't is it easy to revert back to my original linux driver settings?

Also, is Endiswrapper hard to use?

---

