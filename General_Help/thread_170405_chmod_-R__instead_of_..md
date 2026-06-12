---
title: "chmod -R / instead of ./"
date: 2006-05-04
forum: General Help
---

### Post by darkmage072 on 2006-05-04
It seems I'm in a bit of a pickle. I've seen posts on the forum about people who accidentally modify the permissions on sudoers using sudo itself, and they just have to boot into recovery mode. I however, seem to have made a bigger mistake...

I accidentally ran this command, using /* instead of ./*:

sudo chmod -R 775 /*

auth.log shows me all of the affected directories, but none of the files affected by the recursion (-R flag). Is there any way to get a list of the files that I've modified, and maybe their previous permissions?

Thanks,

- Chris

---

### Post by localzuk on 2006-05-04
To put it simply - no.

The only, reasonable, way to fix the issue is to re-install I am afraid, else you will spend the rest of time going through the tens of thousands of files changing permissions.

---

### Post by Slim Odds on 2006-05-04
[QUOTE=localzuk]To put it simply - no.[/QUOTE]

I didn't want to be the first one to break the bad news, but it's not that different from trying to recover from: sudo rm -rf / :sad:

---

### Post by darkmage072 on 2006-05-04
Alright... thanks anyways. If only I had included the -v! Gah...

A life lesson learned, I guess...

---

### Post by darkmage072 on 2006-05-04
Oh, I forgot to note that I stopped it after a few seconds, but it was long enough to mess up an unknown amount of stuff.

---

