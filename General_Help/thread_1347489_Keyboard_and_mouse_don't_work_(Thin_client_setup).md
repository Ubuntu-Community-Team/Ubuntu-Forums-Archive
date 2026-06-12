---
title: "Keyboard and mouse don't work (Thin client setup)"
date: 2009-12-06
forum: General Help
---

### Post by Frogging101 on 2009-12-06
I have managed to set up an LTSP (Thin client) server. This server is a desktop computer running on Ubuntu 9.10 64-bit Desktop Edition. The only thin client on this network is a laptop connected with a network cable.

Bear in mind that the client is a LAPTOP, and the server is a DESKTOP.

Now, the problem:

When I start the laptop with the cable connected, it loads things (such as 'vmlinuz' and 'initrd.img') via TFTP, then takes me to a GUI login screen.

At this login screen, the mouse (touchpad) and keyboard don't respond to **ANY** input whatsoever. That obviously makes it effectively useless. The only way to turn off the computer is to hold down the power button. I may be way off with this, but it might have something to do with modules.

Any help would be appreciated.

**UPDATE:** When the client started up, I did:

```

ls /opt/ltsp/amd64/dev
```

And the output of that was:

```
agpgart   dsp2   loop5   midi2       ptmx   ram15  random     smpte3   tty4
audio     dsp3   loop6   midi3       pts    ram16  rmidi0     sndstat  tty5
audio1    fd     loop7   mixer       ram    ram2   rmidi1     stderr   tty6
audio2    full   mem     mixer1      ram0   ram3   rmidi2     stdin    tty7
audio3    kmem   midi0   mixer2      ram1   ram4   rmidi3     stdout   tty8
audioctl  loop0  midi00  mixer3      ram10  ram5   sequencer  tty      tty9
console   loop1  midi01  mpu401data  ram11  ram6   shm        tty0     urandom
core      loop2  midi02  mpu401stat  ram12  ram7   smpte0     tty1     zero
dsp       loop3  midi03  null        ram13  ram8   smpte1     tty2
dsp1      loop4  midi1   port        ram14  ram9   smpte2     tty3
```

Also, that output stays the same even if I turn the client off. Maybe the hardware isn't being detected.

---

### Post by Frogging101 on 2009-12-06
Bump. Nothing I've tried has worked.

---

### Post by Frogging101 on 2009-12-06
UPDATE: When the client started up, I did:

```
ls /opt/ltsp/amd64/dev
```

And the output of that was:

```
agpgart   dsp2   loop5   midi2       ptmx   ram15  random     smpte3   tty4
audio     dsp3   loop6   midi3       pts    ram16  rmidi0     sndstat  tty5
audio1    fd     loop7   mixer       ram    ram2   rmidi1     stderr   tty6
audio2    full   mem     mixer1      ram0   ram3   rmidi2     stdin    tty7
audio3    kmem   midi0   mixer2      ram1   ram4   rmidi3     stdout   tty8
audioctl  loop0  midi00  mixer3      ram10  ram5   sequencer  tty      tty9
console   loop1  midi01  mpu401data  ram11  ram6   shm        tty0     urandom
core      loop2  midi02  mpu401stat  ram12  ram7   smpte0     tty1     zero
dsp       loop3  midi03  null        ram13  ram8   smpte1     tty2
dsp1      loop4  midi1   port        ram14  ram9   smpte2     tty3
```

Also, that output stays the same even if I turn the client off. Maybe the hardware isn't being detected.

---

### Post by Frogging101 on 2009-12-06
Please, can I have an answer? I have searched everywhere. Also, I think it might be a permisiions issue. At the client start-up I see something like '/opt/ltsp/amd64/tmp/mkinitramfs_zOcSfN/sbin/mount.fuse: permission denied.'

---

