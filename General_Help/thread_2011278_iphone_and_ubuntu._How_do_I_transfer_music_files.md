---
title: "iphone and ubuntu. How do I transfer music files?"
date: 2012-06-26
forum: General Help
---

### Post by bobdobbs on 2012-06-26
I upgraded to 12.04 about 6 weeks ago.

On this new version, I can't transfer mp3's to my iphone.

Rythymbox can't see my iphone.

Banshee can only sometimes see my iphone. And then, it's only been able to see my iphone music collection once.

Currently, banshee sometimes sees my iphone, but when it does it doesn't see any tracks. Attempts to write files to the iphone fail. The errors say something about not being able to write mp3's

(Sorry, I can't get the actual error messages at the moment, because banshee is going through it's "screw you, I'm not acknowledging the presence of your iphone" phase)


Is there a way under 12.04 to consistantly and reliably be able to do this:

* Upon plugging my iphone in, I'd like the iphone to be detected by a tool that I can use to transfer music files between the OS and the iphone.

---

### Post by bobdobbs on 2012-06-27
bump

---

### Post by ron999 on 2012-06-27
> **bobdobbs said:**
> bump
Hi
The latest version of **gtkpod** compiled from GIT is OK, though I haven't used it with an iPhone.

It's easy enough to compile from GIT with 12.04.
I still have the commands if you're interested.

---

### Post by bobdobbs on 2012-06-27
Hey Ron.

That's an idea that I'll keep in mind. 

But at the moment, I think that there might be a problem, probably with an underlying library, that I should fix before I install anything that might replace the default libraries.

Just before I got your message, I installed and ran gtkpod from the standard repo's. It didn't pick up my iphone.

I decided to give something else a shot: I rebooted. Then I ran banshee. Then I plugged the iphone in. Banshee didn't see the iphone.

I then unplugged the phone, kill9'd banshee, started rhythymbox, and plugged the iphone in. Again, no device registration by rhythmbox.

It occoured to me that nautilus has always picked up the device. So just for the sake of testing, I started nautilus.

Nautilus did indeed pick up the phone. It could see it, and it could see it as an iphone. It's jailbroken, so nautilus could see it's files.

Nautilus also gave me a message. Something along the lines of "this device contains music files. Open in a media player?", and gave me the option of opening the device with either bansee or rhythmbox. I chose rhythmbox.

From that point, rhythmbox could see the iphone and it's music collection. I decided to test things by transferring mp3's to the device. The operation seems to have been successful.


[CENTER]---------------------[/CENTER]

So, it seems that for the moment I've got a way to access the iphone and it's media collection. 

It's much less then ideal. But it works.

So now I'm curious: what could be going on here?

This might be a bug in something. But I'm not sure which program or process is the origen of this bug.

---

### Post by bobdobbs on 2012-06-28
The above method no longer works.

This is really frustrating: the behaviour of rhythymbox and banshee is completely unpredictable with the iphone.

That's painful enough. But now files won't transfer across at all.

What is happening here? And how can I set things up so that I can transfer music files reliably?

---

### Post by bobdobbs on 2012-07-01
bump

---

### Post by ajukilibodin on 2012-08-29
I'll bump this. My iPhone is recognised and KDE offers me to open it with photo managers. But Rhythmbox, Banshee and Amarok have no idea about the presence of an iPhone.

[EDIT]

gtkpod failed to recognise the device as well :/

---

### Post by ajukilibodin on 2012-08-29
Ok, that was under MINT on my laptop. With Ubuntu, iPhone doesn't get recognised at all. Under VirtualBox. "No USB devices connected"

lsusb returns

Bus 001 Device 006: ID 05ac:1297 Apple, Inc. iPhone 4

which is good. But can not mount it :/ Any ideas?

---

### Post by jdi1312 on 2013-06-25
bump!

---

### Post by oldos2er on 2013-06-25
Hi jdi1312, rather than bumping a year old thread, I think you'd get more response if you start a new thread.

---

### Post by ZPC2THLgate on 2013-06-29
It now bypasses Grub and goes straight in to Windows.

---

### Post by oldos2er on 2013-06-29
ZPC2THLgate, if you're asking for support please start a new thread (the Absolute Beginners section would be a good place) and give as many details about your problem as possible.

Old thread closed.

---

