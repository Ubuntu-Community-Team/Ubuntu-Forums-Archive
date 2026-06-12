---
title: "How do I share my wireless network without sharing my network's password?"
date: 2011-03-04
forum: General Help
---

### Post by s3a on 2011-03-04
Right now when I want to share my wireless network with people, they can easily click the check box along the lines of "show the password while typing" and they can see what the password is.

I have physical access to the machines of the people I want to share my network with since they are my computers. Is it possible for me to make it impossible for them to figure out my network's password but let them use my network?

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by wiggly81 on 2011-03-04
for anyone to be able to access you wireless password they would need to go to edit connections and on my system before that window shows i have to enter my system password so in theory if they don't know that password they cant access your wireless key, however if they have access through your network what is to stop them accessing your router and getting the password there anyway

---

### Post by s3a on 2011-03-04
They have accounts and also have sudoer permission. As for accessing my router, that's password-protected with another password so they cannot access it (which is what I want).

---

### Post by peculiar penguin on 2011-03-04
Set up IEEE 802.1x and a Radius server, give everyone their own password, lock them out when they share their password or get uppity :P

---

### Post by wiggly81 on 2011-03-04
> **s3a said:**
> They have accounts and also have sudoer permission. As for accessing my router, that's password-protected with another password so they cannot access it (which is what I want).

if you trust them to install / change settings on your system why are you worried about your wireless key?

---

