---
title: "Amnesia: The Dark Descent fails to launch"
date: 2010-09-07
forum: General Help
---

### Post by polardude1983 on 2010-09-07
I go to my applications>games>amnesia - the dark descent demo

it opens up the Launcher, but when i hit Launch game it puts my screen into fullscreen then exits out of the game instantly and returns to my desktop :/

---

### Post by Alcareru on 2010-10-01
I had the same issue. Your problem is that the game seems to require write access to where ever you installed it. So one solution is to change all files there to be owned by you but there is ofc many ways to achieve this. 

Another issue I myself had was sound crackling horribly. In the end I chose PortAudio Software (start the game through Launcher.bin to get to select options). I have no idea what so ever what on earth is that PortAudio Software thingy, but it seems to work.. regardless of the fact that I have pretty standard Ubuntu installation and there for naturally pulseaudio should be the logical way to go here. Anyhow I still get messages saying:
bt_audio_service_open: connect() failed: Connection refused (111)
when I start the game from console, but all is fine, a couple of graphics bugs regarding lighting but nothing too drastic (in my 5 minute quick run), but that's another story then I suppose.

---

