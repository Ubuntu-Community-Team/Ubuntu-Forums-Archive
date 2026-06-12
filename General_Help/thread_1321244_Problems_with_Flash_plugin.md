---
title: "Problems with Flash plugin"
date: 2009-11-09
forum: General Help
---

### Post by jfinner1 on 2009-11-09
I just downgraded my computer from Karmic back to Jaunty, since Karmic didn't like my computer. Well, I'm having an issue with my flash plugin in Firefox. At least, I think it's the flash plugin. I can play flash videos, like in YouTube, just fine, so that's not an issue. But I can't use the "Attach" button in Yahoo mail, I can't use the uploader in PhotoBucket, and one of my school pages that uses flash comes up fuzzy. That's what I've noticed so far, and as far as I know all of these things use Flash, so I figure it's gotta be the plugin. Any ideas on what I should do? Thanks in advance.

---

### Post by plusnplus on 2009-11-09
Hi jfinner1,
Have you try install ubuntu-restricted-extras?

---

### Post by jfinner1 on 2009-11-09
Um, no? I don't think so... How do I do that? As much as I've been using Ubuntu for over a year, I still feel like a total noob sometimes...

---

### Post by plusnplus on 2009-11-09
Hi jfinner1,

sudo apt-get install ubuntu-restricted-extras

---

### Post by MelDJ on 2009-11-09
first you add the medibuntu reposortiy by following this: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu). then do sudo apt-get install ubuntu-restricted-extras in terminal

but i doubt its that. maybe you could find solution here: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by jfinner1 on 2009-11-10
Thanks everyone for all the suggestions. I found the solution in the second link posted my MelDJ, under the Flash Optimization section. Everything is working peachy now! Thanks a ton!!

---

### Post by coffeecat on 2009-11-10
> **MelDJ said:**
> first you add the medibuntu reposortiy by following this: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu). then do sudo apt-get install ubuntu-restricted-extras in terminal

A point of information - ubuntu-restricted-extras is in the Multiverse repository, so you don't need the Medibuntu repository for that. Perhaps you are thinking of libdvdcss2 and w32codecs/w64codecs for which you do need the Medibuntu repository. But I always install libdvdcss2 and w*codecs with ubuntu-restricted-extras, so I have to enable Medibuntu anyway. After all, ubuntu-restricted-extras without libdvdcss2 and w*codecs is a bit like strawberries without cream. :)

---

