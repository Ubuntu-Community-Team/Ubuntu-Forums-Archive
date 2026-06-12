---
title: "Difficulty mutli-tasking? Video choppy during file copy."
date: 2011-10-19
forum: General Help
---

### Post by scottbomb on 2011-10-19
I'm running a fresh install of Xubuntu 11.10 on a home-made 3-core 64-bit AMD system (3.1 GHz CPU, 300 GB HD and 1.5 TB HD). I was watching a .avi video while simultaneously copying a 3GB tar file from the 300 GB drive to the 1.5 TB drive. This caused the video (which is also on the 1.5 TB drive) to be very choppy. I'm also using the stock Parole media player that came with Xubuntu. [I prefer VLC but due to it's audio issues (ongoing issues discussed in other threads) that player is practically broken and unusable until the devs fix it.]

Is there some particular reason why the system seems to choke on a simple multi-task such as this? I do not believe this is a hardware issue as I dual-boot with Windows 7 which has no problems with such workloads.

---

### Post by Jose Catre-Vandis on 2011-10-19
What video card have you got? Latest drivers installed? Try turning off Compositing?

---

### Post by thatguruguy on 2011-10-19
Do you have the 32-bit or the 64-bit version of Xubuntu installed?

As an aside, vlc has been fixed.  The fix should roll out soon to the regular repos, or you can get it now if you enable Oneiric-proposed in your software sources and run an update.

EDIT: and it seems like the problem isn't a true "multi-tasking" problem (that is, an issue involving the OS running several tasks at once), but a hardware bottleneck w/r/t moving information on and off the 1.5 TB disk.  Is it an internal or external drive?  Is it NTFS, ext4, or some other file system?

---

### Post by scottbomb on 2011-10-19
The video card is ATI 4350. The driver is a proprietary driver the OS recommended when I did the install. In fact, there were 2 driver versions it proposed. It said the second one was made after the initial release. I got the impression it was talking about being made after the initial release of Xubuntu 11.10 because I was prevs running 11.04 and that OS only mentioned the 1st option. I tried to install that second driver first as I figured it was a newer version but the installation failed. I went with the 1st one and it took.

I would not expect compositing to affect this as the computer runs very well under Win 7 with aero glass. I should also mention it has 4 GB of RAM. Under Win 7, I can burn a DVD, install software, and watch a video all the same time without even a hiccup. 

Perhaps I should see if it will now take that 2nd ATI driver it proposed when I did the install a few days ago?

Yes, the 1.5 TB disk is all NTFS. Would that make so much a difference on it's own?

I'll definately look up that new VLC. Thanks for the tip!

EDIT: My Xubuntu is 64 bit and all drives involved are internal.

---

### Post by gsmanners on 2011-10-19
> **scottbomb said:**
> I would not expect compositing to affect this as the computer runs very well under Win 7 with aero glass. I should also mention it has 4 GB of RAM. Under Win 7, I can burn a DVD, install software, and watch a video all the same time without even a hiccup.

I'll bet compositing is causing something (tearing video at the very least).

---

### Post by Gyokuro on 2011-10-19
> **scottbomb said:**
> I'm running a fresh install of Xubuntu 11.10 on a home-made 3-core 64-bit AMD system (3.1 GHz CPU, 300 GB HD and 1.5 TB HD). I was watching a .avi video while simultaneously copying a 3GB tar file from the 300 GB drive to the 1.5 TB drive. This caused the video (which is also on the 1.5 TB drive) to be very choppy. I'm also using the stock Parole media player that came with Xubuntu. [I prefer VLC but due to it's audio issues (ongoing issues discussed in other threads) that player is practically broken and unusable until the devs fix it.]

Is there some particular reason why the system seems to choke on a simple multi-task such as this? I do not believe this is a hardware issue as I dual-boot with Windows 7 which has no problems with such workloads.

It seems that your bottleneck is your HD - you can check via iostat what goes over your disk and check via top what's up with your system - copying from usb to internal disks can show this problem - however you can try to copy from command line and you mentioned you are using a dual-boot system - Windows 7 if you installed it at first lays at the other space of your HD and therfore more data can be transfered in less time so your ubuntu installation can not take advantage of this small performance trick. 

It's always good the have more RAM which acts as a buffer and you can try to tune some settings to something like:

vm.dirty_ratio = # set them to 80
vm.dirty_background_ratio =  # set them to 50

are to knobs which can be tuned. You can look at them via sudo sysctl -a | grep vm.dirty_ratio and set a different ratio via:

sudo sysctl vm.dirty_ratio = 80

As usual you will do this on your own risk!!!

---

### Post by Jose Catre-Vandis on 2011-10-19
I run HD video over a 100mb network using nfs and don't suffer any problems with playback whilst doing other things. I use mplayer with a reasonable buffer e.g.

[HTML]mplayer -cache 8192 video.mkv[/HTML]

and have compositing turned off to get rid of the tearing (NVidia card)

So try adding a buffer and see if that helps.

---

### Post by thatguruguy on 2011-10-19
This still sounds like a throughput issue, not a video/compositing issue.  Is your Xubuntu on a separate partition from your Windows installation, or did you install it inside Windows (using Wubi)?

---

### Post by 3rdalbum on 2011-10-19
If the drive you are copying to is NTFS, then yes this would be the issue.

NTFS writing is CPU-bound; it uses up a lot of CPU time on Linux. Obviously, video decoding is also CPU bound.

You could "renice" your video player so it has a higher priority and can use greater chunks of CPU time. Check out Google for details on how to "renice a process".

---

### Post by thatguruguy on 2011-10-19
Yep, it's a [known bug when dealing with NTFS drives]("https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/392204").

Dealing with NTFS drives eats up a lot of cpu cycles, which will negatively impact video performance.

You wouldn't see this issue if both drives were ext4 or another linux-native drive format.

---

### Post by scottbomb on 2011-10-19
> **thatguruguy said:**
> This still sounds like a throughput issue, not a video/compositing issue.  Is your Xubuntu on a separate partition from your Windows installation, or did you install it inside Windows (using Wubi)?

It's in it's own partition, no Wubi. I have 120 GB dedicated to Linux and Windows has 170 GB on a 300 GB drive.

Interesting thoughts on the NTFS compatibility. I will try an experiment with copying a video over to the Linux partition and playing it from there. I will also test reading from NTFS with a larger buffer. I will also get the newer version of VLC (already installed on the laptop - which also dual-boots). I may also try out the mplayer as suggested. I'll report back those findings in a day or two.

Thanks all!

---

### Post by Jose Catre-Vandis on 2011-10-20
I also run HD video off an ntfs partition with no problems, so would it have to be a separate HDD to cause these problems?

---

### Post by thatguruguy on 2011-10-20
> **Jose Catre-Vandis said:**
> I also run HD video off an ntfs partition with no problems, so would it have to be a separate HDD to cause these problems?

No, it's trying to run HD video off an NTFS partition while moving a large (3 GB, according to the OP) file from one NTFS partition to another NTFS partition.

---

### Post by scottbomb on 2011-10-20
> **thatguruguy said:**
> No, it's trying to run HD video off an NTFS partition while moving a large (3 GB, according to the OP) file from one NTFS partition to another NTFS partition.

Technically, I was watching video off an NTFS partition on one drive while transferring a large file to that same drive from a Linux parition on a different drive. I don't know if that makes any difference but I thought I'd throw that out there.

---

### Post by andrew.46 on 2011-10-20
> **Jose Catre-Vandis said:**
> I use mplayer with a reasonable buffer e.g.

```
mplayer -cache 8192 video.mkv
```

It is perhaps 'gilding the lily' but you may notice that by default initially MPlayer does not actually fully load this cache. You can manipulate the loading by adding:

```
mplayer -cache 8192 *-cache-min 80* video.mkv
```

Just a very small point :).

---

### Post by Jose Catre-Vandis on 2011-10-20
> **andrew.46 said:**
> it is perhaps 'gilding the lily' but you may notice that by default initially mplayer does not actually fully load this cache. You can manipulate the loading by adding:

```
mplayer -cache 8192 *-cache-min 80* video.mkv
```

just a very small point :).

Very good Andrew =D>

---

### Post by scottbomb on 2011-10-24
I copied a video to the Linux system partition and tried the experiment. I started the video and then began the file transfer. Video became unplayable.

Oh and the new version of VLC is still buggy. It seemed to be working fine for several Star Trek episodes until tonight. Sound cut out at 7:12. But that's another subject....

I will try mplayer with some of the buffer suggestions made in this thread and see what happens.

---

