---
title: "how to make 32 bit programs work on 64 bit ubuntu."
date: 2010-11-03
forum: General Help
---

### Post by HonestBob456 on 2010-11-03
first you go to the file location in the terminal, for example if you wanted to make a 32 bit program in your downloads folder work on your system you would first open the terminal and type,  **cd ~/Downloads** you will now be in your downloads folder, now type in 
 ** sudo dpkg -i --force-architecture **DO NOT PRESS ENTER YET!, now right click on your 32 bit program in you downloads folder and copy the file name, paste it in the terminal so that it looks like this[B]:
jose@jose-laptop:~/Downloads$ sudo dpkg -i --force-architecture gens_2.15.5_i386.deb 
[/B][I]in this example i install a gens emulator 32 bit.

[/I]**gens_2.15.5_i386.deb **is the example program, replace the name with YOUR desired program (32 bit) 

AFTER YOU TYPE IN THE COMMAND IT SHOULD ASK FOR YOUR PASSWORD, ENTER IT AND THE PROGRAM SHOULD INSTALL!!!! ENJOY!!!

---

