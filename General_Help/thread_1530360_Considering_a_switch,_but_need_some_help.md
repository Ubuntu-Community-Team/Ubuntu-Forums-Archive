---
title: "Considering a switch, but need some help"
date: 2010-07-13
forum: General Help
---

### Post by Zyrtec on 2010-07-13
I currently use Lucid, but I've been considering switching to Ubuntu Studio Lucid. I do a lot of stuff with music and graphics, and I read a bit into Ubuntu Studio and found that there's some differences.

Namely the fact that Studio uses a real-time kernel.

I was wondering if I switched to Ubuntu Studio if I would see any difference in usability? I feel a bit silly for asking this question, because I can't imagine things are going to be very different, but I use my computer for a lot of things, and I still want to be able to do those things (such as Programming, Drafting/Designing Electric Schematics, Oregano, other scientific things, watching movies, playing some games like Saurbraten and stuff from Humble Indie Bundle, general web browsing). Will any of these things be conflicted with a real-time kernel or anything else Ubuntu Studio has different from regular Ubuntu? 

My computer's like a Swiss Army Knife, and I need to keep it functioning like so :P

---

### Post by gzarkadas on 2010-07-13
I don't think that a real-time kernel will prevent you from using your applications, so you can proceed. However, you could also exploit another intermediate option: keep your system as is and install the ubuntustudio-xxx packages that you want (fire up Synaptic Package Manager and type "ubuntustudio" in the search box; it should show a bunch of packages). That way you can experiment with all the applications and do the switch when you are ready and confident for it.

---

### Post by snowpine on 2010-07-13
Everything in Ubuntu Studio can also be added to Ubuntu; there is no need to "switch". 

The real-time kernel is linux-rt and the applications are organized ubuntustudio-audio, ubuntustudio-video, etc. Open your Synaptic Package Manager and you should see them listed. :)

The nice thing about a real time kernel is that you can still choose your old kernel from the GRUB menu if you wish. So you could theoretically use the realtime for multimedia work and the generic kernel for everything else; how's that for ""Swiss army knife?" ;)

---

### Post by Dustin2128 on 2010-07-13
it should work fine; I noticed next to no difference on my multimedia editing laptop.

---

### Post by Zyrtec on 2010-07-15
> **snowpine said:**
> 
The nice thing about a real time kernel is that you can still choose your old kernel from the GRUB menu if you wish. So you could theoretically use the realtime for multimedia work and the generic kernel for everything else; how's that for ""Swiss army knife?" ;)

This is exactly what I did, at your suggestion. Thanks!

Marking as solved!

---

