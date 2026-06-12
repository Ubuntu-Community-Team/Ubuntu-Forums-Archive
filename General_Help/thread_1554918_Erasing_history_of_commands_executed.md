---
title: "Erasing history of commands executed"
date: 2010-08-17
forum: General Help
---

### Post by rahulburra on 2010-08-17
What **command** is used to **remove** the **history of all the commands executed**
while compromising a Linux system?

---

### Post by sydbat on 2010-08-17
> **rahulburra said:**
> What command is used to remove the history of all the commands executed
while **compromising** a Linux system?Ummm...

---

### Post by kiridude on 2010-08-17
```
rm -f .bash_history
```

---

### Post by rahulburra on 2010-08-17
@kiridude

Thanks for reply

could you  please tell me **where can i find the file .bash_history**

Thankyou

---

### Post by KeyserSoze93 on 2010-08-17
> **rahulburra said:**
> @kiridude

Thanks for reply

could you  please tell me **where can i find the file .bash_history**

Thankyou

You can find it **in your home directory**.

```

ls -a ~

```

If a command or file is mentioned without a directory being spoken of, it is probably safe to assume that it will be in your home directory, since this is where your shell will default to.

If you ever log into a root shell, you'll also want to wipe, delete or shred /root/.bash_history

---

### Post by Smart Viking on 2010-08-17
> **rahulburra said:**
> @kiridude

Thanks for reply

could you  please tell me **where can i find the file .bash_history**

Thankyou

It is a file in the home folder, to view it, press "ctrl+h" in nautilus. :)

---

### Post by cek on 2010-08-17
The easiest way is to type the following in a terminal:

history -c

---

### Post by Iowan on 2010-08-17
> **rahulburra said:**
> What **command** is used to **remove** the **history of all the commands executed**
while compromising a Linux system?Feel free to use the Resolution Center to get the thread re-opened.

---

