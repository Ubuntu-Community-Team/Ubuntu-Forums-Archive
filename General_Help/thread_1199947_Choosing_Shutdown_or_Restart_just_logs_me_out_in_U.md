---
title: "Choosing Shutdown or Restart just logs me out in Ubuntu 9.04!"
date: 2009-06-29
forum: General Help
---

### Post by motang on 2009-06-29
I have noticed this for quite sometime now, and it wasn't really bothering me much till the hot weather hit (as I tend to turn my desktop off more since it get really hot in my room). Here is my problem, whenever I got to shutdown or restart on both my desktop and laptop Ubuntu just logs me out and then from the log on screen I can choose shutdown or restart then it works as it suppose to. I don't know what, but 8.10 earlier versions were working as they were suppose to. If I type in *shutdown -r now* or *shutdown -h now* it works fine.

---

### Post by binbash on 2009-06-29
I have same problem on Ubuntu Karmic for a week.Bump

---

### Post by Laysan_A on 2009-06-29
I don't know if mine is the same, or not. I don't go to the login screen - it just logs out and doesn't shut down without reisub. It's been like that for just a few days now.

---

### Post by motang on 2009-06-29
Hmm, looks like I am not the only one with this problem, there might more people with this. I would like to file a bug report on launchpad but I don't what call it. Any suggestions?

---

### Post by Laysan_A on 2009-06-29
Not me. I don't have a clue what's happening. The only thing I've noticed in my logs is an entry in my kernel log (orig. from dmesg.log) that says this during initial boot (first time it's turned on):
> 2009-06-29 10:36:08    PM    Resume from disk failed.


---

### Post by swappa on 2009-07-10
Have the same issue. Ubuntu Jaunty x64. Started a few days ago.

---

### Post by neuralsimulation on 2009-07-18
I also have this issue, and it started a few days ago for me as well.

I hope it's not some kind of hijack!

---

### Post by motang on 2009-07-18
Should we report a bug report on Launchpad? If so what is process as I haven't done it before.

---

### Post by Sidewinder1 on 2009-07-18
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by waraltca on 2009-09-30
guys...
did you find the solution to this problem??
I have the sameone.

---

### Post by motang on 2009-09-30
Nope, not yet.

---

### Post by Giblet5 on 2009-09-30
Yes, if you leave applications running, you'll be logged out instead of shutting down or restarting.

This is clearly a bug.

Workaround:
Close all of your terminals, web browsers, IM clients, email apps, etc., then it will shut down.

---

### Post by motang on 2009-09-30
Oh hmm...I wonder what programs were left open, I shall pay more attention to it next time. Thanks.

---

### Post by azLinux on 2010-07-08
I have this issue right after logging in so it can't be an "open programs". This seems like a very strange issue to me that shouldn't be in an OS as mature as Ubuntu. Does anyone have a clue what is going wrong?

Behavior:
At the log in screen neither "Restart" nor "Shutdown" menu items do anything.

After logging in and going to restart or shutdown I get logged out but just go back to the log in screen. 

please help!

---

### Post by Gargoulf on 2010-07-09
> **azLinux said:**
> I have this issue right after logging in so it can't be an "open programs". This seems like a very strange issue to me that shouldn't be in an OS as mature as Ubuntu. Does anyone have a clue what is going wrong?

Behavior:
At the log in screen neither "Restart" nor "Shutdown" menu items do anything.

After logging in and going to restart or shutdown I get logged out but just go back to the log in screen. 

please help!


Same pb with ubuntu 10.04. restart or shutdown just logs me out!!!

---

### Post by Gibbs on 2010-07-09
Have you tried to shut down from the terminal?

```
sudo shutdown -h now
```

That's what I did when I had this problem once. After the next boot I could shutdown normally.

---

