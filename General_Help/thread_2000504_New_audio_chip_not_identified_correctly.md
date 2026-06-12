---
title: "New audio chip not identified correctly"
date: 2012-06-09
forum: General Help
---

### Post by MikeB23930 on 2012-06-09
I recently replaced a dead motherboard on my Mythbuntu box and now have no sound.  The relevant portion of the output of lspci is:

lspci | grep Audio
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

The dead motherboard had Intel HDA/NVIDIA audio; the new motherboard has Realtek ACL889 audio.  It appears to me that the system doesn't realize the audio chip has changed.  I suspect I could resolve the sound problem by reinstalling the entire system from scratch, but then I would lose all of the programs I have recorded but not yet watched. 

Can some one walk me through the process of getting the system to correctly identify the new audio chip and load the correct drivers without having to reinstall the system from scratch?

Thanks,

Mike

---

