---
title: "Palm Pre media sync"
date: 2009-09-09
forum: General Help
---

### Post by loupy on 2009-09-09
I have a Palm Pre and am using 9.04 32 bit.  I can see my Pre from Banshee and Rhythmbox however neither lets me add new media or playlists to it.

I know I can also do a USB attach and add files - but that does not allow for playlists which I need.  So far only YamiPod will allow for all the syncing I need - but I'm not too crazy about the interface.

Anyone have a Palm Pre fully syncing with Banshee or Rhythmbox?

---

### Post by mlissner on 2009-09-17
I plugged my pre into my computer via USB, hit the button on the pre to "sync media" or something like that, and then it crashed banshee...which sucked.

But I restarted banshee a moment later, and it's working fine now. I think banshee thinks it's an ipod named "Palm Pre," but I think that's fine...

---

### Post by HeresJohnny on 2009-11-02
Hi! I had no problem syncing my Pre using Rhythmbox.  A couple of caveats, though:
1. I don't use iTunes in any form, shape, or fashion.  I have heard that some folks have had trouble syncing if they used iTunes first and then tried to use a Linux program- doesn't seem to matter what program.
2. Before syncing, it's a good idea to make sure your program (I used Rhythmbox, didn't really try with Banshee or the-Amarok-which-shall-not-be-named) has an iPod manager plugin activated.  The Pre seemingly identifies itself as an iPod, regardless of which OS you use, so an MTP player controller, for example, might not work.  I connected using 'media sync' settings.

I did notice a couple of things:  having those things set up, all I did was drag songs over to the Pre and they were copied, album art and everything.  Didn't try doing a playlist, I was just trying more or less on a lark.  I had created a music folder on the Pre for my bible study stuff (and that was copied over in USB mode), but the music I copied over using Rhythmbox was housed instead in a hidden folder named iPod_Control.  You should be able to see this by browsing to your Pre using Nautilus and using control-H to view hidden files/folders.  Inside that folder, there are five folders:  Artwork, Device, iTunes, Music, and .gnupod.  Each song is given its own folder within 'Music', and I'm not at all sure what the other folders do (except maybe Artwork).

I hope this helps all the other Pre owners out there.  I have 9.10 64-bit, so maybe they have changed Rhythmbox or some of the protocols to work better with the Pre.  But on second thought, you'd think that could be changed just as easily with an update?

---

### Post by Ingenium on 2009-11-18
I'm having the same issue. It actually worked fine for me in Rhythmbox in 9.04, which I used to transfer all my music, however my Pre now shows up completely blank in Rhythmbox in 9.10. Browsing into the iPod_Control folder on the Pre shows everything is there.  Interestingly, Amarok works perfectly with it. I've copied new music onto it from Amarok now, and it still is showing up as blank in Rhythmbox.

---

### Post by Tetenterre on 2010-04-11
> **loupy said:**
> I have a Palm Pre and am using 9.04 32 bit.  I can see my Pre from Banshee and Rhythmbox however neither lets me add new media or playlists to it.

My playlist workaround is this:

My music is stored in a directory called "Music" on my computer. I copied this over to my Pre in USB mode.

I use RhythmBox to create playlists from the music; save in the Music directory in M3U format. Copy these M3U files to the Music directory on the Pre. (If you save anywhere else, you will need to edit them in Text Editor so that the path from the Pre Music folder is correct.)

Works for Music Player and the far better Music Player Remix.

If you have previously used RhythmBox to install music, you must use it again to remove it, otherwise you will find that Music Player Remix points to duplicate empty files.

---

