---
title: "Try #2 - Help!#2"
date: 2006-03-05
forum: General Help
---

### Post by seanmc42 on 2006-03-05
I have rebooted, changed my passsword, man'd securetty and login, and inspected the files /etc/securetty and /etc/security/access.conf, and I cannot login to the tty's!! I am trying to do so with a non-root account.
I CAN login via the gdm - so I know my pw is good.
WTF??
Can anyone please help me?

---

### Post by knalle on 2006-03-05
check if **/etc/passwd** has a bash entry for the user

```

karl:x:1000:1000:karl,,,:/home/karl:/bin/bash

```

like this, the last part tells tty that i can log in with **/bin/bash** if this entry isn't there you cannot log in with that account without adding to the file

---

### Post by seanmc42 on 2006-03-05
Well, yes - not be terse, but if it didn't I couldn't login via the Xterminal.
I looked at /etc/passwd anyway and it's there.

---

### Post by seanmc42 on 2006-03-05
OK, well found out something that's going on, just not sure why...
I used CAPS LOCKS when entering my username - the text was showing
up as a mix of upper and lower...??
Is this a security feature?

Since my pw had caps in it, I had been using caps lock, and hitting shift to
down-case, but of course I couldn't tell that the letters were being entered in mixed mode since the prompt prints out only ****.

What's goint on?

---

