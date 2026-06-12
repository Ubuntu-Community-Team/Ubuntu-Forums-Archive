---
title: "ATI dual monitor video only on primary"
date: 2005-03-17
forum: General Help
---

### Post by Phlegethon on 2005-03-17
Does anyone know how to get video displayed on both monitors in a dual monitor setup? I have an IBM Thinkpad T40 with an ATI Radeon Mobility 9000 M9, running Hoary with xorg-driver-fglrx 6.8.0-8.8.25-0ubuntu8.

---

### Post by zep24 on 2005-03-17
Hi, 
I was about to post the same thread. I assume you're using Clone mode. I'm experiencing the same problem with my radeon 9250 with the x.org OSS radeon dri driver: can't have overlay on my secondary monitor in clone mode (no problems with other modes). I think it's a problem with the MergedFB option, I can't say if it is a bug or if it is the new xorg behaviour (honestly I HOPE it's a bug). As I'm new to linux (switched 4 months ago) I can't be 100% percent sure. If a guru can give a look...

Normaly, to get overlay on the secondary monitor you should just add a line: 

      Option "OverlayOnCRTC2" "true"

to the Device section of your xorg.conf file, but when MergedFB is on (which is the default setting) it doesn't work. I think it's because:

>  MergedFB is enabled by default if a monitor is  detected in  each  output.  If no position is given it defaults to clone mode (the old clone options are now deprecated, also, the option OverlayOnCRTC2   has   been   replaced   by   the  Xv  attribute XV_SWITCHCRT; the overlay can be switched to CRT1 or CRT2 on the  fly in clone mode). 

That's a nice feature but I can't find how to switch overlay from CRT1 to CRT2 neither pemanently neither on the fly...

There is a workaround: first dump fglrx (you don't need these drivers for your radeon 9000 board, radeon driver from xorg works nice for 3d on it even with default ubuntu settings) and then add to the Device section of your xorg.conf the following lines:

     Option "MergedFB" "false" 
     Option "OverlayOnCRTC2" "true" 

and you will get overlay on your secondary monitor.

UNFORTUNATELY, if you do this the options 

     Option "CRT2HSync" "string" 

and

     Option "CRT2VRefresh" "string" 

stop having any effect (and so do the old xfree 4.3.0 "CloneHSync" and "CloneVRefresh" ). That's very anoying for me as my secondary monitor is a 17 years old Sony 21" CRT which works only with a 1024x768@60Hz resolution (very nice for watching DVDs a real torture for your eyes if you're trying to do anything else...).

So you have the choice:
    - without MergedFB you can't adjust refesh rate on secondary monitor and you can get overlay on it
    -  with MergedFB on you can't get overlay on secondary monitor but you can adjust its refesh rate. 

Maybe it's just the way xorg 6.8.2 behaves but I hope it's a bug as everything worked fine on warty's xfree 4.3.0 radeon dri driver (overlay and refresh rate). Can anybody more competent comfirm? Thanks in advance.

PS I'm sorry for my bad english but I'm french...

---

### Post by zep24 on 2005-03-17
I forgot to tell: if you don't use clone mode you can have overlay on the primary or secondary monitor  and you can switch on the fly but you can't have it in full screen mode (you can't even maximise the window).

---

