---
title: "Stuck in botnet anything i do get backin it? bios is bad try flashing it? error"
date: 2011-02-21
forum: General Help
---

### Post by elifecoach on 2011-02-21
Got in a botnet nothings works starting from usb or scdrom with live cd does not work. flashing bios gives error help!!!
Bot net infected my 6 win computers en 4 ubuntu ones. Its very fast. Try working around it but failed! Think router is bad :( xs4all will not give me new IP :( what to do? help!!!! UpNP is off I work on a open network, router is fitzbox 7170

---

### Post by eentonig on 2011-02-21
Why do you suspect being a botnet and think your 6 Windows and 4 Ubuntu pc's are infected?

If you're infected, flashing BIOS won't do any good. Re-installing the OS will be much better.

---

### Post by elifecoach on 2011-02-21
because my systemsoftware changed and my permittions changed not by me! I got less rights that i not have changed as admin and my phone ask me for my puccode wikth the same pin!
All the computers that i want to fight the botnet got quikly infected by modem router of wireless wifi my phone as turn into. i did not change cdrom boot defaults but yet I cound not boot from cdrom or usb or floppy. The system only boot from HD. Everything else has taken over by the botnet. I had my computers shared files behaind my firewall so i could work with every computer. but once the botnet effected one computers is has taken over the whole network! Now everything is stand alone en working only with linux for a while till when i know for sure i canb reach the internet en secure sites freely.
Linux 486 with networking is the only one now connected but still i am in trhe botnet. becouse i cannot reach https sites.
I want to download a live cd for ubuntu of live cd or floppy of linux. But all the sites i visit give errors the botnet is keeping me away from solutions! 
Now i am on a public computer with win xp and steady state That version i will install on all my pc's and togetger with ubuntu. But i looking for a good firewall and anytivirus for linux and windows;
eset; crappy firewall!
norton; slow down the sytem
kaspersky ; gives lots of errors and no solution but alot of notoifications.
 
The plan is now to protect my router with a new IP and no UPNP and behind that a 486 or PII or PII with linux and a live cd of linux with a good firewall and options to get internet access for my laptop and other computers behind that firewall; Looking now for a good advanced program that will do that for me; Any suggestions are welkom....:)
 
Once I have my old linux firewall PC behind a good public router and new IP I can install Ubuntu savely (ordered live cd from site! within 6-8 weeks i get it send home...)
 
After that I flash all my bios en clean all HD and usb disks and floppy's , protect all my computers with the newest ubuntu and updates and the best firewalls for linux and windows xp or vista and steady state.
Then i run nortons botnet detector and hoppe i am save?
 
Have I forgot anaything? please reply and give me good suggestions i a linux n00B
 
After that I will be free from botnets and virussen or malware
 
:guitar:

---

### Post by elifecoach on 2011-03-01
I installed (on 2 pc's) xp prof sp2+sp3 and wil validate it! After succesful start and after installed virussoftware and firewalls. Ik install a linux pc with firewall behind that my network.
 
Does anyone can recommand me best linux antivirussoftware or firewallsoftware and a software to configure firewall on a PIII or PIV 500hmz with small linux and a boot cd linux or boor floppy with firewall.
 
Or can i install Ubuntu minimal or other distribution just for firewall settings? Witch software do i have to install? for good firewall?

---

### Post by matt_symes on 2011-03-01
Hi

> Does anyone can recommand me best linux antivirussoftware or firewallsoftware and a software to configure firewall ...

Enable IPtables and let netfilter do its job. Install either ufw (command line) or gufw (GUI) to configure the firewall.

[http://www.webupd8.org/2010/10/gufw-is-easy-to-use-ufw-uncomplicated.html](http://www.webupd8.org/2010/10/gufw-is-easy-to-use-ufw-uncomplicated.html)

ClamAv is good anti-virus software but has been known to give a number of false positives.

```
sudo apt-get install clamav 
```

and to update the definitions

```
sudo freshclam
```

Advast is also highly recommended anti virus software

[http://www.ubuntugeek.com/how-to-install-avast-anti-virus-software-in-ubuntu-10-10-maverick.html](http://www.ubuntugeek.com/how-to-install-avast-anti-virus-software-in-ubuntu-10-10-maverick.html)

Kind regards

---

