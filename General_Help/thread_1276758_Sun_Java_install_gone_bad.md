---
title: "Sun Java install gone bad"
date: 2009-09-27
forum: General Help
---

### Post by Shuffman on 2009-09-27
I was installing Java and it was stopped before it completed and now whenever I try to install anything or open Synaptic package manager I get the following message.

dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

 I am new to Linux, currently I have Ubuntu 9.04

---

### Post by FunkyRes on 2009-09-27
Application->Accessories->Terminal

(Open Application menu, choose Accessories sub menu, choose Terminal)

Then in the terminal, run the command it showed you:

sudo dpkg --configure -a

It will ask you for your password, that's your login password.

---

### Post by bruce2000 on 2009-09-27
Try typing the command it gives you into a terminal window.

If you're unsure of the steps involved here's a detailed breakdown:

1. Start a terminal: It's in the menu Applications/Accessories/Terminal

2. Type the command (the part between but not including the apostrophes) into the terminal and hit return.

3. Enter your password when it asks you for it, but note that while your keystrokes won't appear on the screen, it will still accept it.

Hopefully that will fix it, if not post back here and maybe someone else can help you further.

---

### Post by Shuffman on 2009-09-27
Wow that took care of it! I must have entered the text wrong when I tried it before.
Thank you!

---

### Post by tuxxy on 2009-09-27
Java is included with the package ubuntu-restricted-extras along with Flash, codecs etc its a gereat package to install on a clean system :D

```
sudo apt-get install ubuntu-restricted-extras 
```

---

