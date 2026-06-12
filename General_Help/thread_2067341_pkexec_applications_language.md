---
title: "pkexec applications language"
date: 2012-10-06
forum: General Help
---

### Post by el_baby on 2012-10-06
Hi,

in my home computer I have Spanish as the default language since we all speak Spanish.

However, I (and only I) am much more comfortable using the computer in English rather than in Spanish, so I have set my own user language as English.

Most things work just as I want, however, there are a couple of things that I always noted that displayed in Spanish within my own user.

Digging a bit today, I noticed it was **synaptic** and **gparted**... digging a bit deeper, I found out that they're invoked using **pkexec** within unity (that is, the actual command launched are **synaptic-pkexec** and **gparted-pkexec**.

Now, I notice that if I invoke the command as "**gksu synaptic**", "**sudo synaptic**" or "**gksudo synaptic**", it starts up in English, however, if I invoke it as "**synaptic-pkexec**" or "**pkexec synaptic**", it appears in Spanish.

I tried adding "LANG=" and "LC*=" variables to root's .profile and .bashrc to no avail.

Where can I set the language that applications invoked through pkexec will use? I DON'T want to change the system's default language.

TIA

---

