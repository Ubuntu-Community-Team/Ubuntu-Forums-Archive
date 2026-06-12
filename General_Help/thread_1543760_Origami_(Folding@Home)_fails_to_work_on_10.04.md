---
title: "Origami (Folding@Home) fails to work on 10.04"
date: 2010-08-01
forum: General Help
---

### Post by caecusum on 2010-08-01
I just did a fresh install of 32bit Ubuntu 10.04 on my desktop and am trying to get some F@H clients working.

I installed Origami and did a
```
sudo origami install -t blah -u blah -b big
```
and got the error "STARTUP SCRIPT FAILED TO START!"

Then doing```
sudo origami start
``` gives me "UNABLE TO START LOCAL SERVICE" with no other output

Lastly, I tried
```
sudo service origami start
```
and got ```
Starting up FAH client(s) on 4 processor(s):
Starting FAH client at CPU1...
FAH client #1 startup: OK 
Starting FAH client at CPU2...
FAH client #2 startup: OK 
Starting FAH client at CPU3...
FAH client #3 startup: OK 
Starting FAH client at CPU4...
FAH client #4 startup: OK 


Starting of FAH client(s): FAILURE
```

I have looked for solution but the only bugs I see seem to be related to missing ia32-libs, but I am doing this on a 32 bit installation.  I have also made sure to get NSCD running in case that is a problem but it did not resolve the issue.

Edit: Also, for the record, Origami prints a message to check bugs.launchpad.net/origami which is not active

---

### Post by willjammn on 2010-08-01
I've never used F@H, but sometimes I visit the EVGA forums and noticed they are really big on F@H.

So here is some stickies they have put up.concerning folding with GNU/Linux.

[http://www.evga.com/forums/tm.aspx?m=1305](http://www.evga.com/forums/tm.aspx?m=1305)

Here is another one, I don't think it is posted in the Linux collection yet.

 [http://www.evga.com/forums/tm.aspx?m=312520](http://www.evga.com/forums/tm.aspx?m=312520)

---

### Post by caecusum on 2010-08-01
Thank you.  It is mentioned that there is an incompatibility with the version of glibc installed in 10.04

I suppose I will just have to wait.

---

### Post by Routhinator on 2010-12-19
Has anything changed with this issue? I'm having the exact same issue, and it's been months since anyone's updated this one.

---

### Post by Nounours18200 on 2011-09-20
I also use Ubuntu 10.04LTS, and to date (September 19th, 2011) I still have the pb.

Any suggestion ?

---

