---
title: "Question about backing up"
date: 2010-09-06
forum: General Help
---

### Post by rmcellig on 2010-09-06
I read something a while back that in Ubuntu all I have to backup is my home directory and the ETC folder. Then all I would need to do is install new copy of Ubuntu on my PC and then recover the home directory and the ETC folder. Is this true? Partially true?

---

### Post by bradleyd on 2010-09-06
it is both partially true and true.  If you keep all your docs and music, icons, plugins,etc. under your /home then you will be able to recover.  If you install applications under /home, well then you will be good also.  The benefit of backing up /etc would be to make sure all your config files are retained.  This may or may not work depending on the software versions--newer versions may change config format or name.  I usually dump out a list of a packages I have installed and back up my home directory.  This really depends on what you are trying to accomplish with your backup strategy.  If it is just to backup a desktop and be back up quickly, then /home is good.  If it is a server, you might want to look at rsync or one of the many backup solutions in the repositories. I hope that helps a little.

Take care.

---

### Post by audiomick on 2010-09-06
As far as the /home folder goes, that is where all your documents and user config files land by default. That means, if you copy that into a fresh install that has the same user on it (user name, password and so on), you should be back in business.

For this reason, it is often suggested to install with a separate partition for /home. Then you can simply remount the partition in the case of a new install.

I read somewhere that if the system has multiple users on it, they need to be added to a fresh install in the same order as in the original install, or the user id's get mixed up. I don't know if this is true or not.

Sorry, but I don't know enough about what is in /etc to offer any advice about that.

---

### Post by rmcellig on 2010-09-06
Thanks for getting back to me. In my case, I am a single user not using any kind of server. I would assume that all of the applications I add are by default installed in the folder that contains all the apps. The VAR folder? I can't remember it off hand. I'm not too concerned about apps because they are really easy to reinstall with Synaptic Package Manager or the Software Center. It is mostly my Home folder I am concerned about.

All of my computers (two old PC's and a Mac), now have Ubuntu 10.04 on them. Like I mentioned in previous posts, I am really coming to love Ubuntu more and more and this coming from a diehard Mac user.

I think what I love aside from the fact that it is free is the flexibility, as well as the vast amount of apps out there, plus the whole Ubuntu community who are so helpful!!

All I need now is a faster PC to really take advantage of all the cool stuff Ubuntu can do. :)

---

### Post by bradleyd on 2010-09-06
Backing up your /home should be fine.

---

