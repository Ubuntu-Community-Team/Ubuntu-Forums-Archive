---
title: "ssh networking - sync home folders ?"
date: 2010-09-02
forum: General Help
---

### Post by luceerose on 2010-09-02
Ever since I had a hard drive that had an unexpected mechanical failure 2 years ago (& had to pay $1400 to have the drive pulled apart in a vacuum & copied), I've been understandably paranoid about ensuring I keep multiple up-to-date copies of my hard drive.

Currently, I'm running 3 computers- The TV Computer, my Wife's Computer & my Main Computer. A second hard drive in the Main Computer & an external hard drive both act solely as backups for my Home folder. The TV Computer & my Wife's Computer also keep an identical Home Folder to my Main.

I have ssh installed on all computer's & have made bookmarks via the Places Menu's 'Connect to Server', so obviously it's very easy for me to exchange files between computer's...

My problem is this; Every time I save/download/change a file, I have to copy it to 4 other hard drive's. It's kind of annoying.
Can anyone suggest some ways for me to save some time with this ???
It's a wired network with static ip's. All 3 computers are pretty much turned on 24/7.
I'm open to middle-of-the-night scheduled type of thing or whatever. Ultimately if there was a way to keep the 3 computer's Home Folders in active sync, that would be great.

P.S. All computer's are running Debian Squeeze & Ubuntu Lucid

---

### Post by clrg on 2010-09-02
rsync does what you want. Install sshd and sshfs on all three machines. Then, mount the /home folder of your source machine on the target machine. Then run rsync (try cron). For example:

```
sudo sshfs user@host:/home/user /mnt
```

And then sync the directories

```
rsync -avz --update --delete --progress /home/user /mnt
```

---

### Post by luceerose on 2010-09-02
Ok. I already have sshfs installed, though I've never actually used it. When mounting something in that fashion, I can still bookmark it with nautilus, right ?

---

### Post by clrg on 2010-09-02
You can bookmark the mount point, of course, since those are simple directories. Of course you won't see any data from the other machine unless you've mounted it.

---

### Post by scorp123 on 2010-09-02
> **clrg said:**
> rsync does what you want. Install sshd and sshfs on all three machines.  If you have rsync, you don't need sshfs :D
```

rsync -av --progress ssh-login@remote-host:/path/to/files /local/path/to/files
```

... will work tip top. Using sshfs just adds overhead and actually will decrease your performance.

---

### Post by v1ad on 2010-09-02
yes rsync ftw. used it in many cases works perfectly. best this to do is just create a script that will get all those directorys at once so you wont need to type it out every time.

---

### Post by luceerose on 2010-09-03
Ok. Unless someone's already got one... I'll google for a script for multiple rsync. Sounds good.

---

