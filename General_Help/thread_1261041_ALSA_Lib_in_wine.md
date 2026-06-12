---
title: "ALSA Lib in wine"
date: 2009-09-08
forum: General Help
---

### Post by slapnutz on 2009-09-08
I get the following error when I start winecfg (or any wine app):

ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

I know that questions have been asked about this before, but I figured out my work around, I just need to restart X.

My question is, is there a way to make it "recheck" or reinitialize something like that so that I don't need to logout?

I've tried sudo /etc/init.d alsa-utils restart but that didn't work

Thanks,
~Mike

---

