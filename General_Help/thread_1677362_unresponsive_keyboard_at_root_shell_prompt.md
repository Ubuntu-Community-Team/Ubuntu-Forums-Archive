---
title: "unresponsive keyboard at root shell prompt"
date: 2011-01-28
forum: General Help
---

### Post by ktmurph on 2011-01-28
I have no user name or password and cannot log in. In recovery mode, I after I enter "drop to root shell prompt" my keyboard does not respond when I try to "give root password for maintenance" or try to enter "Control-D" at the blinking cursor.

---

### Post by Halzen on 2011-01-28
Is this a USB keyboard? If so, I ran into a similar problem; turns out you'll probably need to edit your BIOS settings to enable legacy USB keyboard support.
(The setting was easily identified on my Gigabyte motherboard, so your procedure will vary. Check the manual.)

---

### Post by ktmurph on 2011-01-28
It's just my macbook keyboard

---

### Post by tredegar on 2011-01-28
Type your password, it will not be echoed to your terminal. This is normal behaviour.
Then press [RETURN]

You should then find yourself logged in.

If not, then please post further details.

---

