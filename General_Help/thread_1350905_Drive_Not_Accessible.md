---
title: "Drive Not Accessible"
date: 2009-12-09
forum: General Help
---

### Post by hawk007 on 2009-12-09
I installed ubuntu successfully and have configured some software on it. I plan to have users upload files. However they are now pointed to a folder called /webspace on the server.
 
I Installed ubuntu on a 72.8 gig HD but used only 19gig for ubuntu and sooftware. Call this Drive C.
 
But the space (Logical Volume is it called?) i partitioned, ie: the other 51 gig (Seperate HArd Drive lets call it D Drive) isnt showing or accessible. My question is this. 
 
How can i make the Drive D visible and usable so i can point user files to a folder on that drive D.
 
Many thanks for any assistance.

---

### Post by zdunham on 2009-12-10
Hi. I am assuming you created these two partitions during the Ubuntu setup?

Open a terminal and enter the following:

```

mount

```

Paste back the output here if you could and I'll see if I can figure something out.

---

### Post by cariboo on 2009-12-10
How is your extra partiton formatted? Is it ntfs, ext4 other? I'm going to assume because you are using windows terminology that it will be formatted as ntfs.

---

### Post by zdunham on 2009-12-10
> **cariboo907 said:**
> How is your extra partiton formatted? Is it ntfs, ext4 other? I'm going to assume because you are using windows terminology that it will be formatted as ntfs.

Just a side note....the number of posts you have made is impressive. You MUST be a guru haha.

---

### Post by zdunham on 2009-12-10
> **zdunham said:**
> Just a side note....the number of posts you have made is impressive. You MUST be a guru haha.

Then I realize you are staff and realize that I'm an idiot for not seeing that.

---

### Post by hawk007 on 2009-12-10
> **zdunham said:**
> Hi. I am assuming you created these two partitions during the Ubuntu setup?
 
Open a terminal and enter the following:
 
```

mount

```
 
Paste back the output here if you could and I'll see if I can figure something out.
 
 
I created the partitions on Proliant DL580 Accellorator array. I couldnt work it out during the instalation otherwize i would have created partitions for boot, var etc.
 
I installed ubuntu on the 19gig partition. Then when viewing the system from hostingcontroller (on windows 2003), and saw that there were no drives to choose ffro. Juts the "webspace" folder on the ubuntu 19gig partition. 
 
I created the partitions this way to keep user files seperate from anything i installed on the 19 gig partition. Hope that helps.

---

### Post by hawk007 on 2009-12-10
> **cariboo907 said:**
> How is your extra partiton formatted? Is it ntfs, ext4 other? I'm going to assume because you are using windows terminology that it will be formatted as ntfs.
 
Yes the partition is ntfs. Created with Array Accellerator on proliant dl580. Before ubuntu was installed.

---

### Post by hawk007 on 2009-12-10
> **zdunham said:**
> Just a side note....the number of posts you have made is impressive. You MUST be a guru haha.
 
LOL, thought you were talking about me. If theres a qualification for not having a clue about linux systems then yes i am a MASTER GURU. (The Guru of Gurus. heheh.)
 
 
By the way, thanks for responding everyone. Gurus and all.

---

### Post by zdunham on 2009-12-11
> **hawk007 said:**
> I created the partitions on Proliant DL580 Accellorator array. I couldnt work it out during the instalation otherwize i would have created partitions for boot, var etc.
 
I installed ubuntu on the 19gig partition. Then when viewing the system from hostingcontroller (on windows 2003), and saw that there were no drives to choose ffro. Juts the "webspace" folder on the ubuntu 19gig partition. 
 
I created the partitions this way to keep user files seperate from anything i installed on the 19 gig partition. Hope that helps.

Well I am no guru so this is probably out of my league. Sorry I couldn't be of more help! Hopefully someone can figure it out for you.

---

### Post by hawk007 on 2009-12-11
Anyone have a clue??? Il go to another forum, maybe with more luck.

---

