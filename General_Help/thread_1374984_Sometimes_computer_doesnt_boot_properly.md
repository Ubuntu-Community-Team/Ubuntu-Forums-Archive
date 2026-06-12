---
title: "Sometimes computer doesnt boot properly"
date: 2010-01-07
forum: General Help
---

### Post by DeusExM1 on 2010-01-07
I have Ubuntu 9.10 64-Bit. sometimes when i boot the computer, right after the grub loads, a black screen is displayed. It just says my computer's name and "tty1".  It lets me enter my username and password. The system takes my password but the black screen remains.

For some reason the word "ubuntu" with the loading bar does not appear like it is supposed to in this case. The system does not boot into my destop like it should. 

This usually happens 1/4 times when i boot so i didnt pay much attention and would just restart the computer. However just 5 minutes ago i had to boot my computer 12 times to get it to boot into the desktop. Anyone else getting this problem?

Is there any fix or should i just downgrade to 9.04 ? :(

---

### Post by Greenwidth on 2010-01-07
This _might_ be related:
[http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)

I had this trouble with graphics driver (I had to use 195.22 in the end).
Strange that it sometimes works though.

When you boot next time and it drops to a prompt, after logging in, type 'startx' and see if there are any errors in the output.

---

### Post by DeusExM1 on 2010-01-07
i will give startx a try . Thanks !

---

### Post by DeusExM1 on 2010-01-08
yep ... starx worked great. Any idea what to do to prevent this from happening?

---

### Post by IsmaelMunchen on 2010-01-08
Sometimes I have this problem too.

---

### Post by DeusExM1 on 2010-01-08
yeah i didnt have it in 9.04. i kept quiet for a few months hoping that some update might fix it. so far nothing. Ubuntu is great, just this one little snag is a bit pesky haha. if anyone comes across a way to fix it please post it here. Thanks in advance ! :P

---

### Post by Greenwidth on 2010-01-08
No errors when you 'startx'?

---

### Post by DeusExM1 on 2010-01-08
no errors at all... it starts the desktop just fine. :o .

its weird... but thats what happens.

---

