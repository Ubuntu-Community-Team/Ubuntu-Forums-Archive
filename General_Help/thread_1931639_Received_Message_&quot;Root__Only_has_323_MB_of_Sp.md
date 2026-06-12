---
title: "Received Message: &quot;Root / Only has 323 MB of Space left&quot;"
date: 2012-02-25
forum: General Help
---

### Post by johnsmoke on 2012-02-25
Got this message and I'm not sure what to do. Root is where the OS is installed, correct? Should I be concerned with this? Is there anything I should do?

---

### Post by johnsmoke on 2012-02-25
Doesn't make sense, I check system monitor and there appears to be plenty of space.... I've attached a pic of it. Any advice would be appreciated.

---

### Post by johnsmoke on 2012-02-25
I think maybe it had something to do with K3B, I was burning some DVD's and the message came up then, maybe the temp folder was getting full? Why would it say the "root" folder then, if it was only the temp folder for K3b?

---

### Post by Dreamer Fithp Apprentice on 2012-02-26
If they are on the same partition, and it looks like they are, judging from your picture, then it wouldn't matter that it is a different folder. The whole partition is available to anything you put in either folder. So if you put a lot of stuff in any folder, that much less space is available to every folder on the same partition. Could be a problem with k3b. K3b was my burner of choice, despite the fact I was using mostly gnome, until Oneiric but now it doesn't work for me any more. I don't remember what kind of errors I was getting - it wasn't a big deal to me, I just switched to Brasero, which seems to have improved since I last tried it. But one new problem would suggest that some changes have been made and there could be more.  Another possibility - could you have had a lot more stuff in your trash can than you realized and emptied it in between the low space message and checking system monitor? It's been a while since I've seen the low space message but I believe it used to offer to DO something about the low space. Could it be it offered to empty the trash can as a default and you accepted it?

---

### Post by dcstar on 2012-02-26
> **johnsmoke said:**
> I think maybe it had something to do with K3B, I was burning some DVD's and the message came up then, maybe the temp folder was getting full? Why would it say the "root" folder then, if it was only the temp folder for K3b?

The temp folder is in the root filesystem, which is **exactly** what the message is referring to.

---

### Post by gordintoronto on 2012-02-26
So the solution is to change the "default temporary directory" in K3B.

---

### Post by johnsmoke on 2012-02-26
Thanks, I think I got it. I can create my own temp folder somewhere for K3B. Not sure why it was set to go to root.

---

