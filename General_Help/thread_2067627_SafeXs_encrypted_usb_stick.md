---
title: "SafeXs encrypted usb stick"
date: 2012-10-07
forum: General Help
---

### Post by tsanctuary on 2012-10-07
Dear All,
I wonder whether anyone can help with this problem?

I have been provided with a SafeXs memory stick from work. It's encrypted. According to the producer 'Softek', it is usable in linux. One simply needs to copy the following line '%users ALL = NOPASSWD: /media/safestick/safestick' into sudoers and it should work.
I have tried this using sudo visudo as was recommended on a few forums. Then ctrl+X and then Y to save.  In fact, because of the error message I was getting as shown below, I exchanged the 'safestick' bit of the line for 'SafeXs'.
Despite this, when I click on the SafeXs.exe file that I see when I open the usb drive, I continue to get the same error message:

Archive:  /media/SafeXs Login/SafeXs.exe
[/media/SafeXs Login/SafeXs.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/SafeXs Login/SafeXs.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/SafeXs Login/SafeXs.exe or
          /media/SafeXs Login/SafeXs.exe.zip, and cannot find /media/SafeXs Login/SafeXs.exe.ZIP, period.

I have tried using it via WINE. It looks promising initially but the little password box that pops up simply says 'waiting for safeXs' and nothing happens.

I have tried opening it with archive manager, autorun prompt....nothing works.

Have I made the sudo adjustments incorrectly? Is there something I am missing?
Any advise gratefully received

Tom

---

### Post by Cheesemill on 2012-10-07
It looks like you are trying to run the wrong file.

We can ignore all of the sudoers stuff for now, that just means you don't need to enter your password but for now we'll just try and get it working.

What other files are there on the drive?
Can you post the output of:
```
ls -la /media/SafeXs\ Login
```

---

### Post by tsanctuary on 2012-10-07
Thanks for the reply.
When I input your line into the terminal, the following comes back

dr-xr-xr-x 3 tom  tom     2048 Jan 27  2012 .
drwxr-xr-x 4 root root    4096 Oct  7 15:07 ..
-r-xr-xr-x 1 tom  tom       65 Jan 26  2012 autorun.inf
-r-xr-xr-x 1 tom  tom    23558 Jan 26  2012 autorun-storage.ico
dr-xr-xr-x 3 tom  tom     2048 Jan 27  2012 SafeXs.app
-r-xr-xr-x 1 tom  tom  3280960 Jan 26  2012 SafeXs.exe
-r-xr-xr-x 1 tom  tom     1239 Jan 26  2012 SafeXs.exe.safesig
-r-xr-xr-x 1 tom  tom     5757 Jan 26  2012 warranty.txt

---

