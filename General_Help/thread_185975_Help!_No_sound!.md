---
title: "Help! No sound!"
date: 2006-06-01
forum: General Help
---

### Post by drinkingmouse on 2006-06-01
Can anyone help me?

There is no sound coming out from my speaker...
My sound card is Creative Vibra 128...
Please help me! THank you...

---

### Post by Estariel on 2006-06-01
Hi!
Let's check whether your soundcard got detected, all channels are unmuted, and the volume is turned up.

Please open a Terminal/Konsole/Shell/whatever-you-use and do the following

```

alsamixer

```

A program will start (within the shell) that displays on the top left name and chip of the detected soundcard. Please post here what it displays.

It also displays all channels, and whether the are turned up and unmuted.
If a channel is muted, it reads "MM", and you can unmute it by hitting the "m" button on the keyboard. You can navigate through the channels by the arrow keys on the keyboard. If one is set to "0" (not turned up) turn it on by using the "up-arrow"-key.

Let me know whether this helped.

---

### Post by drinkingmouse on 2006-06-01
Thank You.

I saw the display and then push all to the highest.
The centre was muted, so I unmuted it by pressing "m"

Still, no sound comes out.

---

