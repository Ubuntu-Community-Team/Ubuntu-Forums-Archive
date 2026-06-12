---
title: "memory stick not mounting on ubuntu 9.10"
date: 2009-12-13
forum: General Help
---

### Post by khalid1100 on 2009-12-13
I have Ubuntu 9.10 installed on LG notebook X110 Atom 270. the system is intalled through woobi under Windows XP.
The memory sticks does not mount on the system. I have tries different types and none is working. I wounder if anybody can help with this issue

---

### Post by internalkernel on 2009-12-13
Try going to the Ubuntu Logo (i.e. Start menu) Select Accessories --> Terminal. 

Type: 

```
dmesg -f
```

Then plug in your Memory stick and see what kind of out put you get. Post some of that back here. If it's a huge amount of output please use pastebin or copy past it into a text file.

---

### Post by chaanakya_chiraag on 2009-12-13
Also, is this happening after a suspend?  I think there is something wrong after suspending sometimes in 9.10.  Try rebooting.  I've had the same issue before, and a reboot has fixed it.

---

### Post by khalid1100 on 2009-12-13
thanks for th quick response. this is the output:

dmesg: invalid option -- 'f'
Usage: dmesg [-c] [-n level] [-s bufsize]

---

### Post by khalid1100 on 2009-12-13
thanks for th quick response. this is the output:

dmesg: invalid option -- 'f'
Usage: dmesg [-c] [-n level] [-s bufsize]

---

### Post by internalkernel on 2009-12-13
> **khalid1100 said:**
> thanks for th quick response. this is the output:

dmesg: invalid option -- 'f'
Usage: dmesg [-c] [-n level] [-s bufsize]

Ha! My bad... 

try: 

```
tail -f /var/log/dmesg
```

---

### Post by khalid1100 on 2009-12-13
[   27.416010] 
[   27.416017] i915 0000:00:02.0: LVDS-1: EDID invalid.
[   27.506293] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   27.506305] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   27.510718] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   27.510730] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   27.520609] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   27.520621] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   27.524114] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   27.524125] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known

---

### Post by internalkernel on 2009-12-13
Did you unplug your memory stick first, run that command and then plug in the memory stick... 

That command will "follow" that file as out put is being written to it. When you plug in the memory stick you should see new output and that's what we are looking for - the result of plugging in the USB stick.

The output you posted looks normal, as if no memory stick was plugged in while that command was running. Is that the case?

---

### Post by khalid1100 on 2009-12-13
before plugging the memory stick:
[   27.416010] 
[   27.416017] i915 0000:00:02.0: LVDS-1: EDID invalid.
[   27.506293] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   27.506305] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   27.510718] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   27.510730] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   27.520609] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   27.520621] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   27.524114] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   27.524125] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.


After plugging the memory stick:

[   27.416010] 
[   27.416017] i915 0000:00:02.0: LVDS-1: EDID invalid.
[   27.506293] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   27.506305] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   27.510718] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   27.510730] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   27.520609] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[   27.520621] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[   27.524114] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[   27.524125] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.

---

### Post by internalkernel on 2009-12-13
Ok, let's try another approach... plug in the USB drive and just run: 

dmesg

We're looking for a few lines starting like this, and of course all the ones after it.  

[31673.984779] usb-storage: device found at 3
[31673.984773] usbcore: registered new interface driver usb-storage
[31673.984793] usb-storage: waiting for device to settle before scanning
[31673.984787] USB Mass Storage support registered.

---

