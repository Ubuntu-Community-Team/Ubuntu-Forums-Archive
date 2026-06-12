---
title: "Help! Can't find/create libz.a"
date: 2010-05-14
forum: General Help
---

### Post by tictran on 2010-05-14
Please excuse if this is in the wrong forum, I'm new here.  We are running Ubuntu and I want to install an oldish drawing program (inkscape, although that's not relevant).  The configure file for inkscape wants libpng and the configure file for libpng wants something called "zlib" which it checks for via the "-lz" option.

There appears to be something available online called zlib but it only makes "uncompress.so"   I am getting absolutely nowhere trying to figure out whether I should just rename it as libz.a (seems wrong) or whether I even have the right package to make whatever libpng wants when it is asking for the "-lz" option.

Anyone know?  I'd appreciate any suggestions.

Mods: If this is in the wrong place, feel free to move.  If it's in the wrong forum, please let me know if you know what the right forum might be!

Thanks,
  
Richard (the system won't let me use the nickname everyone calls me by!)

---

### Post by happyhamster on 2010-05-14
Welcome to the forums! Can't you just install libpng12-dev (or perhaps libpnglite-dev) from the repos?

---

### Post by tictran on 2010-05-14
Probably could if I knew what the "repos" were!  But I do notice there are Ubuntu packages containing similar libraries as well -- is that what you meant?

Your suggestion seems like it might be one possible solution, but I won't be able to try it now for a day or two.  Thanks!

---

### Post by happyhamster on 2010-05-14
> **tictran said:**
> Probably could if I knew what the "repos" were!
That would help, yes :). I guess over the years I have become comfortable with a fair amount of jargon, and occasionally forget not everyone else has as well.

> 
  But I do notice there are Ubuntu packages containing similar libraries as well -- is that what you meant?
- Yes. Repo is short for "repository", in this case meaning a central collection of ubuntu software packages. Online repos are accessible using the synaptic package manager, or by using the command "apt-get" in a terminal. For example, to install the development files of libpng, you would run:

sudo apt-get install libpng12-dev

- in a terminal. Or: go to System-->Administration-->Synaptic Package Manager and do a search for that package there. For more info:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> 
Your suggestion seems like it might be one possible solution, but I won't be able to try it now for a day or two.  Thanks!
Good luck.

---

### Post by tictran on 2010-05-17
Worked like a champ!  Thanks for the suggestion.

Of course there were a zillion other libraries it then required but with patience I eventually found all of them.

---

