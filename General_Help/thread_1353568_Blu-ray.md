---
title: "Blu-ray"
date: 2009-12-12
forum: General Help
---

### Post by hantechbl on 2009-12-12
Is there a bluray software for linux.  Can it read bluray discs? Can it play bluray movies?

---

### Post by justin_guerin on 2009-12-12
I am not aware of any licensed Blu-ray software for Linux, so you'll have to follow the instructions here:
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

Justin

---

### Post by 3rdalbum on 2009-12-12
DumpHD and MakeMKV Beta can remove the encryption and protection schemes and leave you with a file that can be played in Mplayer.

DumpHD relies on stolen decryption keys and only works on discs from 2008 and earlier (because all the stolen keys get revoked by the AACS organisation). MakeMKV uses a stolen key that has not been revoked yet, and it's a bit easier to use too, so it should work on most discs.

I highly recommend upgrading to 9.10 if you want to rip and play Blu-ray discs, because I know that Mplayer in 9.10 has everything you need to play the decrypted files (except for some newer discs, but you can compile your own Mplayer if you encounter any of those).

I wrote a large amount of that "Decrypting HDDVD/Bluray" guide so if you have any questions, please PM me as well as asking on this forum.

---

