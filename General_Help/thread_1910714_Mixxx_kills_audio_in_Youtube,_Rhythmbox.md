---
title: "Mixxx kills audio in Youtube, Rhythmbox"
date: 2012-01-17
forum: General Help
---

### Post by iamnigel on 2012-01-17
I'm using the DJ software Mixxx from the repositories. Immediately after I open Mixxx, the sound in Youtube goes out and Rhythmbox's audio stops working. Any help?

---

### Post by marin123 on 2012-01-17
I think it uses Alsa and Alsa can handle only 1 input at a time. It happens to me when I turn on VLC (I configured it to use ALSA).

But that should be useful, because you don't want strange sounds when you're playing music (like skype or IM or window sounds).

You can tell Mixxx to use Pulseaudio but you will get bigger latency and you don't want that when mixing music.

---

### Post by MoreOrLess on 2012-01-17
You should be using JACK for low-latency and multiple sound streams.

---