### Post by khalid1100 on 2009-12-13
[25926.556366] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[25966.630172] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.630189] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.634167] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25966.634182] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.703902] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.703919] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.707424] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25966.707441] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.788524] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.788541] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.792077] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25966.792095] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.902577] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.902599] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.906270] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25966.906289] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.997672] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.997693] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25967.001377] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25967.001398] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25978.871202] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25978.871218] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25978.893144] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25978.893165] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25978.952915] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25978.952935] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25978.965258] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25978.965279] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25979.029994] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[25979.030011] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.047411] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[25979.047431] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.107005] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[25979.107022] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.122992] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[25979.123013] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.201264] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[25979.201284] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.221596] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[25979.221617] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26094.640122] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26099.144561] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26099.440245] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26124.648127] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26175.288616] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.288625] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.292161] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.292181] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.352809] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.352830] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.356295] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.356314] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.457374] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.457391] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.460665] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.460676] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.532711] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.532728] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.536076] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.536089] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.627120] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.627141] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.630454] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.630472] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.686702] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26176.686723] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.703409] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26176.703429] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.748560] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26176.748581] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.764659] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26176.764680] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.839010] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[26176.839026] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26176.859845] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[26176.859866] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26176.933755] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[26176.933771] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26176.954282] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[26176.954304] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26177.031251] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[26177.031267] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26177.047230] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[26177.047251] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26426.264109] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26445.760193] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26451.460405] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26480.272183] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26492.576128] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26540.904187] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26592.816128] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26629.276163] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26754.656093] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.656109] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.660173] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.660194] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.720852] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.720864] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.724395] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.724406] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.795676] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.795697] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.799220] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.799238] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.879259] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.879280] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.882773] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.882792] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.963821] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.963843] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.967307] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.967326] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.290671] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[27355.290692] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.294089] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[27355.294109] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.628813] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[27355.628834] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.632178] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[27355.632196] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.693683] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[27355.693704] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.697211] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[27355.697229] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27994.198978] CPU0 attaching NULL sched-domain.
[27994.198999] CPU1 attaching NULL sched-domain.
[27994.212437] CPU0 attaching sched-domain:
[27994.212454]  domain 0: span 0-1 level SIBLING
[27994.212467]   groups: 0 1
[27994.212490] CPU1 attaching sched-domain:
[27994.212500]  domain 0: span 0-1 level SIBLING
[27994.212511]   groups: 1 0
[27994.987111] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[27994.987132] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[27994.999562] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[27994.999584] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[27995.065085] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[27995.065106] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27995.081897] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[27995.081907] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28019.850665] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28019.850685] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28019.854233] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28019.854252] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28021.082909] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28021.082929] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28021.098761] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28021.098781] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28027.604137] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[28064.055380] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28064.055395] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28064.059045] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28064.059060] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28089.112124] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[28090.612141] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[28199.820159] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[28346.249885] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28346.249901] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28346.262161] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28346.262182] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28356.748737] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28356.748754] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28356.752218] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28356.752232] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28434.856850] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28434.856867] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28434.872366] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28434.872381] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28446.903047] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28446.903064] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28446.906436] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28446.906451] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28520.441262] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28520.441278] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28520.462258] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28520.462280] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28531.788247] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28531.788263] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28531.791629] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28531.791643] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28545.137743] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28545.137760] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28545.158211] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28545.158232] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28555.513611] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28555.513627] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28555.516902] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28555.516920] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28652.904795] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28652.904811] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28652.922395] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28652.922416] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28663.434247] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28663.434263] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28663.437741] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28663.437755] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28720.695480] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28720.695497] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28720.715966] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28720.715982] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28731.478629] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28731.478650] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28731.482338] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28731.482356] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28772.284375] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28772.284391] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28772.288135] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28772.288153] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28782.388814] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28782.388830] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28782.392504] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28782.392520] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28858.034057] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28858.034074] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28858.037456] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28858.037467] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28868.776166] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28868.776182] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28868.780375] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28868.780390] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28919.677369] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28919.677385] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28919.680967] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28919.680983] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28930.741533] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28930.741549] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28930.744896] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28930.744911] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29000.918304] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29000.918320] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29000.922151] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29000.922171] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29029.817696] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29029.817712] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29029.821196] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29029.821215] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29061.600906] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29061.600923] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29061.604951] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29061.604967] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29080.088817] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29080.088838] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29080.092208] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29080.092226] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29089.543256] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29089.543277] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29089.547498] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29089.547519] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29134.208129] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29134.208149] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29134.212349] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29134.212368] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29188.126025] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29188.126046] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29188.129566] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29188.129586] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29214.424114] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[29221.324107] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[29290.667616] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29290.667633] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29290.671123] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29290.671138] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29291.433853] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29291.433870] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29291.455160] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29291.455180] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29322.728093] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[29592.132127] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[29602.032591] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[29615.533981] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[29659.640143] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[29983.960206] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30013.064192] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30019.664145] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30036.764500] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30055.364200] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30068.564161] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30093.168114] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30094.668139] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30193.944155] Linking with vodafone_0142: channel is 6
[30196.461070] Linking with vodafone_0142: channel is 6
[30198.976499] Linking with vodafone_0142: channel is 6
[30199.011631] Associated successfully
[30199.011641] Using G rates
[30263.458940] Associated successfully
[30263.458953] Using G rates
[30271.064133] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30337.072196] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30441.484122] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30479.888116] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30494.288197] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30504.788196] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30516.189662] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30599.888296] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30614.288207] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30665.940159] Linking with vodafone_0142: channel is 6
[30665.958238] Associated successfully
[30665.958252] Using G rates
[30672.788176] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30841.424171] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30842.928124] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30923.948141] Linking with vodafone_0142: channel is 6
[30923.968612] Associated successfully
[30923.968623] Using G rates
[30967.552081] Associated successfully
[30967.552094] Using G rates
[30998.332132] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31150.140211] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31319.960169] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[31429.772132] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31528.788170] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31578.290849] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31579.788203] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[32152.364886] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[32152.364907] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32152.368792] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[32152.368811] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32194.746969] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[32194.746989] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32194.758671] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[32194.758682] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32212.240210] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[32261.366112] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[32261.366133] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32261.369675] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[32261.369693] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32287.617972] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[32287.617993] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32287.640093] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[32287.640112] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known

