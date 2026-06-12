---
title: "Booting without network configuration forever"
date: 2011-12-18
forum: General Help
---

### Post by MajinSaha on 2011-12-18
Hello!
It happened very suddenly to me. I've been using Ubuntu 11.10 since october no sweat. Only yesterday, when I tried to install some app, I had to free some space in my boot folder beforhand ( I'm sure some of you had the same issue ). I moved some of the files from my boot folder (only those with indexes lower than 3.0.0-*) to another partition. Then the app istalled smoothly after that. Also, I deinstalled the old header and image files corresponding to those files I moved to another partition (2.6.35-*, 2.6.38-* etc.). The system worked fine after. I turned off the computer and went to bed.
Next day it all started. After typical screens "waiting for network configuration" and "waiting up to 60 more seconds" the normal screen "booting system without full network configuration" appeared. And that's it... Nothing happens after. Usually it jumps quickly to login-password, but now it's dead. No black screen, simply this one, forever.
I read forum threads, nothing helped.
I tried to load from live CD, I checked my boot folder and found nothing there!!! I remember I left files with indexes 3.0.0-* inside, but they're gone! So I copied files from the live Ubuntu BOOT folder (all of them had files with new indexes 3.0.0-*) to the original boot folder, and also moved some of the old files back. Not all of them, as I said, there's not enough space. This gave no effect whatsoever.

What should I do? This is my office computer, all the Ubuntu was pre-installed before it went into my poccession. I hope I can fix this without complaining to my job administrator... I really need this fixed, I cannot work without it.

By the way, I'm not sure that what I did yesterday has something to do with this booting failure. Just a piece of information for those of you who think it's important. And the fact that boot folder just went empty on its own bothers me a lot!

---

### Post by Paddy Landau on 2011-12-18
Unfortunately, moving program files around like that might well have confused the Package Manager. Thus, when you deinstalled old packages, it might have caused the problem.

Remember that for the future. Install and deinstall programs only using the package manager (Ubuntu Software Manager, Synaptic Package Manager or apt-get).

Are you able to boot into recovery mode? (Boot up your machine and hold down the shift key while it boots. Grub will present a menu; choose (I think) the second option down, which is the recovery mode.)

If you can boot into recovery mode, it may be fixable without reinstalling Ubuntu, though I wouldn't promise it.

---

### Post by MajinSaha on 2011-12-18
Thanks for quick reply.
I did get into recovery mode. There was a command line, so I could execute commands. I don't know where to go from here though.
Also, I managed to load previous version of Ubuntu (11.04) by choosing it from the list ( there was an option like "previous versions of Linux" or something like that). It works just as my newest version 11.10, even Desktop background is saved. 
How can I use it? Should I try to carefully update my Ubuntu again to 11.10?

---

### Post by Paddy Landau on 2011-12-19
I don't actually know the best way forward for you.

You could try the following commands from the recovery mode, but unfortunately I simply cannot promise that they will work.
```
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
```If this does not work, I think you'll need to boot from a Live CD, back up your data, and try to upgrade again. Or, more reliably, reinstall 11.10 from scratch. But be sure to back up your data first.

Good luck.

---

### Post by MajinSaha on 2011-12-22
Thanks for your advice! I'm away from my work now, since I went for vacation. So I'll have to wait several weeks before trying something new. I'll definitely return to this post when I'm back.

---

### Post by MajinSaha on 2012-04-03
Sorry for the delay. The thread may be closed now as the problem I had before no longer persists.

---

### Post by Paddy Landau on 2012-04-03
Good news.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by MajinSaha on 2012-04-03
I'll mark it solved although I the problem was solved (at least fully) without current forum's advice. I hope this won't confuse future readers...

---

