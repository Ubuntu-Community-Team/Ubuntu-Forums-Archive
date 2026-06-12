---
title: "Issues installing ubuntu 10.10 from usb"
date: 2011-03-27
forum: General Help
---

### Post by Mr_GSSF on 2011-03-27
I've been trying to install ubuntu 10.10 on a dell DE051 desktop its using Phoenix ROM BIOS PLUS Version 1.10 A00 for the BIOS, it makes me go through bios options before loading from usb  now the install process seems to work fine I'm using a different hard disk than the original one that had windows XP on it but when the installation is finished it goes to restart and comes up with an error and when it does reboot  it wont load from the hard disk drive and when i try to run ubuntu without installing  it sits on the ubuntu loading page I have tried recreating the usb boot version of ubuntu but no matter what I seem to do it seems like the bios is somehow stopping ubuntu from loading from the hard disk is this possible? if so how do i fix this? i used my original usb boot disk of ubuntu to install on a compaq mini 110 and did not run into these issues if anyone can help im open to suggestions thanks

---

### Post by cmcanulty on 2011-03-27
Did you reset bios after install to boot first to internal hard drive?

---

### Post by Mr_GSSF on 2011-03-30
yes  I did  and its really frustrating cuz Ive done everything i can think about ive even made sure to switch over the hard disk drive jumper so it reads as master and not slave ive tried switching it to be single as well but it  just wont load from the hard disak and like I said wen I try to boot ubuntu from usb it just sits on the loading screen

---

### Post by cmcanulty on 2011-03-30
I install Ubuntu on about 8 machines at our local library. Some are very old so I just keep throwing things at them until something works. Here is another thing to try.Burn a knoppix cd and run it live or a puppy CD they seem more tolerant of issues. Then from that live cd format your hard drive to ext 4. Then try booting to Ubuntu CD sometimes that extra step will allow an install on a screwed up or unusual setup. Of course that will delete any files you have so beware.Knoppix especially seems to work on absolutely anything.
[http://www.knoppix.net/get.php](http://www.knoppix.net/get.php)
[http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

---

### Post by Mr_GSSF on 2011-04-01
well thank you for your help but i ended up going with mandriva 2010.2 and it installed wonderfully  im also  going to be checking out the other linux versions you posted eventually  because i am a beginning user of linux products so im going to be trying all of the ones i can get my hands on ive already got another hdd set up with linux mint  and im alternating between both of them until i can convince my brother that linux is a better system for the kinda stuff he does and we find a good match for the kinda stuff we have planned and again thanks for your help :)

---

