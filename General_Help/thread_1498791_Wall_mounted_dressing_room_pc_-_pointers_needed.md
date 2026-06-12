---
title: "Wall mounted dressing room pc - pointers needed"
date: 2010-06-01
forum: General Help
---

### Post by strictlybusiness on 2010-06-01
I've gotten an idea into my head and now I have both some old hardware and the time (paternity leave) to attempt it.
The idea is to use an old laptop (pIII 600Mhz with 128mb RAM) and rebuild it as a wall mounted screen (like a digital picture frame but with the touchpad accessible) and hang it in our walk in closet.
The purpose is not so much to use it for anything, but rather have it display pictures (automatically grabbed from my server) and to display the day's weather and news headlines in the morning, in a nice way (i.e. like a 10 foot interface). To connect to my houses squeezeserver would also be nice, but not necessary.
I guess I need some way to automate wake-up/shut down (doesn't have to be on all day and night) and specific packages that can be made to display what I'm after.
I figure xubuntu due to the low-end specs of the hardware - other distributions might be even better, but I'm not so good at Linux. I have run Ubuntu for some years, XBMC Linux since it came and have some xubuntu installations up and running (mostly for relatives) but I've always just gotten by through reading in forums and stuff, and I can't figure anything out by myself.
So, I'd really appreciate any pointers to methods, software or just ideas to enable this project to start. (Or someone telling me that this just isn't possible, so I can get rid of the idea)

/Ben

---

### Post by dcstar on 2010-06-01
> **strictlybusiness said:**
> I've gotten an idea into my head and now I have both some old hardware and the time (paternity leave) to attempt it.
The idea is to use an old laptop (pIII 600Mhz with 128mb RAM) and rebuild it as a wall mounted screen (like a digital picture frame but with the touchpad accessible) and hang it in our walk in closet.
The purpose is not so much to use it for anything, but rather have it display pictures (automatically grabbed from my server) and to display the day's weather and news headlines in the morning, in a nice way (i.e. like a 10 foot interface). To connect to my houses squeezeserver would also be nice, but not necessary.
I guess I need some way to automate wake-up/shut down (doesn't have to be on all day and night) and specific packages that can be made to display what I'm after.
I figure xubuntu due to the low-end specs of the hardware - other distributions might be even better, but I'm not so good at Linux. I have run Ubuntu for some years, XBMC Linux since it came and have some xubuntu installations up and running (mostly for relatives) but I've always just gotten by through reading in forums and stuff, and I can't figure anything out by myself.
So, I'd really appreciate any pointers to methods, software or just ideas to enable this project to start. (Or someone telling me that this just isn't possible, so I can get rid of the idea)

/Ben

I once set up a netbook running Ubuntu UNR (with an external display) using the **keyjnote** package to cycle through PDFs and jpegs of weather radar I got using wget cron jobs.

I basically had a series of screens with messages interspersed with up to date info from the Internet to keep peoples' attention and it worked reasonably well.

The netbook was to sit up behind a big flat screen way up on a wall with just a power and LAN connection and automatically log on and run a script that started the keyjnote program.

---

### Post by strictlybusiness on 2010-06-01
Thanks dcstar, that's just the sort of ideas I'm after!
KeyJnote seems to be Impressive now, and I'll look into it more closely. However, at first glance it seems as if it would require quite some setup (doesn't everything...). I'm still hoping for something along the lines of "A weather widget on the left side of the screen, an RSS widget on the right side of the screen", but that's probably too much to ask for.
Any more ideas while I'm thinking?
/ Ben

---

### Post by strictlybusiness on 2010-06-01
With some more thinking, can Conky be something for me? I'll read up on it.

---

