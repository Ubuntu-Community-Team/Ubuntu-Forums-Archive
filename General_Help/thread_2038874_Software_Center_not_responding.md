---
title: "Software Center not responding"
date: 2012-08-07
forum: General Help
---

### Post by Benjiboy180 on 2012-08-07
I searched he forum for similar problems, but nothing looked quite like what I have been experiencing (or the problem was a different situation, thus did not appy), so I am going to go ahead and post asking for help (partially just to build a base of things to try when I get home from work).
 
I just recently installed Voyager/Xubuntu 12.04 (first time Linux user, just got plain bored with windoze). I have been poking around the system trying to figure out the logic and whatnot behind how it is setup (I should probably buy a book or something, but hey, I am cheap). Needless to say, the Software Center definitely caught my attention (everything you might want software wise at your fingertips!). So I began downloading a few things I had researched. This is where the trouble begins.
 
I was in the middle of installing Claws mail client, as it heard it was better than Thunderbird, especially as of late and I am not committed enough to go straight to Mutt. In the middle of the install, the computer got extremely slow and unresponsive, to the point where I just had to manually power it off (it's older and has some...issues). When I turned it back on this morning, Software Center would boot up, but stay at the white screen. When I exited, it would say "Software Center is Unesponsive...etc). 
 
I tried the following:
 
```
1. sudo apt-get update
2. sudo apt-get purge software-center _and_ sudo apt-get install software-center
```
 
Originally 1 gave me some grief that I didn't fully understand about what I now think had to do with packages, though finally worked later. The second option, not surprisingly, didn't do jack.
 
Is this a probelm with broken packages to be addressed in package manager? Does someone else know what might be the problem? I am sure it won't be too difficult a fix, but as I said, I am pretty new to Linux, so trouble shooting it isn't my strong suit curently, though things like this add to those skills....
 
Thanks.

---

### Post by daslinkard on 2012-08-07
Try

```
sudo apt-get purge software-center
```

```
sudo apt-get install software-center
```

```
sudo apt-get update
```

---

### Post by Benjiboy180 on 2012-08-07
I already tried purging and reinstalling software center. I don't think I tried updating since I did that, so I can try it. But I am not exactly hopeful that will work. No offence.

---

### Post by daslinkard on 2012-08-07
Try the order that I gave you....first sudo, second sudo, etc.

---

### Post by Benjiboy180 on 2012-08-12
Ya, I tried it and nothing. Luckily the Lubuntu install was brand new, so I just decided to fresh install. I had a few other things I wanted to correct anyway. Thanks for your help either way.

---

