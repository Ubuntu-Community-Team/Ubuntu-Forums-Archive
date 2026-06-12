---
title: "&quot;An Unhandlable Error Occurred&quot;"
date: 2012-02-05
forum: General Help
---

### Post by lawrencrj on 2012-02-05
For several days after I installed the most recent version of Ubuntu (10.11 with Unity GUI) I had no problem installing packages.   I installed Skype, and Rodegarden, and several other applications.   The only problem I had was with Google Earth where I got the message “Internal Error”, but after installing WINE and trying to use it to install MSPaint (without success) I am now no longer able to install  ANY package!   I first tried to install Google Chrome (Google-Chrome-Stable-Current-i386.deb) and got the following message after putting in my authentication:

An Unhandlable Error Occurred:
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Dettails:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate

Then thinking that this was a problem limited to Chrome I tried to install several other items in the Software Center and got the same error message for all of them.   All I know to do is to just reinstall Ubuntu and start from scratch and this time avoid WINE.

The message says there is a “programming error”, but that cannot be true because, if that were the case then I would not have been able to install Skype or any of the other programs that I was initially able to install with no problem.    I have a feeling that my attempt to install with WINE has screwed up the system but that might just be a coincidence.

Any help someone can give me will be appreciated.   

-Richard
PS – I am a “newbie” to Linux.   Recently I got really angry regarding Microsoft Company because I got a new motherboard for my computer and XP did not recognize the new board and required activation and I found that now when you attempt to activate XP you no longer gat a live person to whom you can explain that you have legit copy of XP (purchased the full retail professional XP) but that you just have a new motherboard in your computer.   I only need Windows for MSPaint and Quicken (and I would like to continue to use my old image viewer, Ed Hamrics's Vuepro,   Anyway, I saved all my files, and I reformatted the drive uponwhich XP was installed and replaced it with Linux and am bound and determined to tough it out with Linux.    I will stop using computers before I go back to MicroSoft!!!!

---

### Post by Ms. Daisy on 2012-02-05
I googled the error you reported 

```
Details:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
```

and found this thread:

[http://ubuntuforums.org/showthread.php?t=1914808](http://ubuntuforums.org/showthread.php?t=1914808)

Perhaps the advice in that thread can help you.

---

