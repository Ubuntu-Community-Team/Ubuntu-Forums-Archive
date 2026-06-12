---
title: "FGLRX disabling APAGART error on Ubnutu boot"
date: 2006-05-08
forum: General Help
---

### Post by zakusage on 2006-05-08
Whenever I boot my computer from a complete shutdown, I notice an error that pops up momentarilly on screen. It basically says my APAGART is reporting the wrong VRAM amount, and that to fix it I should enable something in grub boot (which of course doesn't help at all). I'm running an AMD64 computer, and I have an ATI Radeon 9600 (I know, I feel like shooting myself). 

The problem of the fact that whenever this appears (which is EVERY time after a complete shutdown) my FGLRX driver does not work. At first, I thought this was a BIOS problem, but after fiddling around in there for about a week I determined that it just wasn't. I finally figured out a temporary solution: if I reset my computer any time after this error has shown, the error will not appear on the reboot and FGLRX will load completely normally. Now, I'm at ends wit with this annoying problem. Does anyone know anything that will help it to disappear? 

I'm thinking it might be one of two things: a kernel error, or a GRUB problem. I don't has anything to do with Ubuntu specifically, however, since I noticed the same problem when I installed Fedora Core 5 the other day. 

Should I try to install LILO, and see if that helps? (note, I've never really used LILO aside from one bad experience)
Should I complain here until someone offers assitance?
Is there anything I can do?

---

