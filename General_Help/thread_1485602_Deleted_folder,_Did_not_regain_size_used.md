---
title: "Deleted folder, Did not regain size used"
date: 2010-05-17
forum: General Help
---

### Post by iMisspell on 2010-05-17
Sorry about the poor title, did not know how to word it.

I had a folder on my Lucid server which had a bunch of files in it, the folder was around 200GB.

While connect via SSH i was renaming things and screwd up a command and the result was all files where renamed with a period at the begining which "hide" them.

I had a back up of all files so i dump the "hidden" files to a new folder and then copied over the backup files via a samba mount from my desktop.

After everything was copped over, i delete the "bad" folder which was holding all the 'hidden' renamed files. After deleting that folder, the 200GB worth of 'hidden' files never came back, that 200GB is lost (the server still thinks the 200GB is there, but the folder with the "hidden" files is gone).

Just restarted the server and checked again the size of the mount and still, the size never was regained.

Any advice would be great.

_

---

### Post by BoneKracker on 2010-05-17
I know this is a server, so you were probably working over ssh from the command line, but I don't suppose you did your deleting via Nautilus and those files are now sitting in a trash directory somewhere?

---

### Post by iMisspell on 2010-05-17
Thanks for the responce.
Yes, the files where deleted while working through Nautilus.
Trashcan can was empted... but with you using the phrase, "trash directory somewhere" i just checked the drives main mount and the files are sitting in .Trash-1000/files.

Mystry solved, thanks :)

Now, this bring me to a new question.
The drive which the "hidden" files where deleted from is mounted in two different machines and also shared with Popcorn Hour. 

If i deleted the files though Nautilus from desktop A, shouldnt those files be deleted period ? Machine 'B' is in the living room, im in the bed room right now, i have no kids (to send off and check the other computer), Remote Desktop is acting up and im way to tired to get up an work my way to the other computer and check.

Ive had drives mounted on different computers in the past and nver came across this problem before.

---

### Post by BoneKracker on 2010-05-17
> **iMisspell said:**
> The drive which the "hidden" files where deleted from is mounted in two different machines and also shared with Popcorn Hour. 

If i deleted the files though Nautilus from desktop A, shouldnt those files be deleted period ? Machine 'B' is in the living room, im in the bed room right now, i have no kids (to send off and check the other computer), Remote Desktop is acting up and im way to tired to get up an work my way to the other computer and check.

Ive had drives mounted on different computers in the past and nver came across this problem before.

I don't know.  I don't use a file manager, so I don't really know how trash works.

Drink some coffee, smoke a cigarette, get up off your dead *** and check. :P

---

### Post by DawieS on 2010-05-17
It seems as if every user has to empty his own trash before logging off. If you have deleted files with a sudo login (without emptying the trash), you would not be able to empty the trash when logged in as normal user.
:smile:

---

### Post by iMisspell on 2010-05-18
> **BoneKracker said:**
> Drink some coffee, smoke a cigarette, get up off your dead *** and check. :PThanks for the motivation... hahaha


Ok, heres a play by play for any one interested.

Have one machine running Lucid server.
Have two more machines running desktops; 'A' - Jaunty, 'B' - Lucid.
Both desktops have a server drive mounted in them (full storage harddrive).

- While using desktop A, i deleted a bunch of hidden files from the mounted drive via Nautilus.

- Emptied desktops A's trash only to find that the space the hidden files was taking up was never "freed".

- Restarted the server, still not "freed"
- Emptied desktop B's trash, still not freed.
- Restarted server, still not freed.
- Logged off desktop A, still not freed
- Logged off desktop B, still not freed
- Restarted server, still not freed.
- Powered off desktop B, still not freed (this was not part of the testing/trouble shooting, i only use that computer on the weekends)
+ Using desktop A, whent in the mounted drives '.Trash-1000' folder though Nautilus and deleted the hidden files, still not freed.
+ Emptied desktops A's trash, FREED

This server is my own home server used for various things, nothing top secret or earth shattering, but i would still like it to run good, along with learning how Linux works.

Can someone explane to me what whent on here ?

_

---

