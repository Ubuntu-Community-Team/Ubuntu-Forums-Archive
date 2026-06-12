---
title: "Ubuntu Software Center has no software..."
date: 2010-06-01
forum: General Help
---

### Post by IWC316 on 2010-06-01
When I went to Ubuntu Software Center it had no software listed.  I am having problems with VLC playing a video so I thought I would reinstall it.  There is not any software listed in the "installed software" either!  

What is the deal?

Running 10.04

---

### Post by mac9416 on 2010-06-01
Hi, IWC316.

Very strange. I would first suggest running 'sudo apt-get update' in the Terminal to update the package lists. Then I would run 'software-center' from the Terminal so you can see any error output.

Another way to reinstall VLC would be to these command in the Terminal.

```
$ sudo apt-get remove vlc --purge  # --purge removes config files. Omit it if you'd rather keep them.
$ sudo apt-get install vlc
```

---

### Post by IWC316 on 2010-06-01
I forgot to add that if you click on "installed software" there is nothing listed but if put something into the search it will show up.  From there I tried to remove VLC but it had an error. 

So after your post I did both of the runs in the terminal that you suggested with no change except that I could search VLC and remove it.  

When I ran the first string in the terminal I got...

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

So I did, and then ran software center in the terminal and got nothing it just went back to the prompt.

I have not done much sense the install so it would not be a big deal to reinstall but if I do not have to that would be great!

---

### Post by IWC316 on 2010-06-02
?:(

---

### Post by IWC316 on 2010-06-02
I was excited about getting this thing up and running.  I tried 9.10 and 10.04 on another computer I had with no luck.  For some reason the netbook 10.04 worked on it but I scrapped that venture when someone gave me this computer.  I had to switch out some drives but I got 10.04 on here and after finding some drivers I was in business.  Now I can't get software and this is becoming a drag.  I am sure there is a fix!  I am not big into computer stuf but I find it fun to tinker with.  The good part of this problem is that I have used the terminal!  Either way I would love to get back at setting this dude up!

---

