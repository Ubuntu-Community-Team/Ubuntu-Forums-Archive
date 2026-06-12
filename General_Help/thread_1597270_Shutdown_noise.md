---
title: "Shutdown noise"
date: 2010-10-15
forum: General Help
---

### Post by startling on 2010-10-15
I've just bought a new laptop with Windows 7 installed, so the first thing I did was install Ubuntu 10.04 :)

I noticed that when I shut down from Windows 7 it's a silent process, but when I shut down from Ubuntu there's a clicking or popping sound just before the power goes off. This is worrying because I've had a problem like this before where a hard drive eventually broke because it wasn't shutting down properly.

It's difficult to tell from listening what's making the sound, so is there a way I can diagnose this? Could it be the speakers? Are there log files I could look at to determine if there's a problem?

The laptop is an Advent Modena M200.

---

### Post by mikewhatever on 2010-10-15
I think it's fairly simple if the sound comes from the speakers or from something else. Mute the speakers, shut down. Hear anything?

---

### Post by startling on 2010-10-15
Thanks mikewhatever.

I muted the speakers and shut down. There was still a definite click, so it's not the speakers or sound card.

---

### Post by startling on 2010-10-20
I really don't want to harm my laptop so please could someone tell me if there any log files that would show up anything abnormal at shutdown?

---

### Post by startling on 2010-10-26
Is it okay to bump this thread?

---

### Post by Unfrog on 2010-10-26
Actually I think muting the speakers wouldn't tell you if it was a problem with them. I know because on my laptop the speakers do that even if Ubuntu is muted.

In fact the sound card's settings are not retained after Ubuntu's shutdown. After every reboot the sound level is on the last level W7 left them on, it changes only if I change the sound level in Ubuntu; sometimes that leads to a huge difference in the levels. eg: W7 was on low level, sound is weak, I make it higher in Ubuntu, and BAM! it goes super loud, because Ubuntu was on 80% already, but only updated the level now.

What you could try is muting them on Windows, booting into Ubuntu, then shut it down again. If you hear that noise, it doesn't actually mean it's something else, it could be the speakers.

---

