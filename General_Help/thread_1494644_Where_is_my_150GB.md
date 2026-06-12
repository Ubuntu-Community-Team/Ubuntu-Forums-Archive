---
title: "Where is my 150GB ?"
date: 2010-05-27
forum: General Help
---

### Post by Veren on 2010-05-27
Hello,
I recently made a dual-boot with win7 and Ubuntu.
When I installed win, I made 2 partitions, 150GB ond and 340GB one.
THe win and games were on the first one ( C: ) and the bigger one was empty ( D: ). Then I installed ubuntu for dual boot, I chose the first option there, install side by side. Everything works flawlessly, however, when I log into win I see C: as as it was, though D: is only 150GB big and it has  bootsqm.dat file there. That's enough space, however, I wonder where the rest moved. Is it safe to use it ? Thank you, I'm sorry for such a noob question but I'm curious. Thanks

---

### Post by blueturtl on 2010-05-27
Windows uses a different file system from the many possible ones Linux does.

You assumed was that Linux would install on drive D, correct?

What has actually happened is that Ubuntu resized drive D (which it couldn't use) to make room for itself. You cannot see the Ubuntu file system from Windows, although you can see your drive C and drive D in Ubuntu.

Does that make sense?

---

### Post by jerrrys on 2010-05-27
by installing side-by-side you created a partition and still have unused space.

---

### Post by Veren on 2010-05-27
> **blueturtl said:**
> Windows uses a different file system from the many possible ones Linux does.

You assumed was that Linux would install on drive D, correct?

What has actually happened is that Ubuntu resized drive D (which it couldn't use) to make room for itself. You cannot see the Ubuntu file system from Windows, although you can see your drive C and drive D in Ubuntu.

Does that make sense?

Yes, thank you, so as I understand it:
There is C: , which is normal as it was
Then the former D: has been split into 2 parts:
1st one is the "new" D: I can see in win
2nd one is the one using Ubuntu
Hope I got it right :)
Thanks

---

### Post by Jakiejake on 2010-05-27
> **Veren said:**
> Hello,
I recently made a dual-boot with win7 and Ubuntu.
When I installed win, I made 2 partitions, 150GB ond and 340GB one.
THe win and games were on the first one ( C: ) and the bigger one was empty ( D: ). Then I installed ubuntu for dual boot, I chose the first option there, install side by side. Everything works flawlessly, however, when I log into win I see C: as as it was, though D: is only 150GB big and it has  bootsqm.dat file there. That's enough space, however, I wonder where the rest moved. Is it safe to use it ? Thank you, I'm sorry for such a noob question but I'm curious. Thanks

I don't understand what you mean
Could someone tell me...

---

### Post by Veren on 2010-05-27
> **Jakiejake said:**
> I don't understand what you mean
Could someone tell me...

What is meant, basically, is that after I installed Win7 I had 150GB on C drive and 320 on D drive. Then I installed Ubuntu (dualboot) and I now have 150 on C and 160 on D. I was wondering where the rest was.

---

### Post by Jakiejake on 2010-05-28
> **Veren said:**
> What is meant, basically, is that after I installed Win7 I had 150GB on C drive and 320 on D drive. Then I installed Ubuntu (dualboot) and I now have 150 on C and 160 on D. I was wondering where the rest was.

Oh thanks but what is a bootsqm.dat file :confused:

---

### Post by blueturtl on 2010-05-28
> **Veren said:**
> Yes, thank you, so as I understand it:
There is C: , which is normal as it was
Then the former D: has been split into 2 parts:
1st one is the "new" D: I can see in win
2nd one is the one using Ubuntu
Hope I got it right :)
Thanks

You got it.

If you have any other questions regarding the file systems or directory structure in Ubuntu, fire away. :)

---

