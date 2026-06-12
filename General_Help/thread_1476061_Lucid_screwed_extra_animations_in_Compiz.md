---
title: "Lucid screwed extra animations in Compiz"
date: 2010-05-07
forum: General Help
---

### Post by vamc on 2010-05-07
I recently upgraded to Lucid from Karmic on my Acer Aspire 4736. Since update, I am unable to activate the 'extra-animations' effects in compiz. It worked fine with Karmic. Every thing else is working well. I am unable to sort out the problem. Anyone please help me out.

Thanks in advance.

---

### Post by McMichael96 on 2010-05-07
I got a fix. Run this in a terminal.


```
sudo apt-get install compiz-fusion-plugins-extra
```

Hope that helps :D

(Please tell me if it works on your PC)

---

### Post by McMichael96 on 2010-05-07
You will have to restart CCSM if you got it open. If it still dn't work, try restarting PC.

This worked for me, I had the same problem.

---

### Post by vamc on 2010-05-09
Thanks for your help McMichael. It solved my problem.
                            
                             :P:P:P

---

### Post by standingwave on 2010-05-17
Thanks for this. I missed the burn animation but since it wasn't a life or death issue for me, I just got around to googling for a solution and this thread popped up.

---

### Post by Solrac924 on 2010-05-23
after upgrading to Lucid i was really missing these animations. thanks for the fix. i never knew about "plugins-extra". 

Compiz rocks!

---

### Post by manjunath426jc on 2010-09-01
hey thr, I tried to run the above code but it didn't work . my laptop is acer 5738

---

### Post by Sef on 2010-10-17
The above command works with Maverick Meerkat, 10.10.o

Just copy and paste these commands into the terminal (Applications > Accessories > Terminal):

```
sudo apt-get update && sudo apt-get install compiz-fusion-plugins-extra
```

The first part insures that you have the latest version from the repositories.

---

