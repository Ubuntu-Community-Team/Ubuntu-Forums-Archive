---
title: "Firefox wont load anything except Google"
date: 2009-10-01
forum: General Help
---

### Post by Anxious on 2009-10-01
i seem to have the same problem as stated here:[http://ubuntuforums.org/showthread.php?t=400497](http://ubuntuforums.org/showthread.php?t=400497)[B]  exactly the same simphtoms, but still cant find a solution, its stuck at about the half of the progress bar and wont load the site further, i tried deactivating ipv6 or activating pipelining, but wont do.

---

internet does work fine, can use pigeon everytime without problems, but still firefox refuses to do propper work.
[/B]

---

### Post by karlson on 2009-10-01
> **Anxious said:**
> i seem to have the same problem as stated here:[http://ubuntuforums.org/showthread.php?t=400497](http://ubuntuforums.org/showthread.php?t=400497)[B]  exactly the same simphtoms, but still cant find a solution, its stuck at about the half of the progress bar and wont load the site further, i tried deactivating ipv6 or activating pipelining, but wont do.

---

internet does work fine, can use pigeon everytime without problems, but still firefox refuses to do propper work.
[/B]

Can you get output of

```

telnet www.cnn.com 80
GET /

```

If you get nothing firefox is not your problem, so check 

```

traceroute www.cnn.com

```

or 

```

tracepath www.cnn.com

```

---

### Post by Anxious on 2009-10-01
telnet establishes the connection without a problem

> 
GET /
<HTML>0K<HTML>
Connection closed by foreign host.
 

---

### Post by lovinglinux on 2009-10-01
Try the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Anxious on 2009-10-02
Hm, i just tried to install another browser, Opera, and i did need some additional packets for it. And it seems like the problem is not just with Firefox, because the packet download is stuck at the start.

---

### Post by Giblet5 on 2009-10-02
Is it possible that your ISP is bouncing your connection?

I had a similar problem, though not as frequent, and it was a router on their end.

Try ```
ping ftp.x.org
``` and let it run for five minutes. Stop it with ^C. Look at the ending stats. Were any packets dropped?

---

### Post by Anxious on 2009-10-02
hmm no packets at all dropped. seriously, im confused...
best of all, if i start windows on the same machine or use my other pcs in the lan, it works just fine.

dont know if it matters, but the dns service in my router is open dns :|

( what really does confus me, i can surfe all google sub sites perfectly fine.. but no other site ..! )

---

is there a tool to see what exactly firefox does? so i could determine where hes stuck.

---

