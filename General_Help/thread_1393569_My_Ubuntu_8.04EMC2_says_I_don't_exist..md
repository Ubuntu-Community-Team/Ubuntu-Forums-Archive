---
title: "My Ubuntu 8.04/EMC2 says I don't exist."
date: 2010-01-29
forum: General Help
---

### Post by grey1beard on 2010-01-29
I'm going through the process of setting up EMC to run my cnc machine in Ubuntu 8.04 (both updated online yesterday).
Trying out various settings, but getting nowhere, I decided to come in from the cold workshop and set up hardware in the front room.
Switched on, entered username and password, and it tells me that
 "your home directory /home/john is listed but appears not to exist"
It offers me a possible way forward, but this doesn't work.

1.   "$HOME/.dmrc file is being ignored"

2.  "Try logging in with one of the failsafe sessions"

Unfortunately, I've no idea what this means, or how to do it, so I'd be very grateful for some advice.

John

---

### Post by audiomick on 2010-01-29
Hallo.
Is /home perhaps on a different HD to the system? I'm thinking of a cable getting loose during the move.

---

### Post by grey1beard on 2010-01-29
Hi Michael.
No,  literally carried the pc + screen etc. into the house, plugged everything together, and crunch - brick wall :(
John

---

### Post by grey1beard on 2010-01-29
I've just checked inside that the hdd is ok, but then at least it boots as far as the user/password screens, so that's ok.
I tried a cold boot, but no change.

---

### Post by grey1beard on 2010-01-29
I've just found the method of going in via a terminal, but don't have the correct sudo instruction to complete this route.
I tried sudo mkdir -p -tmp, then sudo chmod 1777 /tmp as quoted in a recent thread, then ctr/del/F7 but it didn't get me in.
Could someone spell it out for me ?
Many thanks,
John

---

### Post by grey1beard on 2010-01-29
End of this problem.
I've just reinstalled, as I have no data to save, and I can start again, knowing a little more this time round.
John

:|

---

