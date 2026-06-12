---
title: "Need Gtick sound device"
date: 2011-01-11
forum: General Help
---

### Post by Ubunthree on 2011-01-11
I am trying to get the Gtick metronome to work, and the advice that I've found on other threads hasn't helped so far. Gtick gives me the error:

[COLOR="DarkRed"]Couldn't start metronome.
Please check if specified sound device
and sample file are accessible.[/COLOR]

Things I've tried so far:

Installed alsa-oss, started Gtick with [COLOR="DarkRed"]aoss gtick[/COLOR] (same error).

Started Gtick with [COLOR="DarkRed"]padsp gtick[/COLOR] (same error; pulseaudio-utils is installed)

The default sound device shown in Gtick's preferences is [COLOR="DarkRed"]/dev/dsp[/COLOR]. There is nothing in my /dev directory with "dsp" in its name. How do I determine what existing alternative to use, or install what Gtick needs?

I have tried using the [COLOR="DarkRed"]sine[/COLOR] option as well as my own tick sound, in case it was a problem with the default sound, to no effect.

Sound in general seems to work for other applications.

I'm running Mint Julia at the moment, but I assume this would all apply to Maverick as well.

Thanks!

---

