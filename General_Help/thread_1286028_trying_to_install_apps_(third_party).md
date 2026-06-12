---
title: "trying to install apps (third party)"
date: 2009-10-08
forum: General Help
---

### Post by tufyuma on 2009-10-08
Hello,
I'm new to Linux, I finally got my Dual boot laptop up and running.  

I am trying to install a Third party program (happens to be AirCrack - Ng)  I used synaptic package manager to install it.  It said it worked, but now i don't know where it is, i hoped it would be under "applications" but it is not.  There is now a file in the "bid" folder for it.  

How do i get it under the applications menu?

Thanks

Jim

---

### Post by jeremyswalker on 2009-10-08
The "bid" folder? Do you mean the "bin" folder? Anyway, if you right click the application menu, and then click edit menu, there will be an option to add an entry. You can then browse for the command, change the icon, etc.

---

### Post by NightwishFan on 2009-10-08
Is this application graphical or command line? If it is a command line program, you can try running it in the terminal.

Try:
```
apropos aircrack
```

---

### Post by tufyuma on 2009-10-08
Thanks for the info, wireshark loaded fine, i forgot about aircrack being command line.

Looks like it's working!!


Thanks again

---

