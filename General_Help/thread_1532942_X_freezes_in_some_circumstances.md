---
title: "X freezes in some circumstances"
date: 2010-07-17
forum: General Help
---

### Post by nereid on 2010-07-17
Hi folks,

I've discovered a rather curious error on my PC.

Recently I started to play some games using Wine again and I discovered, that X will freeze most of the time, when I start the games.

It seems, that this is a problem with my nVidia card or even X, as I also got the same error while switching from Metacity back to Compiz.

Another strange thing is, that X is not completely frozen, as I can still move the mouse and it also reacts to keystrokes (even if they are severely delayed). And if I switch to another tty, things work rather fine (restarting X is another matter, which almost all of the time gets me to restart the whole PC. Somebody has decided to deactivate the X kill switch by default in Lucid...).

I'm currently using the latest drivers from the Ubuntu-X team (this means 256.x or something like that). Another curiosity is, that I can use Compiz as my window manager without a problem. It seems that there are only problems with context switching.

I would be really delighted, if anybody could help me or at least point me in the right direction. Cheers and thanks in advance.

---

### Post by nereid on 2010-07-17
Ok, checking the various logs in /var/log resulted in a hit.

It seems, that the nvidia driver is the culprit:

```
Jul 16 17:35:06 antares kernel: [ 1180.628088] NVRM: Xid (0002:00): 8, Channel 00000004
...
Jul 17 16:09:32 antares kernel: [13589.026019] NVRM: RmInitAdapter failed! 0x12:0x2b:1671)
Jul 17 16:09:32 antares kernel: [13589.026029] NVRM: rm_init_adapter(0) failed
```

Are the log entries from kern.log. I can't even start VirtualBox without hosing X...

I'm still up for any hints ;) And I could try to revert the nvidia driver to the original Lucid one, althought that one also wasn't the best.

---

### Post by nereid on 2010-07-17
Great, reverting to the original driver did the trick.

On the other hand, it is really sad, that nVidia has introduced this sort of bug into their drivers. The whole X server goes to hell, as soon as the card has to do a little bit work.

---

### Post by nereid on 2010-07-18
Darn, the original Lucid driver has the same problem, although not as often as the newer one.

Because of this I marked the thread as unsolved again and I am still happy to receive any help or even just a pointer in the right direction.

It seems, that I am also not alone: [http://ubuntuforums.org/showthread.php?t=1163786](http://ubuntuforums.org/showthread.php?t=1163786)

---

### Post by dino99 on 2010-07-18
what i do when things goes wrong:

into synaptic: install bleachbit and gconf-cleaner to remove the mess left behind (use bleachbit as admin but set correctly your prefs)

remove/purge then reinstall the drivers: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

take care of the non genuine ubuntu repo (ppa (x-swat is a trusted one), manual install )

and of course, after reboot, check that nvidia-current is activated (system admin hardware driver)

---

### Post by nereid on 2010-07-18
Thanks for the post, dino99.

But it seems, that I've got it worked out (for now ;), as in for about an hour... ).

According to the nVidia devs, you should boot the kernel with the following

```
pci=nommconf
```

If you have a multicore CPU and *dmesg* yields something along the following

```
PCI using MMCONF...
```

Additionally I also boot the kernel with

```
nomodeset
```

As this is not supported by the binary nVidia drivers (althought I am not really sure, if that is really needed. Didn't really make a difference before).

---

### Post by nereid on 2010-07-20
It seems, that X doesn't really freeze, but starts lagging a lot. If I am lucky, I am able to kill the offending program and X returns to the normal state.

I think, that the Xid messages from the nVidia driver are some indicator for a large time out.

---

### Post by nereid on 2010-07-21
Things get stranger and stranger...

It seems, it is enough, to restart X to get OpenGL working again and I should run nothing else before the offending program. This means in my case, I shouldn't start Firefox and/or Thunderbird. If I don't do this, I can put some load on the GPU.

---

### Post by eznet on 2010-08-17
Nereid, I am assuming since you have continued to post here, that this is still a problem for you?  I too am experiencing this issue... 

Just reinstalled Ubuntu 10.04x64 with the latest NVidia binary and this began...  Usually, I notice it after the system has gone to idle and activated the screensaver... I have also noticed it when loading Virtual box. 

Same entries as you in syslog.  If I check the previous Xorg log, I see errors about the module not being present, but know this isn't right as they are, I can see em and a reboot magically allows the kernel to see em... so...  Well, off to spend what will likely grow into hours trying to figure this out :P

---

