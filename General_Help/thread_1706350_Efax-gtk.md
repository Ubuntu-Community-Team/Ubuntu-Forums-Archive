---
title: "Efax-gtk"
date: 2011-03-13
forum: General Help
---

### Post by gdiloren on 2011-03-13
Just installed version 3.2.3 from repository. When I send a .ps file by fax, I have this error message:
efax-0.9a: 17:38:19 Error: sync: modem not responding
I have a motorola modem internally and it was running fine under windows. Now, I previously had pc-fax printer  MFC-240C and it dialed and had a tone. Now, my Lexmark X5690 installation did not install any fax drivers but anyway with efax I only need to have a fax-modem- no???

---

### Post by gdiloren on 2011-03-13
Seems my modem is not detected but just last week with my previous brother multifunction everything was fine and I did not reinstall Linux. Forum is messy and confuse on faxing from pc with efax, not only this forum, but the efax web site as well. Seem to be a hair-tearing question.:popcorn:

---

### Post by gdiloren on 2011-03-14
My modem is now detected on port COM1. This is following a lot of package installs for Motorola modem 56K SM56 data fax modem. I installed the drivers from a thread in this forum and did sudo scanmodem. Now it prints to fax but there is no dial-up and the fax stays queued. I'm stucked there!!!:KS

---

### Post by gdiloren on 2011-03-14
Just tried to send a pdf document:
Socket running on port 9900
efax-0.9a: 11:50:13 opened /dev/ttySL0
efax-0.9a: 11:50:14 using /dev/slamr0 in class 1
efax-0.9a: 11:50:15 waiting for activity
efax-0.9a: 11:51:03 opened /dev/ttySL0
efax-0.9a: 11:51:04 using /dev/slamr0 in class 1
efax-0.9a: 11:51:04 dialing T5145076182
efax-0.9a: 11:51:43 connected
[COLOR=Red]efax-0.9a: 11:51:45 Warning: bit-reversed HDLC frame, reversing bit order[/COLOR]
efax-0.9a: 11:51:45 received UNKNOWN
efax-0.9a: 11:51:46 received CSI - answering ID
efax-0.9a: 11:51:46 The remote ID is        000  000 0000
efax-0.9a: 11:51:46 received DIS - answering capabilities
efax-0.9a: 11:51:46 remote has no documents to send and can receive
efax-0.9a: 11:51:46 local   196lpi 14.4kbps 8.5"/215mm  any   1D    -     -  0ms
efax-0.9a: 11:51:46 remote  196lpi 14.4kbps 8.5"/215mm  any   2D ECM-64   -  0ms
efax-0.9a: 11:51:46 session 196lpi 14.4kbps 8.5"/215mm  any   1D    -     -  0ms
efax-0.9a: 11:51:46 sent TSI - caller ID
efax-0.9a: 11:51:48 sent DCS - session format
efax-0.9a: 11:51:52 sent TCF - channel check of 2700 bytes
efax-0.9a: 11:51:53 received CFR - channel OK
efax-0.9a: 11:51:54 header:[2011-03-14 11:51    xxx (555 555 5555) --> 0000000000     1/2]
efax-0.9a: 11:51:54 Warning: EOF before RTC
efax-0.9a: 11:52:20 sent 20+2187 lines and 45947+0 bytes, in 26 secs at 14137 bps
efax-0.9a: 11:52:20 sent MPS - not done
efax-0.9a: 11:52:23 received MCF - page OK
efax-0.9a: 11:52:23 sent page /home/xxx/Documents/CV-S0810-xxx.pdf.001
efax-0.9a: 11:52:24 header:[2011-03-14 11:51    xxx (555 555 5555) --> 0000000000     2/2]
[COLOR=Red]efax-0.9a: 11:52:58 Warning: EOF before RTC[/COLOR]

---

### Post by gdiloren on 2011-03-14
Sender received the 6 faxes from me 100%. I hear no dialing but it's ok! I detected my modem (Motorola SM56 Data Fax Modem) by this[http://ubuntuforums.org/showpost.php?p=2756636&postcount=1](http://ubuntuforums.org/showpost.php?p=2756636&postcount=1)
be aware that the make install must be in folder where you untared 
ungrab-winmodem-20070505, mine was in the home/downloads folder for example, not in /tmp,
then download and use scanmodem to identify your port ttyS0 is COM1 and ttyS1 is COM2:
[http://linmodems.technion.ac.il/#scanModem](http://linmodems.technion.ac.il/#scanModem)

---

