---
title: "Please Help me set up my TV TUNER"
date: 2006-06-08
forum: General Help
---

### Post by medya on 2006-06-08
I had one time long time ago , could set up my TV tuner card in linux....
but now I dont know how.

I can see that ubuntu has found my car,... I see it in Device manager.
Philips Semiconductors
SAA7130 Video Broadcast Decoder


I have installed TVTIME ... but it seems TVTIME doenst know my tv tuner.
> 
fred@fred-desktop:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/fred/.tvtime/tvtime.xml
Scanning using TV standard PAL.

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.


please help ...I dont want to go back to windows to watch World Cup Games

---

### Post by SimonTheMime on 2006-06-08
Me too, same card, same problem. Help us!

---

### Post by chronusdark on 2006-06-08
what is the name of your card like i have a sabrent TVFM card
i have been doing alot of work on this particular card

---

### Post by SimonTheMime on 2006-06-08
Philips SAA7130HL

---

### Post by scxtt on 2006-06-08
what's the output of "modprobe -l | grep bttv" give you?

i get:

/lib/modules/2.6.12-10-386/kernel/drivers/media/video/bttv.ko

in breezy, and it works in dapper as well ...

shows up as Bt878 video/audio capture in the D.M. ... (i have an ATI TV Wonder VE - nice, cheap & effective) ...

FWIW, i don't have to do much of anything to get TV working - just a few settings in my TVtime config - i can even just copy/paste it anytime i install tvtime and it works just as it had before ...

---

### Post by hxx4 on 2006-06-08
I have a KWorld TV tuner and the same problem. :???:

---

### Post by palermi on 2006-06-08
[http://www.linuxtv.org/](http://www.linuxtv.org/)

---

### Post by medya on 2006-06-09
[QUOTE=scxtt]what's the output of "modprobe -l | grep bttv" give you?

i get:

/lib/modules/2.6.12-10-386/kernel/drivers/media/video/bttv.ko
in breezy, and it works in dapper as well ...
[/QUOTE]

/lib/modules/2.6.15-23-386/kernel/drivers/media/video/bttv.ko


and I think my card doenst use bbtv driver,,, it uses saa7130

---

### Post by scxtt on 2006-06-10
[QUOTE=medya]/lib/modules/2.6.15-23-386/kernel/drivers/media/video/bttv.ko

and I think my card doenst use bbtv driver,,, it uses saa7130[/QUOTE]so what happens when you do a "modprobe -l | grep saa"?

i get:```
$hostname [~]
:> modprobe -l | grep saa
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa7185.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa7134/saa7134.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa7134/saa7134-dvb.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa7134/saa6752hs.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa7134/saa7134-empress.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa7114.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa7111.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa7110.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa5249.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/video/saa5246a.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/common/saa7146_vv.ko
/lib/modules/2.6.12-10-386/kernel/drivers/media/common/saa7146.ko
```

---

### Post by nik on 2006-06-10
I have a different card, using the saa7134 module. All I had to do was add```
saa7134 card=39
``` to /etc/modules. The card number is from the documentation for the module, and is needed for some cards that doesn't get autodetected.

---

### Post by medya on 2006-06-10
scxtt : I get the same result that u get

nik , where is the documentation which I can see what is my card number?

---

### Post by tkman on 2006-06-12
I'm going to bump this message because I too would like to know where to find the module documentation so I can find my card number.

---

### Post by nik on 2006-06-12
sorry, missed it the first time...

anyway, couldn't find the documentation now, I have a new installation... but take a look here
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)
and see if that helps...

---

### Post by darkteckno on 2006-09-20
> **hxx4 said:**
> I have a KWorld TV tuner and the same problem. :???:
Try asking here: [http://tech.groups.yahoo.com/group/KWORLD-TV/](http://tech.groups.yahoo.com/group/KWORLD-TV/)

---

