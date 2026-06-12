---
title: "Create song list from folder"
date: 2009-07-08
forum: General Help
---

### Post by ricardisimo on 2009-07-08
I have a folder with about 100 audio files in it, all titled with the exact same format: "a% - b% - d% - n% - t%.ogg"

I'd like to know if there is some way for me to easily generate a plain text track listing from them, for printing or otherwise. A spreadsheet-friendly CSV might be nice, too. Thanks.

---

### Post by aysiu on 2009-07-09
```
ls -R *foldername* >> *textfilename.txt*
``` should do it.

---

### Post by ricardisimo on 2009-07-09
No. I tried with and without cd-ing to the folder in question first, and both ways all I got was ```
> 
``` with a flashing cursor after it. I'll try cd to the parent folder first, then just use the sub folder's name, unless there's another problem.

Does this code work for you?

---

### Post by ricardisimo on 2009-07-09
Hey! That worked! So if someone needs to do this, let's suppose they have a folder called  with all of the album's songs in it. So first they would cd to the penultimate folder, "David Bowie" like so:
```
cd '/home/username/Music/David Bowie' 
```
and then run aysiu's command like so:
```
ls -R '/home/username/Music/David Bowie/Hunky Dory' >> songlist.txt
```
Maybe it should work without going to the parent folder first, but it didn't for me. Thanks.

---

### Post by aysiu on 2009-07-09
So what happens when you run this command? ```
ls -R ~/Music >> songlisttest.txt
```

---

### Post by ricardisimo on 2009-07-09
You mean your original command? If I don't cd to the parent folder, it just blinks at me with a ">"... it's clearly doing something but what I don't know.

---

### Post by mbeach on 2009-07-09
no, I think aysiu is saying to do exactly as posted in the more recent post.

```
ls -R ~/Music/ >> songtitletest.txt
```

if you type exactly that in - do you still get the > prompt? The ~ is shorthand for the current user's home directory. You should be able to run that command from anywhere (as long as you have write access, as whereever you are is where songtitletest.txt will be written). So 
```
cd ~
ls -R ~/Music/ >> songtitletest.txt

```
will put songtitletest.txt in your home directory.

---

### Post by ricardisimo on 2009-07-09
Well, there's no music in my home "Music" folder; the folder I used is on a separate storage drive, not in my home folder.

This is very curious... now it's working. It is producing a "songtitletest.txt" file in my home folder, no matter what folder I'm plugging into the equation. Very cool. Also perplexing. Why wasn't it working before?

Interestingly, if you run this command various times without deleting songtitletest.txt or changing the name, it appends, rather than overwrites. That's a nice feature, I guess. Thanks again.

---

### Post by mbeach on 2009-07-21
> **ricardisimo said:**
> Well, there's no music in my home "Music" folder; the folder I used is on a separate storage drive, not in my home folder.

This is very curious... now it's working. It is producing a "songtitletest.txt" file in my home folder, no matter what folder I'm plugging into the equation. Very cool. Also perplexing. Why wasn't it working before?

Interestingly, if you run this command various times without deleting songtitletest.txt or changing the name, it appends, rather than overwrites. That's a nice feature, I guess. Thanks again.

If you do happen to need a new file (instead of appending) replace the >> with > which will start a new file. Whatever folder you are currently in will contain the songtitletest.txt. If you want to put it somewhere else you'd do something like:
```

ls -R /path/to/youMusic/ >> /home/yourusername/somefolder/songtitletest.txt

```

some reference for you:
[http://www.tuxfiles.org/linuxhelp/iodirection.html](http://www.tuxfiles.org/linuxhelp/iodirection.html)

---

