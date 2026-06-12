---
title: "How can one bypass password for a sudo command?"
date: 2011-04-03
forum: General Help
---

### Post by TheHimself on 2011-04-03
I have to enter the root password every time I want to run
```
sudo vpnc
```

and I know that there is a way to avoid entering password every time but I can't remember what it is.

---

### Post by mdhollis on 2011-04-03
You can go to root.

sudo -i

---

### Post by mdhollis on 2011-04-03
I haven't been using linux for a long time but on my system I usually only have to enter my password once.

---

### Post by fela on 2011-04-03
First run ```
sudo visudo
```

Then add a line saying ```
**username** ALL=NOPASSWD: /usr/bin/vpnc
```

(replace username with your username of course)

It might not be /usr/bin/vpnc, to find out, run ```
whereis vpnc
```

---

### Post by TheHimself on 2011-04-07
How can I save the file in visudo?

---

### Post by fela on 2011-04-07
> **TheHimself said:**
> How can I save the file in visudo?

Colon (on my keyboard: shift+semicolon), then wq, then enter.

EDIT: that's if you're editor is vi.

If you're editor is nano, you save by issuing ctrl+X, then y, then enter. For other editors, do whatever is the correct 'save file and exit' procedure.

---

### Post by jerome1232 on 2011-04-07
Why not just allow that specific program to be run without a password.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

There are examples towards the end on how to allow a specific program to be run by certain users with no password. There's no reason to strip your system of protection from malicious programs, which is what allowing nopasswd for everything does.

---

### Post by fela on 2011-04-07
> **jerome1232 said:**
> Why not just allow that specific program to be run without a password.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

There are examples towards the end on how to allow a specific program to be run by certain users with no password. There's no reason to strip your system of protection from malicious programs, which is what allowing nopasswd for everything does.

```
ALL=nopasswd: /bin/somefile
```

Doesn't allow *any* command, it allows /bin/somefile. At least that's what it does on my Debian box. I wouldn't have thought the syntax would be different for Ubuntu?

---

### Post by jerome1232 on 2011-04-08
Ooops I apologize, that's the second time a quick glance at a post messed me up today :oops:.

I just saw ALL=nopasswd and stopped reading. Sorry!

---

### Post by fela on 2011-04-08
> **jerome1232 said:**
> Ooops I apologize, that's the second time a quick glance at a post messed me up today :oops:.

I just saw ALL=nopasswd and stopped reading. Sorry!

I guess it does look a bit confusing :P

---

