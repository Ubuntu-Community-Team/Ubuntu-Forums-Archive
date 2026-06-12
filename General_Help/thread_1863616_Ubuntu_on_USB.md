---
title: "Ubuntu on USB"
date: 2011-10-18
forum: General Help
---

### Post by AZBoy28 on 2011-10-18
Hey.

After unsuccessfully installing Chrome OS on my USB, I decided I wanted to install Ubuntu on my USB stick.

However my question is, can I install Ubuntu on my USB so it isn't running under trial mode, eg.. so it could save my settings just like a OS installed on a computer.

OR isn't this possible.

If this isn't possible is there another Linux OS that can accomplish this. My idea is to have a OS on my spare 2GB USB that I can take everywhere with my settings, documments, programs etc..

Thanks =)

---

### Post by AZBoy28 on 2011-10-18
UPDATE:

Thanks,

I found a YouTube video, Is this what you mean?


[http://www.youtube.com/watch?v=VHRz8Ab0PeY&feature=related](http://www.youtube.com/watch?v=VHRz8Ab0PeY&feature=related)


Would this work on a 2GB USB Stick (1.88GB)?

---

### Post by Grenage on 2011-10-18
You can simply install Ubuntu by booting from the CD and selecting the USB drive as the install destination; it really is that simple.  Make sure that the bootloader (grub) is also installed to the USB drive.

2GB is too small, you'll need a bigger drive.

---

### Post by varunendra on 2011-10-19
> **Grenage said:**
> 2GB is too small, you'll need a bigger drive.
It is small for a full installation, but is good enough for a Live setup. Besides, it is easier and safer (no chance of grub confusion) than a full install - especially for a new user. The only drawback would be lack of kernel updates, but the OP only wants to use it in trial mode.

@AZBoy28,
If you have a larger USB drive, a full install on it would be better for long-term use. But if you rather want to use that 2GB USb drive, go with live installation (using either inbuilt "Startup Disk Creator", or "Unetbootin").


**_EDIT_:**
Apologies to *Grenage *for my BIG MISTAKE. I read "[COLOR=Red]**isn't**[/COLOR] running under trial mode..." as - "[COLOR=Red]**is**[/COLOR] running under trial mode" in the first post.

---

### Post by haqking on 2011-10-19
> **Grenage said:**
> You can simply install Ubuntu by booting from the CD and selecting the USB drive as the install destination; it really is that simple.  Make sure that the bootloader (grub) is also installed to the USB drive.

2GB is too small, you'll need a bigger drive.

I have 11.10 running with persistence from a 2GB USB Drive.

Too small for full install of course though

---

### Post by Grenage on 2011-10-19
Indeed, I was merely making an assumption based on the initial post, as they said that they didn't want a Live/trial install, but desired a "USB that I can take everywhere with my settings, documents, programs etc"

---

### Post by haqking on 2011-10-19
> **Grenage said:**
> Indeed, I was merely making an assumption based on the initial post, as they said that they didn't want a Live/trial install, but desired a "USB that I can take everywhere with my settings, documents, programs etc"

Yeah i was just about to edit my post actually as i re-read what you said, i took it differently the first time ;-)

I will leave it anyways so the OP knows 2GB will be fine depending on what they want to do.

Cheers

---

### Post by varunendra on 2011-10-21
My apologies to *Grenage*. I misread the "isn't" part in the first post. Included the correction as 'Edit' in my previous post, but left the earlier description as information about the 'optional choice'. Sorry for the mistake again.

---

