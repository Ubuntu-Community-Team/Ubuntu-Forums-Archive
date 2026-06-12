---
title: "Bluetooth DUN connection failure"
date: 2011-08-28
forum: General Help
---

### Post by supercooledmaterial on 2011-08-28
Cant connect my nokia 5230 using bluetooth modem after pairing when i  click on the checkbox stating "access the internet using phone (DUN) it  fails to configure the device and gives and error message : [COLOR=Red]the  remote application did not send a reply, the message bus security  policy blocked the reply, the reply timed out or network connection  blocked the reply..[/COLOR]
PLEASE HELP!

---

### Post by raja.genupula on 2011-08-28
in your mobile was the settings are properly configured or not . man but everytime bluetooth  is not a good idea , my suggestion is a buy a data cable . ubuntu will detect the modem in nokia phones automatically . i am getting connection with my 2690 mobile .

---

### Post by fenixjose on 2012-05-15
> **supercooledmaterial said:**
> Cant connect my nokia 5230 using bluetooth modem after pairing when i  click on the checkbox stating "access the internet using phone (DUN) it  fails to configure the device and gives and error message : [COLOR=Red]the  remote application did not send a reply, the message bus security  policy blocked the reply, the reply timed out or network connection  blocked the reply..[/COLOR]
PLEASE HELP!
Hi,
I have blackberry 9100, Internet provider Claro - El Salvador.
I just searched with "Ubuntu software center" for "tether" and "blackberry" and installed the following:
tether:
ipteth-utils
python-scapy

Blackberry:
libbarry0
libbarry0-dbg
barrybackup-gui-dbg
barry-util-dbg
barry-util
barrybackup-gui
libbarry-dev
ogmrip-profiles

After that, configured bluetooth and clicked "DUN" because i want to access internet trought my cell phone. Then the wizard worked and now I have enabled the option "Claro" in my network menu.

Hope it helps

---

### Post by Steve White on 2012-05-25
Hi,

When Bluetooth is working right, as it was in the Ubuntu 10.10 an othere OSs, it's just wonderful.  I had multiple devices playing together with very few problems.  People who say "nay" invariably don't know what they're talking about.

Until the 11.x series.  I had the same problem, with a different phone, and so did everybody else.  Many bug reports were filed.  For instance 
   [https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/879923](https://bugs.launchpad.net/ubuntu/+source/obexd/+bug/879923)

Fortunately, much of this problem is now resolved by a kernel patch in recent updates to Ubuntu 12.04, and I now use Bluetooth DUN on a daily basis.

(I still have the problem that if the DUN connection is broken, it can't be re-established without re-boot.  But I don't know if that's a NetworkManager problem or Bluetooth.)

---

