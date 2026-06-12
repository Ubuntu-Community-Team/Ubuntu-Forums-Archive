---
title: "How do I open a file to write?"
date: 2012-08-12
forum: General Help
---

### Post by Rixonomic on 2012-08-12
I've been through a bunch of guides, FAQs and boards and tried all these lines of code, but I just can't figure out how to open a file to edit it and save what I've changed. I'm trying to edit /etc/pulse/default.pa. After making a backup, I use this code:

gksu gedit /etc/pulse/default.pa

A lot of people have told me to do this. But when I enter it into the Terminal, nothing happens. It thinks for a couple seconds and then prompts me for another line of code. So I tried to prepend it with "sudo", but I get the same results. So what do I do?

---

### Post by Rixonomic on 2012-08-12
I also tried entering the code with Ctrl+F2, and it prompts me for my password, but still nothing happens.

---

### Post by ads52 on 2012-08-12
This works on my system:

```
gksudo gedit /etc/pulse/default.pa
```

and the only prompt is for my password. Can you give a screenshot or direct quote of the subsequent prompt on your system?

---

### Post by Rixonomic on 2012-08-12
When I said that it prompts me for another line of code, I just mean that the process finishes, and the next line pops up:

username@ubuntu:~$

But I tried that code with "gksudo" instead of "gksu", and it actually prompted me for my password, but that's still all that happens. 

I guess I don't understand when I get to edit the file and save what I've done? Is it supposed to open automatically after I've entered the code? I tried opening it and changing it after I entered the code and put in my password, but when I try to save, I still get the error message that says "Can't open file to write".

---

### Post by Rixonomic on 2012-08-12
Got it. I found another thread that said to use "sudo nano filepath". Worked perfectly :D

Thanks for the help though, I appreciate it.

---

