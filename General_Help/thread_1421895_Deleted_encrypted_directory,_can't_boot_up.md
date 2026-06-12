---
title: "Deleted encrypted directory, can't boot up"
date: 2010-03-04
forum: General Help
---

### Post by alexjohnc3 on 2010-03-04
When I used the Disk Usage Analyzer to find something I could delete off my computer to free up some space, I found a huge amount of data was in a Private folder. I didn't realize it until after I had deleted it, but apparently the encrypted folder was mirroring my hard disk. (The Disk Usage Analyzer showed it taking up exactly half of my data.) After permanently deleting the folder, I realized that that was a very bad idea, and after restarting the computer, I could no longer boot up. (It gives me some error message: "Could not update ICEauthority file.")

When I used to Live CD, the only thing I could see when I went into my hard disk was "Access my Private Data" and "README.txt". Clicking Access my Private Data doesn't do anything whatsoever. When I do "ecryptfs-mount-private" in the terminal, I get this message: "ERROR: Encrypted private directory is not setup properly"

Is there a way to fix this?

---

### Post by alexjohnc3 on 2010-03-06
Aside from reinstalling Ubuntu (again...) I don't know what to do. I've been running the Live CD for the time being... =\

---

### Post by alexjohnc3 on 2010-03-07
I've been looking all over Google for a solution, but no luck so far. Any ideas?

---

### Post by alexjohnc3 on 2010-03-07
Ok, good news is that *for some reason* the encrypted directory wasn't permanently deleted. Now I'm just not sure where to put it so that it will be unencrypted when I log back in.

Originally the only things I could see on my hard drive were "Access Your Private Data" and "README.txt". In the .Trash-0 folder, after checking the option to see hidden files, I found the stuff I deleted: two folders named .ecryptfs and .Private. Where should I put them?

---

### Post by alexjohnc3 on 2010-03-09
This should be pretty simple to fix if someone could help me out. =(

---

### Post by alexjohnc3 on 2010-03-09
There has to be some way to fix this. I have all the data still (.ecryptfs and .Private); I just don't know where to put them so that I'll be able to boot up/access my files normally. I REALLY don't want to have to reinstall my entire operating system again, but at this rate it looks like I'll have to unless someone can help me out soon...

---

### Post by MasterNetra on 2010-03-09
Hold I'll check to see if I can find it on my system

---

### Post by MasterNetra on 2010-03-09
The .Private folder goes into your home directory as does .ecryptfs. Straight in your home directory no placing them in subfolders. And by Home directory I mean /home/*InsertUserName*/

---

### Post by alexjohnc3 on 2010-03-09
> **MasterNetra said:**
> The .Private folder goes into your home directory as does .ecryptfs. Straight in your home directory no placing them in subfolders. And by Home directory I mean /home/*InsertUserName*/
That did the trick!! Everything works fine now, and I'm back in my account. Thank you so much! :D

---

### Post by MasterNetra on 2010-03-09
> **alexjohnc3 said:**
> That did the trick!! Everything works fine now, and I'm back in my account. Thank you so much! :D

Your welcome! Don't forget to mark the thread as solved! (View your thread, and near the top should be "Thread Tools" click once and a menu should appear, last option.)

---

