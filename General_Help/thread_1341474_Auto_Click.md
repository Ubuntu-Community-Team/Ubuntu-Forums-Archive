---
title: "Auto Click"
date: 2009-11-29
forum: General Help
---

### Post by jluda on 2009-11-29
First im wasnt sure where to post this so i apologize if its inconveniently in wrong place.

Id like to write a program, script anythin that will click for me at certain coordinates. I was wondering if anyone could help me out, i am very curious if its possible. I have had 2 years in JAVA and half a semester in C++. But i am willing to pick up anything to work with this. 

Thanks to anyone who can help.

---

### Post by Agent ME on 2009-11-29
Install [xdotool](apt:xdotool). With that, this terminal code can do what you want (this will click on the Places button in ubuntu):
```
xdotool mousemove 150 10; xdotool click 1
```

---

### Post by jluda on 2009-11-29
The link you provided did not work =/

---

### Post by raktarok on 2009-11-29
```
sudo apt-get install xdotool 
```
Works for me!

---

### Post by jluda on 2009-11-29
does it make a difference that im running Hardy Heron?

---

### Post by raktarok on 2009-11-29
Um..probably. Did you enable all the repos(backports and universe)? Anyway, here is a download link. but beware, this is a karmic package, it may not work properly in hardy.
[http://mirrors.rit.edu/ubuntu/pool/universe/x/xdotool/xdotool_20090330-1_i386.deb](http://mirrors.rit.edu/ubuntu/pool/universe/x/xdotool/xdotool_20090330-1_i386.deb)
You can also snoop around this mirror to see if there is a package for hardy.

---

### Post by raktarok on 2009-11-29
Here is the link for hardy. Hope this helped!
(you have not enabled universe in your repos, probably..)
[http://mirrors.rit.edu/ubuntu/pool/universe/x/xdotool/xdotool_20080720-1%7ehardy1_i386.deb](http://mirrors.rit.edu/ubuntu/pool/universe/x/xdotool/xdotool_20080720-1%7ehardy1_i386.deb)

---

### Post by jluda on 2009-11-29
just to check how do i enable universe in repos?

---

### Post by raktarok on 2009-11-29
Go to System > Administration > Software Sources. There, you can tick mark the universe part.
Or edit the file /etc/apt/sources.list.

---

### Post by jluda on 2009-11-29
i have it selected but link you sent worked thank you so much.

---

