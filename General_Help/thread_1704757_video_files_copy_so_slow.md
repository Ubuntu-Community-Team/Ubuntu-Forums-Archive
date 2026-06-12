---
title: "video files copy so slow"
date: 2011-03-11
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-03-11
is it normal for video files to take an extremely long time to copy/cut? i can move other files (dvd isos, etc) of about the same size and even much larger around like it was nothing, but trying to move videos around is painful. it doesnt take very long to copy to and from an esata drive, but from spot a to spot b on same disc, or between 2 partitions or physcal discs.. very long.. and if i try to usb-- i could almost watch the movie in the time it takes and really could format, copy iso of ubuntu and make boot of in the amount of time it takes to copy a 700mb avi. it is not an avi issue either, as i have same problems with mp4, mkv, etc. 
  especially to usb (which i have no problem with on other similar sized files) it will freeze so many times, especially at the end, be almost done and then take 4+ minutes to be done. the usb is formatted to fat32, so its not an issue with ntfs like the harddrives might be. the issue is not present in my windows boot. i have a pretty fast machine in all other aspects, so is this just an ubuntu issue i will have to deal with or is it fixable?

---

### Post by HermanAB on 2011-03-11
Howdy,

Look at the size of the files, that should explain it.

---

### Post by SE7EN-LOCSTA on 2011-03-11
i understand the file size is somewhat large, but it takes much longer to copy a video file than a differnt kind of file of a larger size.. and the issue is not present on my windows boot.

---

### Post by tordeu on 2011-03-11
Do you know how to copy files from command line? It would be interesting to see if the problem does occur this way, too. I have not had such a problem before, but maybe we should try to test if the problem is Nautilus related or not. 

EDIT: Plus, we could time how long it takes from one location to another in comparison. Maybe this helps locating the problem as well.

---

### Post by SE7EN-LOCSTA on 2011-03-11
@tordeu.. i am not very familiar with the command line. i seen 'cp' to make a copy of a file under a different name, and 'mv' to move a file from spot a to spot b.. but as far as taking a file, and copying directly to another location, i am unsure of. 

is there a built in timer-feature that would show the time for both copying in commandline and nautilus, or do i need to keep track of time myself?

---

### Post by tordeu on 2011-03-12
Okay, I could walk you through the steps. I would recommend that we start with copying files in command line and measure the time with "time", so that we can see if there is a difference in command line. This way we know if the problem has to do with Nautilus.

The first thing you could do is to find a video file and a data file which are at least almost the same size, so that we can use them for testing. (you could just create a tar- or zip-file of that video. This would have the about same size).

And then we need to decide from which location to which location we will copy the files. Does the problem also occur if you have the file in your home folder and create a copy of that file in your home folder (i.e., copying from home folder to home folder)?

If that is the case, we can now measure the time to copy the files. Let's say we have a video named test.avi and a data file named test.zip, which are now both in your home folder.

In command line, you could now do the following to go to your home folder
```

cd ~

```

then we measure the time it takes to copy the video from your home folder to your home folder
```

time test.avi test2.avi

```

This will copy the file and then output three times. You do not need to use a stopwatch or something, the "time" function will do that for you.

After that, we can copy the data file and measure the time it takes:

```

 time test.dat test2.dat

```
 
Then copy & paste the ouput of both time commands and tell me how big the files were.

If copying from your home folder to your home folder is not a problem then we try something else.

---

### Post by gabak on 2011-03-27
hello everyone
did somebody solve this?
i have the same problem  !!!
Question ubuntu 10.10 Very SLOW file copy speed (disk to disk)
i have amd athlon x2 3gb RAM ddr2 two hdd one 80gb other 1tb
in this computer i got only ubuntu all disk in EXT4
i want to copy 10gb many file of 700mb or 1gb ( many linux ISO )

the transfer is 1mb/s this is SOOO SLOW !!!

i did a touch /forcefsck just in case but nothing happen it is still slow!!
what might be the problem ??

---

### Post by tordeu on 2011-03-27
Unfortunately, I don't know if the problem is somehow fixed or not. Could you please post the following information:

- Do you use any kind of encryption?
- Please post the exact models of your drives
- Did you have this problem the whole time or did it start some day?
- Is the transfer only slow when you copy from the 80GB to the 1TB or also when you transfer from 80GB to 80GB or 1TB to 1TB?

I really hope we can find a fix for the problem, because this seems to affect several people.

---

### Post by gabak on 2011-03-28
i had the same problem , it was the sata data cable that was a little loose. then wow !! everything changed !!
if you solve ur problem plz let's know.
and change the status of this post to SOLVED



> **SE7EN-LOCSTA said:**
> is it normal for video files to take an extremely long time to copy/cut? i can move other files (dvd isos, etc) of about the same size and even much larger around like it was nothing, but trying to move videos around is painful. it doesnt take very long to copy to and from an esata drive, but from spot a to spot b on same disc, or between 2 partitions or physcal discs.. very long.. and if i try to usb-- i could almost watch the movie in the time it takes and really could format, copy iso of ubuntu and make boot of in the amount of time it takes to copy a 700mb avi. it is not an avi issue either, as i have same problems with mp4, mkv, etc. 
  especially to usb (which i have no problem with on other similar sized files) it will freeze so many times, especially at the end, be almost done and then take 4+ minutes to be done. the usb is formatted to fat32, so its not an issue with ntfs like the harddrives might be. the issue is not present in my windows boot. i have a pretty fast machine in all other aspects, so is this just an ubuntu issue i will have to deal with or is it fixable?

---

### Post by tordeu on 2011-03-28
Thanks for mentioning the SATA cable, I would have not thought of that. Maybe this is something he can check. It might be that videos are the only large files he copies and therefore only notices the problem with them.

---

### Post by gabak on 2011-03-28
- Do you use any kind of encryption?
NO I DONT
- Please post the exact models of your drives
80GB WDC WD800BD-22MRA1
1.0 TB SAMSUNG HD103UJ
- Did you have this problem the whole time or did it start some day?
it started few days ago, i guess it was when i put a new dvd-rw drive.
- Is the transfer only slow when you copy from the 80GB to the 1TB or also when you transfer from 80GB to 80GB or 1TB to 1TB?
it was slow for everything, but now i found the problem everything back to normal. i had transfer at 900kb/s now 30mb/s :-)

I really hope we can find a fix for the problem, because this seems to affect several people.[/QUOTE]

---

### Post by tordeu on 2011-03-28
Well, because it was your cable, you would not have needed to supply the information anymore. ;) But if there are several people who have this problem, maybe there is something they all have in common. But nevertheless, thank you for posting your fix. Maybe this is something which helps other who experience this problem. It's certainly a valid point to check the cables. Especially, cause it only takes seconds.

---

