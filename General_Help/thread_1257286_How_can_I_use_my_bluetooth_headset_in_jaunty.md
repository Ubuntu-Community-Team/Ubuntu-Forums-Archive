---
title: "How can I use my bluetooth headset in jaunty?"
date: 2009-09-03
forum: General Help
---

### Post by Blackie_Chan on 2009-09-03
I have a Nokia Bluetooth Headset (BH-102) and I will like to use with Skype (using both the headphone and mic part).

The problem I'm having so far is that ubuntu doesn't seem to see my headset. After connecting my bluetooth dongle and pairing my headset. I tried: ```
blackie@ubuntu:~$ cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1985 at irq 17

```

I tried a number of things, including editing ~/.asoundrc as in [Step 2]("http://wiki.bluez.org/wiki/HOWTO/AudioDevices"). Still I can't use the headset in Skype or see it running `cat /proc/asound/cards`. 

I even installed [Blueman]("http://www.blueman-project.org/"), but I don't understand how to use it. When I pair my headset, I see red, green and orange lights come up in the UI, but only for a few seconds. 

Anyhow, what can I do to get my bluetooth headset to be recognized so that I can use it with Skype?

---

### Post by mynyml on 2009-09-03
I'm having the exact same problem, with the exact same bluetooth device. I've been reading about the issue on help.ubuntu.com/community, wiki.bluez.org, etc, but I find the information hard to follow since I have little knowledge of how the sound systems work.

I'm also attempting to use the device with skype. Any help would be greatly appreciated.

---

