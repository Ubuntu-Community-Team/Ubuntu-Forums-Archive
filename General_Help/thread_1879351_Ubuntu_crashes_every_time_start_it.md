---
title: "Ubuntu crashes every time start it"
date: 2011-11-11
forum: General Help
---

### Post by ApoFlo on 2011-11-11
[LEFT]Hello,[/LEFT]
 
I've downloaded Ubuntu 11.10 from a CD-rom that a friend of mine gave me.
Everything went well for a few days, then, just yesterday, i was unable to get wireless connection on Ubuntu, while Windows (!) could find it without problems.
 
Then today, I tried to log on several times, and my computer totally freezed and crashed several minutes afterwards. 
Last time i didn't even have to log on to have it as frozen as an ice cube :confused:
I had to wait for the battery to get empty in order to restart it.
And I insist on the fact that Windows never crashed on my computer.
 
What should i do? Uninstall Ubuntu and re-download it on the official site? 
 
Please help me.

---

### Post by raja.genupula on 2011-11-11
post here the output of ```
dmesg
``` command .

---

### Post by ApoFlo on 2011-11-11
Well, i just tried to. Computer crashed twice, and the third time, i was able to enter "dmesg" on the Terminal, and got a pretty long result.
Then (i don't know if it is normal) Ubuntu seemed to work fine (except for the wireless).
Then -no kidding- it crashed again before I could paste the results.

---

### Post by raja.genupula on 2011-11-11
ok do this 

```
dmesg > log.txt
```

and attach that file here from attachments .

---

### Post by ApoFlo on 2011-11-12
ok, here's the file (being too long for the forum, i cut it in pieces using a python script - I hope the result is somehow convincing and readable)
thanks

---

### Post by ApoFlo on 2011-11-12
sorry again, i just saw file 1 did not load, i had to cut it in pieces, using same algorythms... i am very sorry for all the disturbance :(

---

### Post by linuxuser12345 on 2011-11-12
Just uninstall Ubuntu 11.10 and put 11.04 on it for now. 11.04 is MUCH more stable at the moment.

---

### Post by ApoFlo on 2011-11-14
Is there no other solution?
If no, i certainly will :) Thanks a lot!

---

### Post by ApoFlo on 2011-11-15
Oh, by the way, I recently heard that installing Python 3.2 on Ubuntu might cause severe compatibility problems (because of Python 2). Is that true?

---

### Post by 2F4U on 2011-11-15
Since Python is an important component in most modern Linux distributions, this is most likely true.

---

### Post by ApoFlo on 2011-11-15
Then, it might somehow explain the crashing problems?
What would I have to do to uninstall Python 3.2 and re-install it in a way that won't cause troubles?

---

