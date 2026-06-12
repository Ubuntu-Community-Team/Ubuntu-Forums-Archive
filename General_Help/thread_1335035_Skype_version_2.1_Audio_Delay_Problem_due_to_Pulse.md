---
title: "Skype version 2.1: Audio Delay Problem due to Pulse on Karmic 64bit"
date: 2009-11-23
forum: General Help
---

### Post by cmfrtblynmb on 2009-11-23
Hello all

I know there are a bunch of threads about skype but I would like to make it more specific it to Ubuntu 9.10 64 bit

Like a lot of people has experienced, Skype's support for linux really sucks and they still have not done anything on pulse audio bug.

When you try to use pulse audio system, you get a delay while talking to other party on skype. this gap is small at the beginning, but then it gets bigger.

On 9.04 I solved this problem by installing alsa drivers and use them for skype.

But with 9.10 and Skype 2.1, you can not choose anything other than pulse as the sound driver for skype.

I saw people solving this problem by downgrading their skype version, they say you can choose whatever sound driver you want on skype 2.0.

Here is the link for skype 2.0 on 32 bit systems:

[http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb](http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb)

My problem is I can not find amd64 version of skype 2.0. And skype does not provide links for old versions (another gesture of great support!) Probably they just forget this one there on the servers

Does anyone has a solution for this? How can I make skype use alsa? Is there anything I should install? Or does anyone have the download link for the good old 64 bit skype 2.0?

---

### Post by cmfrtblynmb on 2009-11-23
by the way I just found this one:

[http://share.skype.com/sites/linux/2009/09/some_explanations.html](http://share.skype.com/sites/linux/2009/09/some_explanations.html)

I will try the part with configuring pulse audio settings and then I'll let you know the results

---

### Post by cmfrtblynmb on 2009-11-24
OK, here is the temporary solution I have found so far

```
sudo killall -9 pulseaudio
```

This will stop pulse audio. It is a good idea to have skype off when running this. Then skype will run on good old alsa.

Afterwards you can start pulseaudio by just typing ```
pulseaudio &
``` on terminal

Though this is a temporary solution, I will mark this thread as solved.

---

