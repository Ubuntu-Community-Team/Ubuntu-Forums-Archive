---
title: "Power Interruption - file damaged"
date: 2010-09-05
forum: General Help
---

### Post by rory526 on 2010-09-05
My laptop lost power as I was working on a source file in the c programming language today. Upon restarting the computer, most of the file had become corrupted. The corruption looks like the following.

```
÷0ÿûÕ^±&#402;&#8240;F2&#8222;*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*#9Éã¥TÇa<òGÓ\b÷*
```

The corrupted portion is a contiguous region beginning at the start of the file. I am familiar with backup files suffixed with a '~' appearing alongside files that have been edited, but on this installation, none seem to have been created.

Does anybody know of any way to possibly recover the file or a previous version of the file?

Thanks in advance.

---

### Post by CharlesA on 2010-09-05
Wow that's not good at all. You are pretty much screwed if you didn't have a backup of the files.

---

### Post by rory526 on 2010-09-06
it'll teach me to back things up i suppose. Would it be a good idea to make the partition synchronous to prevent such things in the future?

---

### Post by CharlesA on 2010-09-07
Use a UPS. :)

Other then that, save the file constantly.

---

### Post by rory526 on 2010-09-08
I had instructed the text editor (nano) to save but I think that because the file system is asynchronous, the last save had not been fully written to disk when the battery died. (I was using a laptop on a bus.) I'm not sure if this is correct.

I didn't lose much anyway. It's not too bad.

A UPS on the bus might raise a few eyebrows. :)

---

### Post by CharlesA on 2010-09-08
I believe you can set the laptop to hibernate when the battery reaches a certain level. Check [here]("https://wiki.ubuntu.com/PowerManagement").

That way you won't lose data. :)

---

### Post by rory526 on 2010-09-08
You must be referring to gnome-power-manager. I think it's installed by default on a standard ubuntu installation, isn't it?

Thanks, that sounds like the best solution.

In a vain attempt to prolong the life of my battery, I had turned off the GUI and likely also turned off gnome-power-manager. Lesson learned I suppose...

---

### Post by CharlesA on 2010-09-08
I think it's installed by default, but I don't use GNOME. :P

---

### Post by rory526 on 2010-09-08
But... your profile pic... o_0 ???

---

### Post by CharlesA on 2010-09-08
Too lazy to change it. O_o

---

### Post by rory526 on 2010-09-08
Tell me about it. Mine quite frightens me. :)

---

### Post by rory526 on 2010-09-08
Thanks for all the help and chat.

---

### Post by CharlesA on 2010-09-08
Don't forget to mark the thread as solved. :)

---

