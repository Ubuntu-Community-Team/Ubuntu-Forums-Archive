---
title: "Can't delete Empathy's logs!!!!"
date: 2011-06-29
forum: General Help
---

### Post by ?#Yhf%*&amp; on 2011-06-29
All I want to do is delete Empathy's chat logs. Every time I start a conversation with someone it shows a previous conversation. Can someone help me? **I am running Ubuntu 11.04 with Empathy 2.34.0.**

I have tried everything. I found Empathy's log folder and deleted it (multiple times), disabled chat logging, cleared it from within Empathy, everything. Any help would be appreciated.

---

### Post by pqwoerituytrueiwoq on 2011-06-29
```
rm -r /home/$USER/.local/share/Empathy/logs/*
```try that
if they stick around
```
sudo rm -r /home/$USER/.local/share/Empathy/logs/*
```

---

### Post by ?#Yhf%*&amp; on 2011-06-30
Didn't work. I have even deleted the whole Empathy folder and it doesn't go away. I have even deleted and re-installed Empathy and it is still stuck.

The problem is not the logs - it's the fact that ONE conversation with ONE user comes up every time I contact that user.

I'll keep trying and report if I find the solution.

---

### Post by pqwoerituytrueiwoq on 2011-06-30
you could mount it to a small ram disk then it would have nowhere to store the logs
add this to /etc/fstab
```
tmpfs /home/Corbin052198/.local/share/Empathy/logs tmpfs size=1M,nr_inodes=10k,mode=777
```edit your name as necessary
then ```
sudo mount -a
```

---

### Post by ?#Yhf%*&amp; on 2011-06-30
Sorry, "pqwoerituytrueiwoq," I found the solution before I saw your comment. See, it didn't matter what I did to Empathy's log folder. I deleted it several times. I even did a complete removal of Empathy in Synaptic Package Manager. Nothing worked.

**THE SOLUTION:**

**1.** Open the Empathy Buddy List.
**2.** Right-click on a user name, and click on 'Previous Conversations'.
**3.** Somewhere under the menus is an option to delete all chat history.
**4.** Select which accounts you want to clear the history of (I chose all of them) and click Clear.

Hopefully that will be helpful to someone else. :)

---

### Post by Samhain13 on 2012-05-05
> **Corbin052198 said:**
> Hopefully that will be helpful to someone else. :)

Indeed, it was. Thank you very much for the solution.

---

