---
title: "[SOLVED] text input and missing terminal using nVidia (separate issues)"
date: 2006-05-25
forum: General Help
---

### Post by malachias on 2006-05-25
Hi

First of all, text input. Whenever I have a text field (address bar in firefox, pretty much anywhere in open office writer, thunderbird, etc), the blinking vertical bar (is it called a cursor?) goes weird. First of all rather than being 'on' or 'off' a piece of it will be on, then whatever wasn't on before goes on and the rest goes off. Worse is when I move it with the keyboard it leaves itself behind between every character (this usually goes away if I type a character at the beginnning of the line) making it very difficult to figure out where I'm actually going to be typing when I hit a key.

Secondly, when using the nvidia drivers (the real ones, whether I compile them myself, or get them through synaptic, etc), the 'real' terminals disappear. Ctrl-Alt-F1 through F5 just give me black screens and stay that way until I change my xorg.conf file back to the 'nv' rather than 'nvidia' version, and reboot. Apparently they're still functional since I managed to 'blindly' reboot my maching by typing into a black screen, but this is a real pain when I'm trying to fiddle with my X server.

I have a Sony Vaio VGN-S460, and am running Dapper Drake Beta, but these problems have been with me since I switched to Ubuntu Hoary (I don't remember fully, but I don't believe they were a problem under Kubuntu). Anyone have any tips? I've been trying Google for a long time but as of yet have not been able to find anything.

Cheers,
Mal

---

### Post by malachias on 2006-05-28
(bump)
Anyone? This is really starting to get to me.

---

### Post by malachias on 2007-08-29
The solution was just to use the legacy-drivers.
Anyway, the new drivers work a charm

---

