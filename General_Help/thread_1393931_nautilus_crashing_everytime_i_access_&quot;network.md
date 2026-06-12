---
title: "nautilus crashing everytime i access &quot;network&quot;"
date: 2010-01-29
forum: General Help
---

### Post by inphektion on 2010-01-29
i just got some updates today on my jaunty system (not sure if its related) but now everytime i open nautilus and double click network a window flies open then closed.  Same will happen if I go to places -> connect to server... enter the details then it connect, windows opens then closes.  
Literally just started after the updates.  anyone experience same?
what can i look at to try to fix?

---

### Post by inphektion on 2010-01-29
in dmesg i get this:

[  127.329483] nautilus[4516]: segfault at 7972746e45 ip 00007f3c8fd35169 sp 00007fff35ef08b0 error 4 in libglib-2.0.so.0.2200.3[7f3c8fcdb000+c6000]
[  139.456360] nautilus[5170]: segfault at 9 ip 00007f185a9b0d08 sp 00007fffcb047ac0 error 4 in libglib-2.0.so.0.2200.3[7f185a97d000+c6000]
[  150.478403] nautilus[5195]: segfault at 7f0065707954 ip 00007fe8b8b0a169 sp 00007fffba34f3f0 error 4 in libglib-2.0.so.0.2200.3[7fe8b8ab0000+c6000]

---

### Post by inphektion on 2010-01-29
command line mounting of the shares still works with full access.  def just nautilus crashing.

---

### Post by inphektion on 2010-01-30
anyone?

---

### Post by crh0831 on 2010-02-01
I had the same problem and solved it by rolling back libglib2.0 (which just came as part of the end of January 2010 updates)  I'm not sure what the problem is but going back to old version let me access "Network" connections again...

See this thread: [http://ubuntuforums.org/showthread.php?t=1395237](http://ubuntuforums.org/showthread.php?t=1395237)

hth

---

