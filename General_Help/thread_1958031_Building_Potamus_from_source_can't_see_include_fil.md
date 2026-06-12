---
title: "Building Potamus from source can't see include files"
date: 2012-04-13
forum: General Help
---

### Post by ssj71 on 2012-04-13
Hi All,

I'm trying to build Potamus from source since its not in the oneric repositories. I'm running Xubuntu Oneric. I have all the dependencies up to date (./configure runs without error). My problem is when I try to make it gives several errors such as "potamus-0.12/src/input-flac.c:165: undefined reference to `FLAC__stream_decoder_process_single'" all from the flac libraries.

 I have libflac-dev up to date and I can see the declarations of these in user/include/FLAC/stream_decoder.h which is included in the c file in question. Its just that make can't see the declarations. Do I need to add something to the build path or something like that? I don't know how so any advice would be helpful. Thank you!

_ssj71

---

### Post by ssj71 on 2012-04-14
Update: I have even copied stream_decoder.h into the src directory and it still returns the same errors. I suspect then that its a library issue? Any help would be nice. Thanks.
_ssj71

---

### Post by mikodo on 2012-12-09
Too bad about this nice app!

I have it in Ubuntu 10.04 nice, no frills and light.

Isn't available for my Xubuntu 12.04. I have been using minirok, light (has a demon that runs though), Potamas doesn't, just drag music files from tree for it. . . I miss it.

---

