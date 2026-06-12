---
title: "Configuring JACK problems with SB Live"
date: 2010-07-01
forum: General Help
---

### Post by HunterGathererDrone on 2010-07-01
Hello. Still a noobie. I've been trying to configure JACK to work with Ardour but I simply cannot get playback nor can I record.  For some reason I get sound from my SB Live card with JACK inactive (music, youtube, etc).  When JACK is active I get playback from my onboard sound.  How do I route JACK so its reading it from my SB Live?

Thanks
Justin

---

### Post by cryptotheslow on 2010-07-02
Applications > Sound & Video > JACK Control

Click Setup...

The top of the right column of options you will see a dropdown box labelled "Interface:" - try changing that from (default) to select your soundcard.

Alternatively disable your onboard sound in your computer's BIOS if you don't use it.

If JACK Control is not in your menu it can be installed via the Ubuntu Software Centre (10.04) or from Synaptic - look for the qjackctl package.

Hope that helps.

---

