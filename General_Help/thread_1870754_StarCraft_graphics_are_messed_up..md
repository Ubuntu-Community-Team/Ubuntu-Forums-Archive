---
title: "StarCraft graphics are messed up."
date: 2011-10-27
forum: General Help
---

### Post by RoastedBeef on 2011-10-27
As the title says.
[IMG]http://i44.tinypic.com/33cok5t.png[/IMG]

I've installed StarCraft via wine, with no problem at all. Patched it via wine, no problem at all.

Here's the kicker, when I run it, its graphics are messed, high pitched colors and dots all over the screen. Not to mention when I close the game, the screen stays black.

I had this similar problem when I had Windows 7 installed, and Blizzard has a way of fixing it, but for windows vista, which I assume it would probably be the same for Windows 7 (Compability issues)


Anyone knows how to resolve this? Much appreciated?

---

### Post by spacesamurai on 2011-10-27
I have got Starcraft to run on 11.04 x86_64 after going thru much hardship

More than anything, I think you will need to look a you graphic card and the wine conf you are using.

Can you please give us more info for what graphic card/driver you are using?

---

### Post by RoastedBeef on 2011-10-27
ATI Radeon 3000 Graphics/256 MB

By drivers you mean "Driver Versions"? Because I'm at the Catalyst Control Cener. I'll put em anyways.

Driver Packaging Version: 8.723.1-100408-098580C-ATI
2D Driver Version: 8.72.11
Catalyst Cont. Center Ver.: 2.12
RandR Version: 1.3

OpenGL
   OpenGL Provider: ATI Technologies Inc.
   OpenGl Renderer: ATI Radeon 3000 Graphics
   OpenGL Versions: 3.2.9756 Compability Profile Context

Not sure if this helped, let me know.. I may be wrong.

Edit:

I'm on Ubuntu 10.04 LTS Lucid Lynx (x86_amd64)

---

### Post by spacesamurai on 2011-10-28
I am afraid this might be due to the ATI Radeon card. I had the same problem with my ATI Radeon card, so in the end I gave up and went with a Nvida and that solved all my woes (Worked for both Starcraft and TF2).

The one suggestion I can give for the ATI cards is to get and install the driver directly from the ATI website. Their driver is the latest release and can help solve some of these bugs.

Has anyone else been able to get Wine to play nice with ATI?

---

### Post by RoastedBeef on 2011-10-28
> **spacesamurai said:**
>  Has anyone else been able to get Wine to play nice with ATI?

I have, every single game I've played and installed via Wine. (Warcraft 3, Halo Combat Evolved, and others).

I'll search for the drivers. 

> **iware said:**
> That error code looks VERY familiar. Anyway, I got the same problem when reinstalling and playing Diablo II again. Do you have Windows Vista? If so, you'll have to go on Battle.net if you can and download the patch. If you can't because it messes up on you (Like it did for me) you'll actually have to go to the Blizzard site and download the patch and install it.

What do you mean by if I have Windows Vista? I'm on Ubuntu Lucid Lynx. Sorry, I didn't get that part. 

And I manually patched the game, graphic problems still present.

---

### Post by Blaqksheep on 2011-10-28
It's probably just the curse of playing a 90's game on a modern machine.

Try setting your machine to run in VGA (640x480) resolution and 256 colors.  If you can't drop down to 256 colors, at least try 16 bit.  A plausible cause of the colors being jacked up is that your GPU is just trying to display more colors than the game was made to know of.

Try that and see if it works.  If it does let me know.

---

### Post by Omega420 on 2011-12-21
> **Blaqksheep said:**
> It's probably just the curse of playing a 90's game on a modern machine.

Try setting your machine to run in VGA (640x480) resolution and 256 colors.  If you can't drop down to 256 colors, at least try 16 bit.  A plausible cause of the colors being jacked up is that your GPU is just trying to display more colors than the game was made to know of.

Try that and see if it works.  If it does let me know.

Um no, cuz Starcraft 2 has same kine problem.

---

