---
title: "Keyboard don't work"
date: 2012-06-11
forum: General Help
---

### Post by Kira_Belka on 2012-06-11
Hi everybody!
I'm in trouble(as common :KS )
so I have Acer 5750G (i3 i2320, 4Gb RAM and nvidia optimus(GT540M)) and 
Ubuntu 10.04(lucid) installed on it.
mmmm.. I upgraded it to ubuntu 10.10(maverick) and all was fine.
But I decided to install Bumblebee drivers for optimus and I added PPA for Xorg.(also mb several other PPA's.. not so much.. mb 8-9 PPA's :) )
and I rebooted and All seemed fine..but keyboard don't work..
and "onboard" keyboard don't work too.
Oh.. I forgot.. I installed acerhk-source also..
Anybody helps me![-o<
Certainly I can just reinstall system but it's not Ubuntu way :)

---

### Post by Kira_Belka on 2012-06-12
S.o.s.!

---

### Post by oldfred on 2012-06-13
Since it is the newer i3 series Intel chip and Optimus have you tried a liveCD of 12.04? Often new chips require some time before Linux catches up with the new features. Or you have to do many work arounds to make it work.

Some find turning one or the other video works, even if you do not get the advantage of Optimus.

---

### Post by Kira_Belka on 2012-06-13
Thanks for reply.
mmm.. All works fine or at least "no bad" with most Ubuntu Live CD's on this hardware.
I tryed Ubuntu 10.04 Live CD, Ubuntu 10.10 Live CD, Ubuntu 11.10 Live CD.
so:
Ubuntu 10.04 
wifi and ethernet doesn't work (there are no drivers for these broadcom wifi/ethernet cards in this distro)
sound doesn't work(I suppose this hda-intel sound cart not compatible with alsa 1.023)
video card works as vesa card.
keyboard and touchpad works fine.
broadcom drivers are placed on official site so it's not a prob.
Compilation latest Alsa from sources 's not prob 2.

Ubuntu 10.10
wifi and ethernet works.
sound works.
video card works as vesa card.
keyboard and touchpad works fine.

Ubuntu 11.10
wifi and ethernet works.
sound works.
video card works as vesa card.
keyboard and touchpad works fine.

I understand that easy greatly more just to reinstall newest version of Ubuntu..but I'm just interested what 's wrong with my system? WHy keyboard doesn't work in gnome/GDM and I suppose in Xorg too.. 
Mb anybody has contacts of developers.
Mb it's just my stupid curiosity...but I want to repair my system:popcorn:.

---

### Post by oldfred on 2012-06-13
This says everything but special keys works with 11.10.

[https://friendly.ubuntu.com/11.10/Acer/Aspire%205750G/I:CL9W0p:E4:I8g:Ui:BEfp:vc:BHe:Uj:BEfp:E4E:BYQ:Ovw:BF7/](https://friendly.ubuntu.com/11.10/Acer/Aspire%205750G/I:CL9W0p:E4:I8g:Ui:BEfp:vc:BHe:Uj:BEfp:E4E:BYQ:Ovw:BF7/)

Some issues in this thread and the acpi_osi=Linux workaround


[http://ubuntuforums.org/showthread.php?t=1802755](http://ubuntuforums.org/showthread.php?t=1802755)

---

### Post by Kira_Belka on 2012-06-14
mb it sounds like magic..
but I just recreated my user account.
and all was repaired.
:guitar:

---

