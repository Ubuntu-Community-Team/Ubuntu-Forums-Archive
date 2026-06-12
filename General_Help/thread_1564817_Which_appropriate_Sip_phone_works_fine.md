---
title: "Which appropriate Sip phone works fine ??"
date: 2010-08-31
forum: General Help
---

### Post by idsoft on 2010-08-31
Hello everybody,

Which Sip Phone works Fine on Ubuntu  10.04?? I've tried Zoiper but It's unstable.. I often  have problem with the sound configuration or at times whenever i make a call, the correspondent at the end of line doesn't hear me..  I need One which work perfectly in a call centre environment.. Can Anyone help Please???

---

### Post by lolzywut on 2010-08-31
I don't know.

---

### Post by gradinaruvasile on 2010-08-31
> **idsoft said:**
> Hello everybody,

Which Sip Phone works Fine on Ubuntu  10.04?? I've tried Zoiper but It's unstable.. I often  have problem with the sound configuration or at times whenever i make a call, the correspondent at the end of line doesn't hear me..  I need One which work perfectly in a call centre environment.. Can Anyone help Please???

Zoiper doesnt play well with PulseAudio. On ALSA its perfect.
Other sip phones:

Sflphone - very good routing - make sure you check the interfaces in the advanced settings for the sip account; Has call encryption via zrtp (not all providers support encryption);
Sip Communicator - might be unstable, it is in heavy development, but has excellent SIP routing when it works, zrtp call encryption, audio/video and tons of supported protocols yahoo, gtalk/jabber etc);
Linphone - very good routing, a bit confusing setup and no call forward/conference/recording, very good sound quality;
Ekiga - this has some routing problems so you might end up not hearing the other sometimes.

---

### Post by idsoft on 2010-08-31
Ok I'll try Sfl phone...
But for Zoiper With Alsa... It's the same It gets conflict with Pulse.. N if u have a PCI sound card it just don't detect the sound card.. But i tried it with the onboard sound card.. Still having probs with Zoiper..

---

