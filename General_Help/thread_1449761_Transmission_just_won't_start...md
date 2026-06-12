---
title: "Transmission just won't start.."
date: 2010-04-08
forum: General Help
---

### Post by aklo on 2010-04-08
I've been using it for 5months daily since i started using ubuntu, i was also using this morning but now it just won't start. I have the icon on the gnome panel but i click many times and it just won't start. There are no error message displayed also.

So i opened system monitor and i click on transmission. The "Transmission" process appeared for like 1 sec on the system monitor then it seemed to disappear/quit it self.

Anybody with any ideas? I have torrents running and i'm not sure if reinstall will make it all disappear..

---

### Post by Vaphell on 2010-04-08
run transmission from terminal (open terminal window, type transmission)
apps usually output their warning/error messages when run in terminal, maybe you'll get some hints where the problem is.

---

### Post by 3rdalbum on 2010-04-08
> **aklo said:**
> I've been using it for 5months daily since i started using ubuntu, i was also using this morning but now it just won't start. I have the icon on the gnome panel but i click many times and it just won't start. There are no error message displayed also.

So i opened system monitor and i click on transmission. The "Transmission" process appeared for like 1 sec on the system monitor then it seemed to disappear/quit it self.

Anybody with any ideas? I have torrents running and i'm not sure if reinstall will make it all disappear..

A reinstall will only replace the binary (which is, most likely, perfectly good) with a fresh copy.

The most likely culprit is that some user data, such as your Transmission preferences or details on one of the torrents that is downloading, is corrupted.

The Transmission user data is stored in ~/.config/transmission. Just rename the folder to "transmission-backup" or something and Transmission will create a new user data folder when you next start it.

If this fixes the problem, then you can start introducing parts of the transmission-backup folder back into the main Transmission user data so your torrents will continue. Obviously, stop and reverse your last change if it causes the problem to start again.

---

### Post by shaka_zulu on 2010-04-08
Did you make some update previously or did you do anything with your system previously?

---

### Post by aklo on 2010-04-08
Ok i tried typing transmission in the terminal and it displays this error.

transmission: malloc.c:4903: _int_free: Assertion `p->fd_nextsize->bk_nextsize == p' failed.
Aborted

I'm going to try the 2nd solution next and i'll post if it works or not.

Edit: Yup the 2nd solution works, it enables me to start my transmission again so i believe it is some files corrupted...but i don't know that corrupted files could affect a program? 
My files are mostly video files.

Hopefully i can get my files back.

---

### Post by Charles Kerr on 2010-04-08
You should file a bug at launchpad and attach the crash report to the ticket, so that upstream can learn more about the problem and (hopefully) fix it.

There are instructions on filing a crash report ticket here:

[https://wiki.ubuntu.com/Bugs/Responses#Missing%20a%20crash%20report%20or%20having%20a%20.crash%20attachment](https://wiki.ubuntu.com/Bugs/Responses#Missing%20a%20crash%20report%20or%20having%20a%20.crash%20attachment)

---

### Post by Vaphell on 2010-04-08
if by accident config file got malformed then parsing the file to read settings can crash the app, because for example the app does expect some defined values and gets something else.
if you have backed stuff up, you can try to move files back to default transmission folder. There are files that store only configuration but there also should be the files that track what you currently download and partial downloads.

---

### Post by aklo on 2010-04-10
Problem solved.

For the record, transmission worked fine for months(I always update) and i was even using a few hours earlier on that day itself...and then it suddenly stopped working.

I backup  ~/.config/transmission folder and created a new 1.

Then i replace the torrents 1 by 1 and didn't replace the torrent which caused the problem.

---

