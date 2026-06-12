---
title: "Is Linux instable?"
date: 2010-05-12
forum: General Help
---

### Post by florianr on 2010-05-12
Hello!

I have a very strange Situation ... 
I had a Fujitsu Esprimo mobile Notebook runing with fedora before. I recognized intermittent system crashes. I was not able to find a single Software or any other action 

which caused this crashes. The crashes made the system freeze, what means that the display was still showing my Desktop but the system didn't give me response to any action. No mouse movement, no shutdown on ACPI Event, No Alt-Strg-Entf and so on. Also pressing the Caps-Lock or Num-Lock made no LED Sign. Regular I found no entry in messages, the log finaly just stopped working. Installing a linux mint system on this notebook made no difference. 

All investigations on this issue were not successful. I made a Memtest without result.

So I decided to by a new notebook, a HP ProBook 6460b. There I made a fresh install of Ubuntu 10.04. Can you imagine my surprise when the same things happened there? I still have the same crashes. They happen when I use Open Office ore firefox ore any other software. Memtest also without result. I did not connect any additional hardware to my notebook. I also found no relevant entry in the log:

The freeze happend at 13:15
```
May 12 12:48:47 florian-laptop pulseaudio[2070]: ratelimit.c: 2 events suppressed
May 12 12:48:52 florian-laptop kernel: [13812.439678] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
May 12 13:16:47 florian-laptop kernel: [15484.003422] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
May 12 13:16:47 florian-laptop kernel: [15484.003427] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.

```The "Unknown key pressed" entry was was caused by pressing the Mail button on top of my notebooks keyboard **after the freeze!** Interesting that this event was recognized and logged. I can't imagine that skype has to do with it. These freezes also happened before I installed the skype software.


Any ideas for further diagnosis will be  welcome.

I can't imagine that this is a general Linux issue ... but appearing on verry different hardware makes me wonder.

Btw. for now I use the 64bit Version of Ubuntu. Before I used 32bit Versions of fedora an mint. 

Kind regards

Florian

---