---

### Post by khalid1100 on 2009-12-13
[25926.556366] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[25966.630172] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.630189] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.634167] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25966.634182] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.703902] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.703919] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.707424] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25966.707441] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.788524] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.788541] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.792077] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25966.792095] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.902577] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.902599] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.906270] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25966.906289] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25966.997672] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25966.997693] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25967.001377] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25967.001398] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25978.871202] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25978.871218] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25978.893144] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25978.893165] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25978.952915] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[25978.952935] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25978.965258] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[25978.965279] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[25979.029994] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[25979.030011] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.047411] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[25979.047431] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.107005] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[25979.107022] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.122992] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[25979.123013] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.201264] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[25979.201284] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[25979.221596] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[25979.221617] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26094.640122] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26099.144561] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26099.440245] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26124.648127] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26175.288616] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.288625] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.292161] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.292181] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.352809] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.352830] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.356295] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.356314] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.457374] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.457391] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.460665] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.460676] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.532711] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.532728] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.536076] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.536089] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.627120] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26175.627141] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26175.630454] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26175.630472] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.686702] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26176.686723] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.703409] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26176.703429] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.748560] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26176.748581] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.764659] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26176.764680] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26176.839010] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[26176.839026] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26176.859845] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[26176.859866] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26176.933755] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[26176.933771] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26176.954282] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[26176.954304] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26177.031251] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[26177.031267] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26177.047230] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[26177.047251] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[26426.264109] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26445.760193] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26451.460405] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26480.272183] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26492.576128] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26540.904187] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26592.816128] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[26629.276163] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[26754.656093] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.656109] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.660173] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.660194] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.720852] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.720864] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.724395] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.724406] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.795676] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.795697] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.799220] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.799238] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.879259] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.879280] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.882773] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.882792] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.963821] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[26754.963843] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[26754.967307] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[26754.967326] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.290671] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[27355.290692] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.294089] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[27355.294109] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.628813] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[27355.628834] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.632178] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[27355.632196] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.693683] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[27355.693704] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27355.697211] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[27355.697229] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27994.198978] CPU0 attaching NULL sched-domain.
[27994.198999] CPU1 attaching NULL sched-domain.
[27994.212437] CPU0 attaching sched-domain:
[27994.212454]  domain 0: span 0-1 level SIBLING
[27994.212467]   groups: 0 1
[27994.212490] CPU1 attaching sched-domain:
[27994.212500]  domain 0: span 0-1 level SIBLING
[27994.212511]   groups: 1 0
[27994.987111] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[27994.987132] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[27994.999562] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[27994.999584] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[27995.065085] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[27995.065106] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[27995.081897] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[27995.081907] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28019.850665] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28019.850685] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28019.854233] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28019.854252] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28021.082909] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28021.082929] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28021.098761] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28021.098781] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28027.604137] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[28064.055380] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28064.055395] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28064.059045] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28064.059060] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28089.112124] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[28090.612141] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[28199.820159] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[28346.249885] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28346.249901] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28346.262161] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28346.262182] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28356.748737] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28356.748754] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28356.752218] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28356.752232] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28434.856850] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28434.856867] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28434.872366] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28434.872381] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28446.903047] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28446.903064] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28446.906436] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28446.906451] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28520.441262] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28520.441278] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28520.462258] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28520.462280] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28531.788247] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28531.788263] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28531.791629] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28531.791643] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28545.137743] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28545.137760] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28545.158211] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28545.158232] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28555.513611] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28555.513627] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28555.516902] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28555.516920] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28652.904795] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28652.904811] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28652.922395] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28652.922416] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28663.434247] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28663.434263] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28663.437741] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28663.437755] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28720.695480] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28720.695497] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28720.715966] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28720.715982] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28731.478629] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28731.478650] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28731.482338] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28731.482356] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28772.284375] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28772.284391] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28772.288135] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28772.288153] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28782.388814] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28782.388830] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28782.392504] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28782.392520] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28858.034057] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28858.034074] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28858.037456] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28858.037467] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28868.776166] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28868.776182] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28868.780375] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28868.780390] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28919.677369] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28919.677385] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28919.680967] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28919.680983] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28930.741533] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[28930.741549] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[28930.744896] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[28930.744911] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29000.918304] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29000.918320] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29000.922151] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29000.922171] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29029.817696] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29029.817712] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29029.821196] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29029.821215] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29061.600906] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29061.600923] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29061.604951] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29061.604967] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29080.088817] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29080.088838] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29080.092208] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29080.092226] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29089.543256] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29089.543277] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29089.547498] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29089.547519] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29134.208129] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29134.208149] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29134.212349] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29134.212368] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29188.126025] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29188.126046] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29188.129566] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29188.129586] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29214.424114] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[29221.324107] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[29290.667616] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29290.667633] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29290.671123] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29290.671138] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29291.433853] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[29291.433870] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29291.455160] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[29291.455180] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[29322.728093] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[29592.132127] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[29602.032591] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[29615.533981] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[29659.640143] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[29983.960206] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30013.064192] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30019.664145] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30036.764500] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30055.364200] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30068.564161] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30093.168114] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30094.668139] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30193.944155] Linking with vodafone_0142: channel is 6
[30196.461070] Linking with vodafone_0142: channel is 6
[30198.976499] Linking with vodafone_0142: channel is 6
[30199.011631] Associated successfully
[30199.011641] Using G rates
[30263.458940] Associated successfully
[30263.458953] Using G rates
[30271.064133] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30337.072196] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30441.484122] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30479.888116] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30494.288197] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30504.788196] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30516.189662] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30599.888296] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30614.288207] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30665.940159] Linking with vodafone_0142: channel is 6
[30665.958238] Associated successfully
[30665.958252] Using G rates
[30672.788176] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30841.424171] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[30842.928124] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[30923.948141] Linking with vodafone_0142: channel is 6
[30923.968612] Associated successfully
[30923.968623] Using G rates
[30967.552081] Associated successfully
[30967.552094] Using G rates
[30998.332132] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31150.140211] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31319.960169] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[31429.772132] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31528.788170] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31578.290849] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[31579.788203] StaRateAdaptive87SE(): update init_gain to index 2 for date rate 36
[32152.364886] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[32152.364907] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32152.368792] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[32152.368811] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32194.746969] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[32194.746989] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32194.758671] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[32194.758682] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32212.240210] StaRateAdaptive87SE(): update init_gain to index 1 for date rate 22
[32261.366112] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[32261.366133] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32261.369675] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[32261.369693] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32287.617972] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[32287.617993] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[32287.640093] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[32287.640112] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known

