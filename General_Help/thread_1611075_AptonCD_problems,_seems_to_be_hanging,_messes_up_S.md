---
title: "AptonCD problems, seems to be hanging, messes up Synaptic and apt-get"
date: 2010-11-01
forum: General Help
---

### Post by madmax75 on 2010-11-01
Hi,

I tried to make a restore dvd with AptonCD. 

I got to the point where it read the deb files, configured them, made the iso... and then it seemed to hang on the "cleaning" phase. I got all green tick marks on all phases, including "cleaning", but it just seemed to be keeping doing *something*, not sure exactly what. I have no idea if it was hanged or not.

Eventually, I got bored and closed the program. Sure enough, there was the .iso on my home folder, seemed to be okay, so I burned it to a dvd normally, popped the finished dvd out, inserted it again to the dvd drive to check it out --

Well, the dvd mounted itself twice for some reason and prompted to be opened up with the Synaptic package manager. Ok, I tried that, but then it hanged the Synaptic and informed me about an error with one of the extra deb files I put on the dvd (missing dependencies, I think). I also tried to open the dvd in AptonCD program (restore function) with no luck whatsoever. It didn't recognize the dvd at all.

I popped the dvd out and had to remove the dvd entry from the sources list in order to get Synaptic and apt-get to function normally again.

So, this dvd I made with AptonCD hanged my Synaptic and apt-get because of a missing dependencies of one extra deb file. At least I think this is the problem. Now I did select the "auto-select dependencies" from the AptonCD program menu, but I closed and restarted the program after that. So AptonCD does not remember the settings if you close and restart the program?

Or is something else going on? I'm not sure. I'm not even sure if I made myself a coaster under my glass of orange juice or not. :confused:

AptonCD seems to be quite unreliable?

---

### Post by Jahid65 on 2010-11-01
I never have an issue with apton cd. However of you have difficulties with aptoncd, let's try another way.
1 Make a new folder in desktop or home folder (name whatever you like)
2 copy all the deb packages from /var/cache/apt/archives(you need to be root to copy) to the newly created folder(only deb packages should be there).
3 keep it safe for the future.
4 If you want to restore all the deb packages from newly created folder. you have to do this
first go to that folder that folder through terminal (e.g. for Desktop)
```
cd ~Desktop
```
then ```
sudo dpkg -i *.deb
``` all your deb package will be installed.

Or you can use mintbackup for that. To install this in ubuntu, open a terminal then
```
sudo add-apt-repository ppa:webupd8team/mintbackup && sudo apt-get update
sudo apt-get install mintbackup
```
This is the easiest way to install.

---

### Post by madmax75 on 2010-11-02
> **Jahid65 said:**
> I never have an issue with apton cd. However of you have difficulties with aptoncd, let's try another way.

Yeah, I think that one .deb file (which I downlaoded from the net, it was not in the repositories) with it's missing dependencies was the culprit here. So I might try AptonCD again later (when I have extra dvd's :))...

But that other way you propose is interesting. Yep, it has never occurred to me that it doesn't actually matter *where* all those debs are located, if you just point dpkg to them :) So that is one thing to try.


> Or you can use mintbackup for that.

Hmm, must check that out as well.

So, AptOnCD is not a critical application for me, just wanted to try it out and hit some glitches.  think I'm going to see these other methods first and maybe try AptOnCD again later. So this is kinda solved I think :)

Thanks for the great tips, Jahid65!

---

