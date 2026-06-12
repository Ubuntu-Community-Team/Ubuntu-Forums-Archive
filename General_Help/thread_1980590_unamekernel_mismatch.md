---
title: "uname/kernel mismatch?"
date: 2012-05-15
forum: General Help
---

### Post by Tuxedo Mask on 2012-05-15
My apologies if this is the wrong place for this; if so I will repost in the proper forum.

Earlier today, I was having issues with trying to mount the sd card on my phone using the USB port, getting a "mount: unknown filesystem type vfat" message whenever I tried. I'm running 10.04, for the record, since my system really can't handle anything better (and it had a seizure when I tried to install Oneiric, but more on that later). After digging around a few places I attempted to do the following:

```
modprobe vfat
```

as root and regular user, but I got the following error back:
```
FATAL: Could not load /lib/modules/3.0.0-19-generic-pae/modules.dep: No such file or directory
```

Turns out, my uname contains 3.0.0-19-generic-pae, but the most up-to-date kernel I can get is 2.6.32-41 (and that's the directory available for modules.dep). I'd like to be able to deal with this discrepency by having the system recognize one or the other as the most current version, but I'm not sure how to go about that.

Now, the reason there might be a muck-up is that, earlier this week, I was running 11.04 (or whichever version Natty is). My system has a partition for boot, swap, and then root (and everything else that goes with an install). When I tried to upgrade to Oneiric, my system had a meltdown and I couldn't get past the manufacturer screen. I tried a few ugly repairs with a LiveCD, but after a few more issues I essentially "wiped" boot and root. I then created two partitions from the former root partition; one was primary, which would be for home, and the other extended with two logical partitions within (in case I ever wanted to try a second shot at Oneiric). I left one of the logicals blank and told the LiveCD to install Lucid on the other one, then had it reformat boot and install a new boot partition there. After running it for a while and doing a Synaptic update, I thought everything was fine, but now I've run across this issue.

Apologies for the tome above; I'm sure my repeated reinstalls are the cause for this, I'm just not sure what, exactly, happened, as again I wiped boot and root and told the LiveCD to reinstall them both. The only thing that's preserved from before is the contents of home, but to my knowledge that shouldn't be influencing things like uname (of course, I could be wrong).

Any help in solving this, even if it means once more reinstalling and reformatting partitions, would be welcome. Thanks.

---

### Post by grahammechanical on 2012-05-15
This is just a guess. Check your Software Sources (repositories). See, if they match the version of the OS that you are supposed to be using.

It is possible that the attempt to upgrade was partially successful and it changed the software sources and downloaded certain bits that are causing uname to give this result.

Some of us have converted 12.04 into 12.10 by simply changing the repositories from precise to quantal and then updating. So, something similar may have happened to you. You may have got kernel 3.0 but not modules.dep

Another thing. when you reinstalled did you format? Or were you re-installing over existing files and are still there?

As I say. I am just guessing.

Regard

---

### Post by Tuxedo Mask on 2012-05-15
Right now, yeah, my repositories are all for Lucid, which is the version I'm using. And the kernel I have installed - or, at least, the one that Synaptic is telling me I have - is 2.6.32.

I did specify to format when I installed Lucid again; at the very least, I had the 5 partitions as described above (3 primary and 1 extended with 2 logical inside). One primary partition had the contents that would be /home (so everything from /home/(TuxedoMask) including the hidden files, in other words), another had /boot (which I was sure I formatted), and the last had swap (which I left alone). The extended partition used to be merged with the /home partition, but when I made it extended I naturally had to format it.

---