---

### Post by internalkernel on 2009-12-13
Ok instead of posting ALL the output... we're really only looking for a couple of lines that are at the very bottom and that specifically refer to: 

[31673.984779] usb-storage: device found at 3
[31673.984773] usbcore: registered new interface driver usb-storage
[31673.984793] usb-storage: waiting for device to settle before scanning


If those are not in the dmesg output then your machine is not identifying the USB stick at all. But, you're saying windows identifies that just fine, right?

---

### Post by khalid1100 on 2009-12-13
Those lines are not in the output. That means the machine is not detecting the usb at all. Connecting other devices to the USB work fine like external mouse.
yes running windows the machine detects the usb stick normally. 
also the old Ubuntu 9.04 used to detected the memory stick automatically.

---

### Post by internalkernel on 2009-12-13
check the output of:

```
lsusb
```

while the USB drive is plugged in, we should see a listing of all USB devices attached. Have you tried booting while the USB device is plugged in? that may help to narrow down the issue.

---

### Post by khalid1100 on 2009-12-13
this is the output when the usb is plugged in:
Bus 001 Device 002: ID 5986:0203 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
I will reboot with the memory stick plugged in and try check the output again

I appreciate your help

---

### Post by khalid1100 on 2009-12-13
after rebooT wiTH THe MEMORY stick plugged in:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 5986:0203 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by internalkernel on 2009-12-13
In another thread the user reported success after installing the backported modules: 

```
sudo apt-get install linux-backports-modules-karmic
```

Unfortunately, I don't know exactly what type of laptop you have - other than Acer. But, I would try searching google for your laptop type, ubuntu and USB not recognized. 

The other commands that may help shed some light on this would be: 

```
sudo lspci -v
```  

This will show all the hardware on your system, you'll have to go line by line until you find something similar to this: 

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: COMPAL Electronics Inc Device 0031
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1860 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd


That's my USB controller, at the very bottom you can see Kernel Driver in use. Obviously, if those lines don't exist theres the problem. 

If they are there, then try: 

```
lsmod |grep uhci_hcd
```

lsmod will list all loaded modules in the system, then grep will only show which lines have that expression in them - in this uhci_hcd. However, you will want to replace uhci_hcd with whatever kernel driver is in use for your system.

---

### Post by khalid1100 on 2009-12-13
My laptop is LG X110. I don't know why the output is saying Acer.

---

### Post by chaanakya_chiraag on 2009-12-14
Just wondering, does this happen only after resuming the laptop from suspend/hibernate?

---

