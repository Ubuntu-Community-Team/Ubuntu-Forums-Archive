---
title: "what will command rmmod 8169 do"
date: 2009-06-30
forum: General Help
---

### Post by 10ghost on 2009-06-30
i just ran the command
rmmod 8169 on a hp pavilion
i noticed that the wired network stopped working 
how can i correct this problem? 
this is emergency because i need it to repair the wirless and install build essential 
please help me 
i need your help badly.

---

### Post by 10ghost on 2009-06-30
please help me 
what can i do to reverse this command

rmmod 8169

or how can i install it again on the computer
please help me

---

### Post by 10ghost on 2009-06-30
i just ran the command 
rmmod 8169 
on a friends computer
while troubleshooting the wireless problem

After i did it the wired network stopped working what can i do to reverse this 
or how can i install it again on the computer.
pls help me

---

### Post by Idefix82 on 2009-06-30
Do you mean r8169? You removed the module responsible for the wired connection. To bring it back, do
```
sudo modprobe r8169
```

Do you mind me asking, why you executed the command in the first place, especially not knowing what it did?

---

### Post by Idefix82 on 2009-06-30
Stop posting the same topic several times and don't bump threads within minutes.

---

### Post by mhgsys on 2009-06-30
try :

```

sudo modprobe 8169

```

or maybe it's r8169

---

### Post by t4thfavor on 2009-06-30
your sig should be pebkac for Problem Exists Between Keyboard And Chair!

---

### Post by mhgsys on 2009-06-30
Dude!

Same topic
Got the same answer from me at;
[http://ubuntuforums.org/showthread.php?p=7540319&posted=1#post7540319](http://ubuntuforums.org/showthread.php?p=7540319&posted=1#post7540319)

---

### Post by mhgsys on 2009-06-30
@t4thfavor
lol, 

It can also be "Problem Between Keyboard And Chair."

Nice you noticed it.

---

### Post by doas777 on 2009-06-30
Problem ID: 10T

---

### Post by Elfy on 2009-06-30
Please do not post duplicate threads.

---

### Post by Elfy on 2009-06-30
Please do not post duplicate threads - also don't bump so soon.

---

### Post by mhgsys on 2009-06-30
doas777

indeed,.

---

### Post by 10ghost on 2009-06-30
problem solved
i dont know how to indicate that a thread has been solved
how do i do that?

---

### Post by Elfy on 2009-06-30
Add a solved tag - bottom of the page - on the right - Edit Tags

---

