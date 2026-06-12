---
title: "Skype 4.0 issues"
date: 2012-06-28
forum: General Help
---

### Post by Monotoko on 2012-06-28
I tried to post this in the Linux section of the Skype forum last week, but it doesn't seem to have generated any interest, so I was wondering if you guys can help me?

I've just downloaded the .deb for 64bit Ubuntu, and the installation seemed to go well. I can sign in and talk to other contacts, but when I try to accept a contact skype just vanishes, is this a known problem? Where can I find logs of what's happening?

---

### Post by prshah on 2012-06-28
> **Monotoko said:**
> contacts, but when I try to accept a contact skype just vanishes, is this a known problem? Where can I find logs of what's happening?

Open a terminal emulator (Dash-Terminal), and launch skype from there. ```

/usr/bin/skype
# or find it with the command
which skype
```

Now, choose to add a contact. If skype crashes, you will find relevant output in the terminal. Please post back that output here for a clue to the problem.

---

### Post by Monotoko on 2012-06-28
Thanks for the help, I already tried that and got a very generic error message:
monotoko@KatieV:~$ /usr/bin/skype
Aborted

I'm still on 10.04 just as a btw, think I forgot to mention that in my OP :)

---

### Post by Monotoko on 2012-06-28
bumpity bump

---

### Post by prshah on 2012-06-28
> **Monotoko said:**
> got a very generic error message:
monotoko@KatieV:~$ /usr/bin/skype
Aborted

Try resetting skype config```
mv ~/.Skype/shared.xml ~/.Skype/shared.bak
``` Only resets parameters, no user info is lost.

Or resetting everything```
mv ~/.Skype ~/dotSkype
```

If it doesn't work, and you want to put things back the way they are, exit (sign out) skype, and use these commands```
rm ~/.Skype
mv ~/dotSkype ~/.Skype
```

Please post back with your results.

---

