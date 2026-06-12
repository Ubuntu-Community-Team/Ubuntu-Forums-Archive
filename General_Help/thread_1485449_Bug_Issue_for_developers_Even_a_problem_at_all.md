---
title: "Bug? Issue for developers? Even a problem at all?"
date: 2010-05-16
forum: General Help
---

### Post by Moozillaaa on 2010-05-16
No, probably not a bug (depending on what OTHER scenarios lead INTO this situation), but it is an end-user created problem that COULD be easier to fix...

I moved some data onto my Karmic install, from another machine on my network. It was too much data. I DID get an error at first, for too much data, so I adjusted to amount to be moved.

Next time I re-booted the Karmic machine, I got an error message, that didn't make clear the problem (of too much data on the partition):


> Install problem!
The configuration defaults for Gnome 
Power Manager have not been 
installed correctly. 
Please contact your computer 
administrator.Huh? There's NO indication that too much data is the problem. If there was, a remote mount, and transfer of some data could fix that problem seamlessly.

The error message was accompanied by a slightly different log-in screen, with my normal username and password prompts. Logging in on this screen leads returns the same sequence - the above error message, and different log-in screen - a do-loop.

---

### Post by lisati on 2010-05-16
Moved from "Tutorials and Tips" to "General help"

This is more like a support question than a tutorial/tip

---

### Post by Moozillaaa on 2010-05-17
I don't think 'General Help' is appropriate. NO ONE, perhaps maybe most developers included, would have ANY clue that an over-filled partition would cause this error message.

That's the reason I put it in the Developers section, as a tip for THEM to consider...

edit:
I think it's DEFINITELY something for developers to consider; since other problems might also give the indicated error message - that Gnome Power Manager isn't configured correctly, and there's an INSTALL problem.

It WAS installed and configured correctly...

---

