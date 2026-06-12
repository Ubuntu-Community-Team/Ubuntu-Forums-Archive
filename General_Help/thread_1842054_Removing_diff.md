---
title: "Removing diff?"
date: 2011-09-10
forum: General Help
---

### Post by Theredbaron1834 on 2011-09-10
I am trying to clean up my install a bit, removing old packages, orphaned packages, metapackages, ect. I saw the package "diff". It is just used as an upgrade to diffutils. However, when I tried to remove it, I was given a warning that it could break the system. 

So, can I remove it? I know it is not a big file, so you may ask why, but I have a really small drive. Every bit helps.

---

### Post by TurtleKing on 2011-09-10
I have never came across an application with a warning like that, and I also like to remove stuff I don't use. I have previously in other times removed programs that screwed up Ubuntu badly (IM and social programs) and didn't warn me. If this program is letting you know in advance, then don't remove it. Someone might tell you it's okay, but they cannot guarantee it will react differently on your PC.

---

### Post by WorMzy on 2011-09-10
I guess it depends on which version of Ubuntu you're using. I can personally confirm that it's not installed by default on Natty, so if you're using that, you should be able to remove it without any problems.

The package takes up a grand total of 36kB though, is it really worth the risk?

---

### Post by Theredbaron1834 on 2011-09-10
I had that problem before too Turtleking. And youmakea good point.

I am running natty, a install, not upgrade, and it was installed, how I got it, who knows. Since it so easy to reinstall nix if I mess up (I can go from a blank drive to it set up just the way I like, with all "my programs" in less then an hour) I figgered I would try. Didn't have a prob, but synaptic auto installs when you click install all upgrades. Guess I am stuck with it. :)

On a side note, using deborphan I removed ALOT of files, most under 50kb's, and got over 100mb of freed space. That really helps when I reg have just 500mb of free space on my drive.  (eeepc ssd)

---

### Post by TurtleKing on 2011-09-10
> **Theredbaron1834 said:**
> I had that problem before too Turtleking. And youmakea good point.

I am running natty, a install, not upgrade, and it was installed, how I got it, who knows. Since it so easy to reinstall nix if I mess up (I can go from a blank drive to it set up just the way I like, with all "my programs" in less then an hour) I figgered I would try. Didn't have a prob, but synaptic auto installs when you click install all upgrades. Guess I am stuck with it. :)
I had that happen with a game, Ubuntu Update Manger kept asking me to reinstall it.:lol:

---

### Post by Theredbaron1834 on 2011-09-10
Ha, I HATE the update manager. Among the first things I remove after a fresh install. I only have a 900mhz cpu, and that kills my startup. I use Synaptic most the time, less I frell something up so bad X can't start.Then I use Aptitude and apt-get via a root shell in recovery mode.

It just bugs me that it shows up to be removed with deborphan but I can't just remove it. Also mktemp, which was replaced with coreutils. Does the exact same thing.

---

