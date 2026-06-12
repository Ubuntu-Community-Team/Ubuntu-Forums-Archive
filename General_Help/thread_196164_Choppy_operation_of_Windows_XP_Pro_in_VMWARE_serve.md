---
title: "Choppy operation of Windows XP Pro in VMWARE server"
date: 2006-06-13
forum: General Help
---

### Post by gearshifter on 2006-06-13
I am having very choppy problems in vmware on a 

P-M 2.0ghz. 
1gb ram
60gb 7200rpm drive.

Ubuntu runs flawlessly, this laptop can hang with the best of them witha  6800go. 

I just don't understand why xp in vmware server is so choppy.  Scaling does seem to be on the slow side, so i tried manually setting scalling to performance that made the boot screen of xp really choppy.  I saw that my system resources in linux was about 144 megs of ram so that can't be the issue.

I've installed the vmware tool for xp already so that isn't the issue.


Anyone got any ideas?

thanks,
jason

---

### Post by DarthMandeep on 2006-06-13
I'm not sure if it will make a large enough difference, but you could try disabling the graphical effects XP uses by default and revert to the "classic" style.

---

### Post by scxtt on 2006-06-13
how much virtual ram are you assigning XP? -- i'd generally tell it to take 768MB, up from the default 256MB ...

---

### Post by c-prompt on 2006-06-14
Did you install those VMWare tools things?  I remember that on some machines, the video was always choppy until I installed those tools.

---

### Post by gearshifter on 2006-06-14
it's the appearence settings and at heavy load that things chop up.. i installed the tools and tried 512 ram but still have no luck..

you even notice it with nothing loaded.   when i open start>programs the programs part takes its time loading.  The windows bootup screen takes long too, the bar is extrememly choppy.

---

### Post by rcarring on 2006-06-14
VMWare only emulates an 8MB video card.

---

### Post by psyke83 on 2006-06-14
[QUOTE=gearshifter]Anyone got any ideas?[/QUOTE]Yes, you should disable debug (I'm quoting from a random site that's quoted it from another, heh):

```
    Fix - Stop the VM's

    /etc/init.d/vmware stop

    should do this. If you don't have the VMware Tools installed its better to shut down your guest systems manually before stopping VMware.

    Now go to the vmware lib directory at /usr/lib/vmware.

    There you'll find a directory called bin-debug. Move it to a new location, e.g.

    mv /usr/lib/vmware/bin-debug /usr/lib/vmware/bin-debug.bak

    Now make a symlink from the bin directory to bin-debug:

    ln -s /usr/lib/vmware/bin /usr/lib/vmware/bin-debug

    The bin directory contains the binaries stripped from debugging code. At least it did so on my installation :-)
    After creating the symlink, simply start up VMware Server:

    /etc/init.d/vmware start 
```

Things are much faster after doing that. Graphics are still choppy, but it'll be much better than before.

---

### Post by santo on 2006-06-14
Same problem here :sad: 
On my Fedora partition (on the same laptop), I notice exactly the same behaviour, so it doesn't seem to be Ubuntu specific.

When I use the same virtual machine under Windows (it's on a FAT32 partition and can therefore be accessed on both windows and linux),
there are no performance problems at all.

Maybe it's a problem in the VMware code for Linux ?

---

### Post by santo on 2006-06-14
I just realized that the original post was related to VMware server, 
while my problem is related to VMware workstation v5.5 (v5.5.1 build-19175).

Nevertheless the issues seem to be related.

I tried the suggestion of disabling the bin-debug directory and creating
a symlink to the bin directory, but I don't notice any improvements so far.

---

### Post by gearshifter on 2006-06-15
same here.. i still somehow think its a scaling issue.. dunno tho because when i set it to full performance, i see no change

---

### Post by scxtt on 2006-06-16
i installed XP on VMware server again (would just be using player, but i had to create the VM from scratch) and it's working flawlessly ... i've assigned it 768MB of RAM and when it's sleeping, it's only taking up about 30MB of RAM in Ubuntu ... and my start menu is about 95% as responsive as it is natively ... i haven't installed VMware tools either ...

---

