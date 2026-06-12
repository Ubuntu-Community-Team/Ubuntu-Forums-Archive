---
title: "nano and line wrapping"
date: 2010-01-27
forum: General Help
---

### Post by llamabr on 2010-01-27
I'm having a strange problem that I can't seem to fix.  I'm running a pretty fresh install of 9.10.  When I type a document in nano, the lines do not wrap when I get to the end of the page.  That is, once I've typed a very long line, and I reach the right edge of the screen, the text does not drop down to the next line.  Instead, it continues along the very first line, indicating a long line with the $ character.  I understand that this environment is described as 'wrapping off'.

I'd like to turn wrapping on.  If I've mixed those, please advise.

According to the man page, I should be able to set the line wrap with the -r flag, but this does not help.  The man page also suggests that I can toggle it with alt-l.  I press this, and am told that wrapping is enable and disabled, but it does not change the behavior.

I'm running nano 2.0.9.  This is not the most recent version, but it is the stable version as of my last apt-get upgrade.  I'd prefer not to go outside of the distro, if possible.

I'd appreciate any advice.  In addition, could anyone else test this behavior on your own system and either confirm or deny?

Thank you.

---

### Post by llamabr on 2010-01-27
Hmm.  I just compiled the tarball, and am now running 2.2.2.  Still, this does not solve my problems.

---

### Post by MilesTails on 2010-01-28
Hmmm I just tried and I have the same problem. I looked in .bashrc to see if maybe there was an alias but no luck. 

Is there a second place that ubuntu stores aliases that i'm not aware of?

---

### Post by llamabr on 2010-01-28
I don't have any aliases set.  You can set them in several places, though .bashrc is the place where they ought to go.

But in any case, even if you had an alias set, you could overwrite it with the -w flag.  Or with alt-l from within nano.  Neither of which works for me.

---

### Post by llamabr on 2010-01-30
bump

---

