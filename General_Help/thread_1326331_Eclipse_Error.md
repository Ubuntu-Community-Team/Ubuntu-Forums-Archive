---
title: "Eclipse Error"
date: 2009-11-14
forum: General Help
---

### Post by Hosmion on 2009-11-14
I download Eclipse via the Ubuntu Software Center, but it won't open.  Is there a way to open it?

---

### Post by rcorbish on 2009-11-14
What error do you get (if any)?
What is the installed location?
Can you try running as root?

---

### Post by Hosmion on 2009-11-14
I cant do anything..  I cant run in terminal (at least what I tried) and it wont open to give an error message or anything...

---

### Post by rcorbish on 2009-11-14
You could uninstall the ubuntu version and just get the latest from eclipse.org.

You have got java (sun) working I presume?

RC

---

### Post by Hosmion on 2009-11-15
But I downloaded it from Eclipse.org also, but it still wont open

And yes, I have Java working.

---

### Post by Hosmion on 2009-11-15
Bump

---

### Post by rcorbish on 2009-11-15
I'm not sure what to say. Have you checked whether the DISPLAY is sending it elsewhere 

ps auxww | grep eclipse

echo $(which eclipse)   # does this show where you installed it ?

RC

---

### Post by Hosmion on 2009-11-24
Which do I type in Terminal?

Also, BUMP

---

