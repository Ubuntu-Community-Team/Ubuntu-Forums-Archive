---
title: "UUID of hard drive changed after using Transmission"
date: 2012-10-02
forum: General Help
---

### Post by Ace..... on 2012-10-02
I'm experiencing a problem with my drive unique identifier.
It has created a problem with my grub config - the thread is here:

[http://ubuntuforums.org/showthread.php?p=12274042#post12274042](http://ubuntuforums.org/showthread.php?p=12274042#post12274042)

The question is: what caused the prob in the 1st place.

Everything was running hunky..... the last download I made was the torrent app 'Transmission'.

I figured it was okay as it was part of ubuntu software downloads, and apparently good.

I used it to download:
/home/mark/Videos/Looking_for_Richard/LOOKING_FOR_RICHARD.avi
/home/mark/Videos/PBS Frontline - Much Ado About Something (Did Shakespeare Exist)/PBS Frontline - Much Ado About Something.avi
/home/mark/Videos/PBS Frontline - Much Ado About Something (Did Shakespeare Exist)/PBS Frontline - Much Ado About Something.txt
/home/mark/Videos/PBS Frontline - Much Ado About Something (Did Shakespeare Exist)/PBS Frontline - Much Ado About Something SCREENSHOTS.jpg
/home/mark/Videos/Pioneer.One.S01E01.REDUX.Xvid-VODO/Pioneer.One.S01E01.REDUX.Xvid-VODO.avi
/home/mark/Videos/Pioneer.One.S01E01.REDUX.Xvid-VODO/Support.Pioneer.One_Make.future.episodes.possible!.URL
/home/mark/Videos/Pioneer.One.S01E01.REDUX.Xvid-VODO/vodo.nfo
/home/mark/Videos/Pioneer.One.S01E01.REDUX.Xvid-VODO/Sample/Pioneer.One.S01E01.Xvid.Sample-VODO.avi
/home/mark/Videos/Pioneer.One.S01E01.REDUX.720p.x264-VODO.torrent
/home/mark/Videos/Pioneer.One.S01E01.REDUX.Xvid-VODO.torrent
/home/mark/Downloads/[isoHunt] An ungentlemanly Act.avi.torrent
/home/mark/Downloads/[isoHunt] the_falklands_play_mp4_ac3.avi.5699094.TPB.torrent

At least, that's what I think I downloaded, or attempted to download.

The question is:

Is it possible that, by attempting to download some avi files, I might have been attacked, and downloaded a digital agent that might have modified the hard disk unique identifier?

This I guess requires quite a deep understanding of what is possible.

I only know that everything was running okay until I ran update manager, and I was presented with Configure GRUB-PC informing me that something was wrong.

I had and have not rebooted since downloading transmission and the torrents.

What do you think?

A wierd unfathomable glitch, or an aggressive action?

---

### Post by CharlesA on 2012-10-02
The UUID of your drive shouldn't change at all. I had this update on a couple 12.04 boxes and nothing broke because of it.

As far as I know, you can use tune2fs to change the UUID, but I doubt using a torrent would cause that to run.

Oh and thread title change to more accurately reflect the problem/question.

---

### Post by Ace..... on 2012-10-02
Thanks.... a better title for sure.

If it's unlikely to be transmission, torrents, nor the update itself.... then I'm at a loss.

I wonder if there is a backup copy of the original UUID, so it can be compared to the current UUID.

At the moment, this is a problem thrown up by update manager.
We don't even know if there is an actual fault yet.

---

### Post by CharlesA on 2012-10-02
As far as I know, it would have been listed in fstab, but that would have been replaced when you updated the UUID.

---

### Post by Ace..... on 2012-10-03
Sorry about this but I think this line of enquiry was not correct.
It is now looking like the problem was due to GRUB MBR being written to my USB HD that was disconnected during this last update.

The logic of this is outlined here:

[http://ubuntuforums.org/showthread.php?p=12275081#post12275081](http://ubuntuforums.org/showthread.php?p=12275081#post12275081)

Thanks for the help. :)

---

