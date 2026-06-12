---
title: "dungeon crawl stone soup"
date: 2011-03-15
forum: General Help
---

### Post by dduckett on 2011-03-15
I am trying to play the latest build of dungeon crawl stone soup through command line by placing the binary file in /usr/games (which I built using "make"). The problem is that when I open the game it creates folders in the current working directory, which means if I start playing crawl while in another working directory, then I don't have the save game files, and it drops some more folders in that directory.

I read through install files (tried recompiling with prefix=/usr/games, but that didn't seem to make a difference). At this point, I'm a bit baffled as to how to specify to the game a specific save directory. I thought this was the fix, but it didn't work:

"* If you want to install Crawl for multiple users, you can add the savegame
  path and game data path to the 'make' command line. For instance:

    make prefix=/usr/games/crawl SAVEDIR=saves/ DATADIR=data/

  Please note that SAVEDIR and DATADIR are relative to 'prefix'.

  Of course, you should make sure that SAVEDIR and DATADIR reference the
  appropriate directories. This is not necessary if only one user is going to
  play Crawl."

Thanks in advance for any help.

---

### Post by dduckett on 2011-03-15
The above prefix for compiling was correct, I just needed to move all the files and folders into the correct directory structure (the reason I didn't do this before is I couldn't figure out where some folders and files went). I'm still unsure how the prefix works in relation to the SAVEDIR and DATADIR--finding where folders went was a bit of a trial and error using returned errors when trying to run crawl.

I put my save and data folders in /usr/games, but had some errors with permission access, so I suggest making the prefix, savedir, and datadir all in your home directory.

In my case, here is what I did exactly:

1) I made a folder ~/Games/Crawl/
2) After unpacking the crawl build, go to the source folder and type: make prefix=~/Games/Crawl SAVEDIR=saves/ DATADIR=data/
3) Put the completed crawl binary in /usr/games
4) Create a data folder: ~/Games/Crawl/Data
5) In the newly created data folder, copy and paste the dat, docs, and settings folder from the unzipped crawl file.
6) In ~/Games/Crawl/saves make sure there is a morgue folder and also copy and paste the saves folder from the unzipped crawl file.
7) Type crawl in any working directory and it should allow you to play with saved games in one place and without creating folders in your current working directory.

My apologies for this post being somewhat unrelated to ubuntu.

---

