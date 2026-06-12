---
title: "Possible bug in gvfsd-gphoto2?"
date: 2009-12-25
forum: General Help
---

### Post by gsumners on 2009-12-25
Greetings!

I'm using Jaunty, and just decided to wipe & reload the music on my Creative Zen Sleek 20GB music player.

The Zen Sleek is perfectly accessible in Nautilus, and apparently auto-mounts using gvfsd-gphoto2 to get to the filesystem.  Therein lies the problem.

Twice, while bulk-copying about 16GB of music, the memory usage would climb to max, then gradually the swap usage climbs towards max, resulting in the GUI wedging solid.  The first time, I didn't notice the progressive nature of the issue; went to the first virtual terminal and killed Nautilus, then went back to the GUI and killed the X session.

The second time, I watched conky's monitors and saw the creeping increase.  It looks like for whatever reason, copying files to the Zen Sleek results in gvfsd-gphoto2 retaining the copied contents in memory, rather than releasing the memory after each file passes through successfully.

To confirm the issue, I incrementally copied files to the Zen Sleek.  The memory and/or swap usage does increase in lockstep with the amount of data copied to the device.  I also noticed that exiting the related Nautilus instances did not result in the memory nor swap being released, but dismounting the Zen Sleek DOES result in the memory and/or swap being released.  This implies that the issue is related to gvfsd-gphoto2, as it unloads on dismount of the device.

Remounting the Zen Sleek shows the files present and valid as copied, and you can repeat the sequence as often as desired - as long as you don't run out of system RAM and swapfile!

I'm on 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux, and all the gvfs-related underpinnings are 1.4.1-0ubuntu1.

Any ideas on if there's a tweak I can apply somewhere, to prevent this?  I don't have a major problem with dis- & re-mounting the device as needed to release the memory & swap, but I shouldn't NEED to do this.

Thanks in advance!

---

### Post by MoarningSun on 2010-01-12
Hi, I have a SanDisk Sansa clip and came across exactly the same issue. I'm on 32-bit Ubuntu also with 2.6.31-17-generic and gvfs version number is the same. In my case my player also didn't recognize the files I put on it when this problem occurred. 

I don't really know if this method is supposed to work to begin with. If gvfsd-gphoto2 is loaded that means your device works in MTP mode. This mode is related to windows media player (see the MTP wikipedia article). For copying files over using Nautilus try setting the device to MSC mode. After I did this I could copy music to my player flawlessly. Note that when in MSC mode, you may not be able to see the files you placed on your device using MTP mode.

When using the MTP mode I could use Rhythmbox to copy music, but only after activating the MTP-plugin in the Rhythmbox settings and applying the fix mentioned here: [http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=2803](http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=2803) This fix may very well be Sansa Clip specific, but just in case you want to check it out.. Carefull, I had to set the device to MSC mode to be able to create the .is_audio_player file! Also some people needed to upgrade their player's firmware before it would work with Ubuntu.

Lastly, I don't know if this issue is a bug or not. There are some gvfs related memory leaks known on Launchpad, but I didn't find this particular one. Maybe you could file one.. maybe I'll do it myself later on :D

---

