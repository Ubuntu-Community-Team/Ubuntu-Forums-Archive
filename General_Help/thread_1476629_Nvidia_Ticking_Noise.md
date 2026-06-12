---
title: "Nvidia Ticking Noise"
date: 2010-05-08
forum: General Help
---

### Post by timhaughton on 2010-05-08
I've just enabled the NVidia driver - mainly to get dual monitor support - and I've got this insanely irritating ticking noise which happens exactly once per second. Muting the sound has no effect.

Any way to fix it? It might seem minor, but it's a game-over bug for me.

---

### Post by soltanis on 2010-05-08
Mind listening to your computer to tell us where it's coming from?

The usual culprit of ticking noises is the hard drive. Are you sure this happened only after you installed the graphics driver? Perhaps you can try doing this:

```

sudo watch 'smartctl -a /dev/sda | grep Load'

```

In a terminal. Check to see if the number on the end of "Load_Cycle_Count" is increasing with the number of ticks you hear (the command will update on the screen every 2 secs).

The line looks like this:
```

193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always
  -       409

```

You want the very last number on the end.

If you don't have smartctl you should do:

```

sudo apt-get install smartmontools

```

To install it.

---

### Post by timhaughton on 2010-05-08
Ha, sorry it was obvious to me at the time, not so much when I read it back :)

The ticking sound is coming from the speakers on my main monitor. It doesn't appear to be dependent on any kind of activity (graphical or otherwise) - it's almost like there's a bomb in my monitor! :) Every 1 second....tick....tick....tick

---

### Post by soltanis on 2010-05-08
If your monitor has integrated speakers, then try unplugging the sound cable and see if that helps. If it doesn't, then it could be either a screwy signal coming from your display cable that's causing the ticking noise or a poorly built monitor with audio cabling not well-enough shielded from the display cables.

---

### Post by timhaughton on 2010-05-08
> **soltanis said:**
> If your monitor has integrated speakers, then try unplugging the sound cable and see if that helps. If it doesn't, then it could be either a screwy signal coming from your display cable that's causing the ticking noise or a poorly built monitor with audio cabling not well-enough shielded from the display cables.

Yes it does help. In the sense that there's no sound. But I like sound - just not ticking. Doesn't happen in Windows or Ubuntu in VMWare on Windows.

---

### Post by BenAshton24 on 2010-05-08
Is there still ticking when you use headphones instead of your built in speakers?

This might also help: [http://www.youtube.com/watch?v=Tx1XIm6q4r4]("http://www.youtube.com/watch?v=Tx1XIm6q4r4")

---

### Post by timhaughton on 2010-05-08
> **BenAshton24 said:**
> Is there still ticking when you use headphones instead of your built in speakers?

Yes, but in my headphones.

> **BenAshton24 said:**
> This might also help: [http://www.youtube.com/watch?v=Tx1XIm6q4r4]("http://www.youtube.com/watch?v=Tx1XIm6q4r4")

Have contacted Iiyama who deny any knowledge of any explosives, pipe bombs or otherwise.

---

### Post by Rynor on 2010-05-08
Make sure your line-in channel is muted, if not it can pick up interference and play it back.

---

