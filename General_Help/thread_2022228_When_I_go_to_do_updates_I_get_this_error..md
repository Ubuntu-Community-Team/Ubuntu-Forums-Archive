---
title: "When I go to do updates I get this error."
date: 2012-07-10
forum: General Help
---

### Post by irv on 2012-07-10
```
W:Failed to fetch http://ppa.launchpad.net/unity-team/lenses-testing/ubuntu/dists/precise/main/source/Sources  404  Not Found 

, W:Failed to fetch http://ppa.launchpad.net/unity-team/lenses-testing/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found 

, W:Failed to fetch http://ppa.launchpad.net/unity-team/lenses-testing/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found 

, E:Some index files failed to download. They have been ignored, or old ones used instead.
```
Does this mean it failed to fetch the ppa's from the Internet, or does it mean I need to add these ppa's to the source?
I don't find them listed as such in my Software source in the package manager.

---

### Post by CharlesA on 2012-07-10
Looks like an old PPA. Uncheck it in software sources and see if that gets rid of the error.

---

### Post by irv on 2012-07-10
That did the trick, but the ppa was just recently added. Maybe it was just down at the time of updating.
I believe it was for the News lens.
[ATTACH]221027[/ATTACH] 
I will mark this solved.

---

### Post by CharlesA on 2012-07-10
The URL was **lenses-testing** so maybe they moved it from testing to something else?

---

### Post by irv on 2012-07-10
> **CharlesA said:**
> The URL was **lenses-testing** so maybe they moved it from testing to something else?

That is very possible because I am always testing something before it is released. My list of ppa are getting very long.
The problem with this is when I do updates it takes longer now. It is getting to the point where I will have to do a wipe and start clean again. The only problem with that is I have so many thing that I use and like I will have to reload them all again. But I know I have stuff that are just taking up space and memory.

---

