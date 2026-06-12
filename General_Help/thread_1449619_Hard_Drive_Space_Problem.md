---
title: "Hard Drive Space Problem"
date: 2010-04-08
forum: General Help
---

### Post by Luke Fleeman on 2010-04-08
Hello All:

I have a strange and complicated problem. My fiancee could not find pictures she needed, so I ran the program recoverjpg on our computer. The result was it filling up my hard drive completely. This caused all kinds of problems, but i have finally managed to get back onto my computer fine. 

I made enough space to have 10 GB open, and everything is running fine. However, I want to get rid of some 120,000 pictures that recoverjpg dropped in my home folder. The problem is that those pictures have permissions only for the root. 

I opened nautilus, and changed the permission of the file and everything in it, but they still show my main user as unable to edit them. So I just started deleting pictures through nautilus, which is a long and complicated process, very slow. And the pictures do not go to my trash, they just disappear. 

This has produced a different problem. My disc space is actually going down. Before deleting almost 5000 pictures, I had 10.1 GB. Now I have 9.3 GB. Worse yet, when I restarted, it showed 9.2. So it appears to be going down. 

This is my big, complicated problem. I need the following solutions:

1. How can I change the permissions of my home folder so I can delete these pictures?

2. Why is my capacity reducing?

3. Is there a faster way to come through all these pictures?

Thanks in advance.

---

### Post by terrrorr on 2010-04-08
Hi,

Terminal is your friend in this case.

1. Open terminal
2. Locate the directory where these stubborn files exists (/home/username/stubborn-dir)
3. Use this command

```
sudo chown -R username:group /home/username/stubborn-dir
```

4. Now you can delete it by using command
```
rm -d -R -f /home/username/stubborn-dir
```

For disk usage you could use Ubuntu's Disk Usage Analyzer to locate which directory consumes your HD's capacity. You can locate it from Application->Accessories-> Disk Usage Analyzer

Let me know if you need more detailed information

---

### Post by Luke Fleeman on 2010-04-08
I used chown, and I was having problems with a file not allowing it. I simply unmounted that file and then ran it again, and it worked. Thanks for the idea.


My fiancee is now going through the pictures and deleting the extraneous ones, but I still have something happen where whenever we delete data, the total available space still goes down. Any ideas?

---

### Post by Luke Fleeman on 2010-04-08
OK, it appears to be something weird. Disk usage shows I have over 25 GB available, but my  files don't reflect that/. Either way, I'm ok. Thanks for the help.

---

### Post by plucky on 2010-04-08
> **Luke Fleeman said:**
> OK, it appears to be something weird. Disk usage shows I have over 25 GB available, but my  files don't reflect that/. Either way, I'm ok. Thanks for the help.

Take out the Trash.

Howto see [here](http://ubuntuforums.org/showthread.php?t=898573&highlight=drs305)

Good Luck

---

### Post by Luke Fleeman on 2010-04-08
Ok, I was wrong. I tried emptying the trash, per the previous poster's suggestions, and I was actually deleting pictures. However, now the file that was full of pictures is showing it has MORE items than it did before. Is it possible that it is still finding new files and dropping in my home folder?

---

