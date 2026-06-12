---
title: "Keyboard errors every 5 seconds"
date: 2011-02-27
forum: General Help
---

### Post by bbzbryce on 2011-02-27
I helped my nine year old brother install ubuntu 10.10 over the phone on an old Sony Vaio VGC-V617G 17" TV-PC. I'm pretty certain, at this point, that we wont be able to get the tuner card to work, however I wanted to resolve this issue that's flooding the syslog.

Every 5 seconds the following errors appear. Given the periodic pattern I suspect this isn't related to a key being pressed, thus I really have no idea as to what's wrong.

Below is the output containing the errors for two rounds of the errors. All rounds are identical except for the time stamp.

```

Feb 27 14:41:05 bob kernel: [ 3546.532014] kbd_keycode: 130 callbacks suppressed
Feb 27 14:41:05 bob kernel: [ 3546.532019] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.568016] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.604018] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.640033] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.676022] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.712021] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.748016] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.784018] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.820014] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.856014] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.576011] kbd_keycode: 130 callbacks suppressed
Feb 27 14:41:10 bob kernel: [ 3551.576015] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.612012] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.648018] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.684011] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.720009] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.756016] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.792010] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.828011] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.865462] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:11 bob kernel: [ 3551.904031] keyboard: can't emulate rawmode for keycode 240

```

---

### Post by Krytarik on 2011-02-27
Did you notice this one!? I really suspect that one key is defect. And he should check what "Keyboard model" is set in "System -> Preferences -> Keyboard -> Layouts".
> **bbzbryce said:**
> 
```

[COLOR=Red] Feb 27 14:41:05 bob kernel: [ 3546.532014] kbd_keycode: 130 callbacks suppressed
[/COLOR]Feb 27 14:41:05 bob kernel: [ 3546.532019] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.568016] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.604018] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.640033] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.676022] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.712021] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.748016] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.784018] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.820014] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:05 bob kernel: [ 3546.856014] keyboard: can't emulate rawmode for keycode 240
[COLOR=Red] Feb 27 14:41:10 bob kernel: [ 3551.576011] kbd_keycode: 130 callbacks suppressed
[/COLOR]Feb 27 14:41:10 bob kernel: [ 3551.576015] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.612012] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.648018] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.684011] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.720009] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.756016] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.792010] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.828011] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:10 bob kernel: [ 3551.865462] keyboard: can't emulate rawmode for keycode 240
Feb 27 14:41:11 bob kernel: [ 3551.904031] keyboard: can't emulate rawmode for keycode 240

```

---

### Post by bbzbryce on 2011-02-28
> **Krytarik said:**
> Did you notice this one!? I really suspect that one key is defect. And he should check what "Keyboard model" is set in "System -> Preferences -> Keyboard -> Layouts".

I noticed this when going through the logs to track down the tuner card issue. The keyboard layout he selected is the default United States / USA layout. I'll have him unplug his keyboard and see if the problem temporarily goes away.

---

### Post by Krytarik on 2011-02-28
> **bbzbryce said:**
> I noticed this when going through the logs to track down the tuner card issue. The keyboard layout he selected is the default United States / USA layout. I'll have him unplug his keyboard and see if the problem temporarily goes away.
I mean especially this one:
>  **Feb 27 14:41:05 bob kernel: [ 3546.532014] kbd_keycode: 130 callbacks suppressed** You should check especially the selected "Keyboard model", as I said.

---

### Post by bbzbryce on 2011-03-02
> **Krytarik said:**
> I mean especially this one:
You should check especially the selected "Keyboard model", as I said.

It's the generic 105-key keyboard. Also it seems at this time, the problem has resolved itself. I'm not sure what to make of that however.

---

### Post by filbo on 2011-10-19
These messages were being emitted every ~0.036 seconds.  They are throttled in the kernel; after allowing 10 of them through, the throttling holds subsequent messages for 5 seconds.  5s / 0.036s = 139, which is approximately how many it shows were suppressed every 5s.

So basically you're looking at a continuous stream of keycode 240 every 0.36s.

<linux/input.h> has:

   #define KEY_UNKNOWN 240

which isn't entirely helpful... just tells us this is an unknown key according to some other input layer.

Anyway.  Given the description of this as a "TV-PC", I would guess that this stream of unknown inputs was coming from a remote control.  Specifically, someone (or a book or whatever) was probably sitting on a key of the remote which auto-repeats (like Vol-Up).

It was then fixed by either (1) remote not being sat on any more, or (2) you installed lirc or something similar, which jiggered the translations to make that key recognizable.

>Bela<

---

