---
title: "Nexuiz help"
date: 2009-11-29
forum: General Help
---

### Post by Monolith1200 on 2009-11-29
hello everyone. im using crunchbang, very specifically one customized for eee pc's. well im having some trouble using nexuiz. it launches but wont allow me to play. the application just kind of kicks out when i try to enter a game.

---

### Post by Cope57 on 2009-11-29
I did not realize netbooks were for gaming... :-k

What has the crunchbang forum had to offer for a solution?

---

### Post by BenAshton24 on 2009-11-29
There's not really enough information, can you give us some terminal output.

(Just in-case you're new to Linux)
Applications->Accessories->Terminal

and type nexuiz and press enter. then post the error messages when it crashes.

EDIT: Also I doubt that you will get very good FPS on an eee PC :P

---

### Post by Monolith1200 on 2009-11-29
you too noticed that the eee isnt for gaming, very perceptive of you. Well im a big fan "if it can do it why not?" this thing did more than fine with halo in xp so i would imagine it shouldnt do too bad with nexuiz. As far as the terminal output it says i hit a segmentation fault

---

### Post by BenAshton24 on 2009-11-29
> **Monolith1200 said:**
> you too noticed that the eee isnt for gaming, very perceptive of you. Well im a big fan "if it can do it why not?" this thing did more than fine with halo in xp so i would imagine it shouldnt do too bad with nexuiz. As far as the terminal output it says i hit a segmentation fault

are there any other errors before the seg fault?

---

### Post by Monolith1200 on 2009-11-29
well here is the ouput itself


S_Startup: initializing sound output format: 48000Hz, 16 bit, 2 channels...
Wanted audio Specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 48000
	Samples   : 4096
Obtained audio specification:
	Channels  : 2
	Format    : 0x8010
	Frequency : 48000
	Samples   : 1024
Sound format: 48000Hz, 2 channels, 16 bits per sample
S_Startup: extra sound time = 48000
execing mutator_reset.cfg
Shader 'textures/Reaptxt/sun' already defined
Server using port 26000
Server listening on address local:1
Server listening on address 0.0.0.0:26000
Loaded maps/downer.ent

Trying to connect...
Segmentation fault

---

