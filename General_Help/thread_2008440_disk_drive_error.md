---
title: "disk drive error"
date: 2012-06-22
forum: General Help
---

### Post by ciscoboy on 2012-06-22
Hello,

I got a message reading that ubuntu was scanning for the disc drives for errors. Now I don't believe that there is something wrong with my drives (but I'll double check just to be sure), but I was wondering what would be the best way to correct drive problems, should I ever need it.

Thank You

Ciscoboy

---

### Post by broomemike on 2012-06-22
I believe that it check each partition after every xx mounts, as well as any unsafe unmounting, so there's probably not anything wrong. If there were, that would probably have found and corrected the problem.

I think that just addresses software issues, though...

Check out gsmartcontrol if you want to test your hardware more thoroughly for errors.

But I don't know how often you see a hard drive failure coming, lol

---

### Post by ciscoboy on 2012-06-22
how do you activate and/or use gsmartcontrol? You also mentioned that it checks disk errors every few months. Only thing is, I only installed ubuntu this week; should it be something that I should worry about or not?

---

### Post by broomemike on 2012-06-23
Every few "mounts". Not months... Your pc mounts all the drives at boot up, so if you're rebooting a lot, this can come quickly.
That's one of the big advantages to the default filesystem (ext4) which does the check very quickly.
So no, I wouldn't worry.
You can install gsmartcontrol with
sudo apt-get install gsmartcontrol
Then just find it on your menu. It's a safe program, so play around with it. It only scans, so it won't break anything. Feel free to go nuts with the Extended Self-Test if you're worried.
Maybe start it up before you go to bed for the night...

---

### Post by ciscoboy on 2012-07-07
I installed the program, but I dont know how to use it. Could you show me how, or show me a place that could show me how?

---

### Post by broomemike on 2012-07-07
You run it... Right-Click on a drive and click perform tests. Then pick some tests. The extended self-test is the most rigorous, but it is quite long. 

Just play around with it. If you're having specific troubles let me know. But there's not much to learn that's not obvious from reading it. Don't get bogged down reading incomprehensible logs before running tests, though.

---

