---
title: "generate xorg.conf from current configuration"
date: 2010-05-09
forum: General Help
---

### Post by Gatemaze on 2010-05-09
Hi,

xorg nowadays does not use a xorg.conf. Is it possibly to make it "spill out" one of the current configuration though?

Thanks,
GM

---

### Post by samsonasu on 2010-05-11
I agree this would be pretty helpful right now.

---

### Post by Point &amp; Click on 2010-05-14
Oh man, would that be helpful!

Does the logfile help you at all?

```
/var/log/Xorg.0.log
```
I'm pulling my hair out trying to get an old laptop going because Xorg & HAL aren't able to auto-detect the display's available resolutions properly (for whatever reason).

So, I'm looking around trying to piece together which bits I need from the automatically detected configuration, and which bits I need to supply.

I have been looking at the logfile and while it doesn't supply a ready formatted, complete xorg.conf it will give you a lot of details to generate one from.

But I'm still looking for a better solution...

---

### Post by Gatemaze on 2010-05-14
Thanks P&C, it is some progress... but still a "write_xorg" of the current configuration would be ideal

---

### Post by Point &amp; Click on 2010-05-18
I've spent some more time looking at this and it would appear that it is  possible afterall... 

In my case, (Ubuntu 9.10) I booted into  the recovery mode and ran

```
Xorg -configure
```This tells you that it generates the configuration file:  /root/xorg.conf.new

It also says that running the following will  test it:

```
X -config /root/xorg.conf.new
```However,  in my case I was pleasantly greated with black text on a black  background with a black cursor - either that or it didn't work...

2nd  time around:

```

cp /root/xorg.conf.new /etc/X11/xorg.conf
shutdown  -r now

```This appears to startup my laptop "normally", so I now have a configuration file to start playing with.

I have yet to check the logfile, etc, but I thought it answered your original post, so I thought I'd post asap

Hope it helps you (or anyone else!) out...

---

### Post by Joe-ubunt on 2010-05-18
> **Gatemaze said:**
> Hi,

xorg nowadays does not use a xorg.conf. Is it possibly to make it "spill out" one of the current configuration though?

Thanks,
GM
I use this command:

                          [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]sudo X :2 -configure[/SIZE][/FONT][/COLOR] 

the new xorg.conf file can be found in home/username folder

---

### Post by Gatemaze on 2010-05-19
Nice one. Thanks guys.

---

