---
title: "Skip username on console login"
date: 2010-03-30
forum: General Help
---

### Post by undecim on 2010-03-30
I have a system setup from a minimal install and have no display manager. Instead I have a bash script that runs startx once per boot.

Since I am the only person who would ever be logging into this laptop, and I need a password for encryption, I'm looking for a way to skip typing my username when logging on.

In /etc/init/tty1.conf, I changed
```
exec /sbin/getty -8 38400 tty1
```
to
```
exec /sbin/getty -l "/bin/login undecim" -8 38400 tty1
```

but instead of skipping the username, it asks me for it and jus't hangs after I type it in.

From a console "sudo /bin/login undecim" works fine, but through getty in tty1.conf it doesn't.

Any advice is appreciated. Thanks in advance.

---

### Post by undecim on 2010-03-30
I found the problem, but I'm not sure how to fix it.

According to ps, the getty command is running as
```
/sbin/getty -l /bin/login undecim -8 38400 tty1
```

the quotes are stripped, and so the "undecim" is taken as a parameter for getty... Any ideas on what I can do to fix this?

---

### Post by CaKiwi on 2010-03-30
These are wild guesses but until someone more knowledgable comes along, try single quotes (') instead of double quotes. If that doesn't work, try putting a backslash in front of each of the double quotes.

---

