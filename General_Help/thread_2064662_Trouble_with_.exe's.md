---
title: "Trouble with .exe's"
date: 2012-09-29
forum: General Help
---

### Post by 13floppydisks on 2012-09-29
So I'm an Ubuntu noob trying to broaden his OS horizons. It's been going well until just now when I started looking at some games to install. I downloaded Urban Terror, but I can't seem to get it running. UrTUpdater won't run for me, and I've looked around at other people having problems but none of their suggestions helped. I've tried running it from terminal, but I always either get: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory, or No such file or directory even though I type it in right. I tried redownloading it many times but no change. I'm sure I'm just making a rookie mistake somewhere but this is frustrating. ](*,)

---

### Post by 3rdalbum on 2012-09-29
How did you download Urban Terror? If you can, you should download it from a PPA as it will automatically download all the necessary dependencies too.

The error message you are getting says that your computer is missing one of the dependencies necessary to make the program run. You'll need to look in the Ubuntu repositories for a package that might provide "libQtGui" - a quick look yielded "libqt4-gui" for me, this may be the correct one.

Once the package is installed, you'll either be able to run the program now, or running it will show another message similar to the one you've just got saying that it's missing something else.

TL;DR: Try looking for a PPA that contains Urban Terror as it will do all this for you.

By the way, your thread title is not really descriptive; ".exe" is the Windows program format, not the Linux program format.

---

### Post by 13floppydisks on 2012-09-29
My bad on the .exe, but where do you go to look for the repositories?

---

### Post by Bashing-om on 2012-09-30
Remember, google is your friend.
Lots of hits "urban terror ubuntu" ..supported package here:
[http://www.ubuntuupdates.org/package/getdeb_games/precise/games/getdeb/urbanterror](http://www.ubuntuupdates.org/package/getdeb_games/precise/games/getdeb/urbanterror)

[INDENT]aim'n to please ==>BDQ

[/INDENT]

---

### Post by Bazon on 2012-09-30
As this is a beginner, it maybe useful:
As written [there]("http://www.ubuntuupdates.org/ppa/getdeb_games?dist=precise"), add the repository by entering in the terminal:
```
wget -q -O - http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu precise-getdeb games" >> /etc/apt/sources.list.d/getdeb.list'
```
after that, you can install the package:
```
sudo apt-get install urbanterror
```

---

