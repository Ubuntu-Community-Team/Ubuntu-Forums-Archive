---
title: "No sound on line-out, speakers work"
date: 2010-05-19
forum: General Help
---

### Post by Rackstar on 2010-05-19
Hi,

I just bought a new Dell Studio 15. It's not such an easy ride with Lucid apparently, the broadcom wireless driver sometimes fails, and there is no sign of any bluetooth on ubuntu.

But the main annoyance at the moment is that no sound is coming through the line-out.

When I plug my headphones in, the speakers go silent as they are supposed to do. But I can't hear anything in my headphone. 

I do have two headphone-line-outs on this laptop, but it's the same effect on both.

Does anyone have an idea? I searched the forum, tried installing gnome alsa mixer, but everything seems to be unmuted.

As I am a musician, this is a big annoyance...

Thanks for reading my post!

Ruben

---

### Post by jsstn on 2010-05-19
try looking at this page:
[http://www.linlap.com/wiki/dell+studio+15](http://www.linlap.com/wiki/dell+studio+15)

about halfway down, James/Subject-17 says that, > To get sound working, add &#8220;options snd-hda-intel model=dell-m6&#8221; to your  /etc/modprobe.d/modprobe.conf and /etc/modprobe.d/alsa-base.conf (no  quotes, create the files if they don't exist)

---

### Post by aphatak on 2010-05-19
When you plug the headphones jack in, the physical connection to the PC speakers is broken.  So speakers going silent will always work.  However, the Gnome default sound behavior will keep only one sound output alive at a time.  I suggest you go System -> Preferences -> Sound, select the Output tab, and make sure (a) the appropriate output is selected, and (b) the output volume slider is not set too far to the left (see attached screenshot).  Sometimes the default volume setting can be mute.  Update the post if this doesn't work; we can look someplace else then.

---

### Post by Rackstar on 2010-05-19
> **jsstn said:**
> try looking at this page:
[http://www.linlap.com/wiki/dell+studio+15](http://www.linlap.com/wiki/dell+studio+15)

about halfway down, James/Subject-17 says that,

Wow!

This fixed the problem for me! Thanks!

I'll file a bugreport tonight

Thanks both for the fast responses

---

### Post by AshRice on 2010-05-19
I have a studio 1747 with the same issue (interestingly my Bluetooth worked out of the box. I think they are essentially the same hardware...). Anyway jsstn I tried that a few weeks back and it caused my speakers to fail completely. 

Aphatak, I've tried that too and it's not the issue (at least with my laptop).

Any more suggestions??????

---

### Post by AshRice on 2010-05-19
> **AshRice said:**
> I have a studio 1747 with the same issue (interestingly my Bluetooth worked out of the box. I think they are essentially the same hardware...). Anyway jsstn I tried that a few weeks back and it caused my speakers to fail completely. 

Aphatak, I've tried that too and it's not the issue (at least with my laptop).

Any more suggestions??????

Well, I just tried it again because of the success and it definitely failed. The gnome audio manager thingy fails to acknowledge the existence of my speakers at all now.

---

### Post by AshRice on 2010-05-19
> **AshRice said:**
> I have a studio 1747 with the same issue (interestingly my Bluetooth worked out of the box. I think they are essentially the same hardware...). Anyway jsstn I tried that a few weeks back and it caused my speakers to fail completely. 

Aphatak, I've tried that too and it's not the issue (at least with my laptop).

Any more suggestions??????

Well, I just tried it again because of the success and it definitely failed. The gnome audio manager thingy fails to acknowledge the existence of my speakers at all now.

---

### Post by AshRice on 2010-05-19
> **AshRice said:**
> I have a studio 1747 with the same issue (interestingly my Bluetooth worked out of the box. I think they are essentially the same hardware...). Anyway jsstn I tried that a few weeks back and it caused my speakers to fail completely. 

Aphatak, I've tried that too and it's not the issue (at least with my laptop).

Any more suggestions??????

Well, I tried it again just to be sure and it did not work. To be clear, I am definitely having the same problem as listed here, and not the problem where the speakers dont turn off but the headphones work. Is there something different about the studio 17 over the 15?

---

### Post by AshRice on 2010-05-19
> **AshRice said:**
> I have a studio 1747 with the same issue (interestingly my Bluetooth worked out of the box. I think they are essentially the same hardware...). Anyway jsstn I tried that a few weeks back and it caused my speakers to fail completely. 

Aphatak, I've tried that too and it's not the issue (at least with my laptop).

Any more suggestions??????

Well, I tried it again just to be sure and it did not work. To be clear, I am definitely having the same problem as listed here, and not the problem where the speakers dont turn off but the headphones work. Is there something different about the studio 17 over the 15?

---

### Post by AshRice on 2010-05-19
Well, I tried it again just to be sure and it did not work. To be clear, I am definitely having the same problem as listed here, and not the problem where the speakers dont turn off but the headphones work. Is there something different about the studio 17 over the 15?

---

### Post by AshRice on 2010-05-19
WOW, I'm sorry about that..... I thought it wasn't working.

---

### Post by AshRice on 2010-05-19
WOW, I'm sorry about that..... I thought it wasn't working.

---

