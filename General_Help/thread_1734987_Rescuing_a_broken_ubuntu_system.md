---
title: "Rescuing a broken ubuntu system"
date: 2011-04-20
forum: General Help
---

### Post by ziggyfish on 2011-04-20
Normally when I have a broken ubuntu system, like when I upgrade to a beta ubuntu version. I just use one of the ttys, however I have not been able to do this with newer kernel versions. Is there a setting I can use to enable this feature again?

---

### Post by lmarmisa on 2011-04-20
Welcome to the forums.

I would recommend to give more information about the symptoms of your problem if you wish to receive some help.

Best regards,

Luis

---

### Post by rcayea on 2011-04-20
You could try going to /etc/default and opening the console-setup file and adding this line if you don't have it:

# Setup these consoles.  Most people do not need to change this.
ACTIVE_CONSOLES="/dev/tty[1-6]"

I just copied that from my file. I am not totally sure if this does the trick.

---

### Post by brpylko on 2011-04-20
depending on the flavor you are using, you may want to log in as root or use sudoing(sudoeing?) in the terminal.

---

