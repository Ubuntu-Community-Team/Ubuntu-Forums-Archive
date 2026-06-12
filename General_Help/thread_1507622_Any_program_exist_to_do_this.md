---
title: "Any program exist to do this?"
date: 2010-06-11
forum: General Help
---

### Post by Monotoko on 2010-06-11
Hi Guys,

What i am after is quite a simple program, basically i need it to do the following:

- Check wifi routers (iwlist maybe?)
- check that a certain router exists
- if it does, try to connect using the WPA key provided (in a file somewhere..)
- If it connects successfully, continue with boot

If not, collect the output of iwlist and if there is an unsecured network around, connect and send the list to the users email address (also in a file somewhere, initial setup of the application would be needed) then shutdown.

It would also be useful to make use of an internal 3G connector if there is one to send the information then shut down...

---------------------

If an application like this doesn't exist yet. Would it be moderately simple to make? Which programming language would you advise?

---

### Post by BoneKracker on 2010-06-11
Bash

---

### Post by Monotoko on 2010-06-11
I would like it to be cross-platform though..
How could i do that?

---

### Post by lisati on 2010-06-11
Be careful not to use other people's wireless without their permission. Possible legal complications aside, your neighbours might not take too kindly to you using their bandwidth.

---

### Post by Monotoko on 2010-06-11
Hmmm good point...
Would it be okay to just scan?

Then tell the thief to plug into LAN in order for the computer to boot...then send the information that way?

---

### Post by BoneKracker on 2010-06-11
Oh, a wise guy, eh?
*smack*
Nyuk, nyuk, nyuk.

---

### Post by cariboo on 2010-06-11
It sounds like you need a pxe server, you can't do it using a wireless connection.

---

