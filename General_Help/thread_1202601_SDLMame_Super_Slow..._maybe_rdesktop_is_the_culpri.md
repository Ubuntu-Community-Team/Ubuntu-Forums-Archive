---
title: "SDLMame Super Slow... maybe rdesktop is the culprit"
date: 2009-07-02
forum: General Help
---

### Post by xcrustwadx on 2009-07-02
I was having trouble with SDLMame running extremely slowly.  It took 2 minutes to open donkey kong and then it was unplayable.  Even in SDLMame menus were unusable -- I couldn't even quit... it took 3 minutes to even do that! My machine is P4 3ghz and Nvidia quadro card with latest Nvidia drivers.

I was running compiz and thought that disabling that would help but no.  It turns out it was the rdesktop windows which were open.  If they are not minimized, sdlmame will run extremely slowly.  I was running v128 and v132.

I hope this helps someone

---

### Post by williamts99 on 2009-10-24
> **xcrustwadx said:**
> I was having trouble with SDLMame running extremely slowly.  It took 2 minutes to open donkey kong and then it was unplayable.  Even in SDLMame menus were unusable -- I couldn't even quit... it took 3 minutes to even do that! My machine is P4 3ghz and Nvidia quadro card with latest Nvidia drivers.

There was a problem with not having libsdl1.2debian-pulseaudio installed.

sudo apt-get install libsdl1.2debian-pulseaudio

If you are getting 100% cpu usage after loading a game, this could be it.

Best Regards,
Williamts99

---

