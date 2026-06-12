---
title: "How to tell how much free HD space?"
date: 2012-03-05
forum: General Help
---

### Post by mjp29mjp29 on 2012-03-05
How do you tell how much free HD space is on the HD?

---

### Post by spiky001 on 2012-03-05
Hi

Try ```
 df -h
```

or ```
 df -h /dev/sda1
```

change sda1 for what ever partition you want

---

### Post by MG&amp;TL on 2012-03-05
Open Disk Usage Analyser, then look at the pretty pie chart. :)

---

### Post by ajgreeny on 2012-03-05
> **MG&TL said:**
> Open Disk Usage Analyser, then look at the pretty pie chart. :)
That's not much use for seeing free space.  The top level that you use is shown as being 100%, ie, no free space is taken into account.

Go with spiky001's suggestion which gives the answer in easily readable output.

---

### Post by MG&amp;TL on 2012-03-05
> **ajgreeny said:**
> That's not much use for seeing free space.  The top level that you use is shown as being 100%, ie, no free space is taken into account.

Go with spiky001's suggestion which gives the answer in easily readable output.


Could you elaborate? It shows the free space for me. 

I completely agree with you, *df* is the way to go, but I was not sure on the OP's level of experience.

---

### Post by HiImTye on 2012-03-05
> **ajgreeny said:**
> That's not much use for seeing free space.  The top level that you use is shown as being 100%, ie, no free space is taken into account.

Go with spiky001's suggestion which gives the answer in easily readable output.
it shows the usage properly for me (save for where it is not able to due to permissions)

I would use 'df -h' though

---

### Post by undeuxtrois on 2012-03-05
Hello all,

I guess a more "GUI friendly" solution would be to simply look at the bottom status bar of the file manager (PCManFM) window! It displays the free space count for the partition you are currently browsing...

P.

---

### Post by ajgreeny on 2012-03-06
> **HiImTye said:**
> it shows the usage properly for me (save for where it is not able to due to permissions)

I would use 'df -h' though
Whoops!  I see you are correct.  It shows how seldom I have used the DUA as I have never seen much need for it.  However, it does always show the top level of the display as 100% which often confuses users.

---

