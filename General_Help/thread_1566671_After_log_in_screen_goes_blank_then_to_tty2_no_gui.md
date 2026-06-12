---
title: "After log in screen goes blank then to tty2 no gui"
date: 2010-09-02
forum: General Help
---

### Post by I-75 on 2010-09-02
Right after logging in, as the graphics starts up the screen goes blank then goes to tty2 with a login prompt and no graphics at all.  

I searched the Ubuntu forums and checked the known bugs before posting...I didn't find anything so I am posting here.


I have Kubuntu 10.04.1 I used the standard Kubuntu install disc. The Computer is a Compaq dm 220mt desktop 2.80 Ghz, 1.2 GB Ram, 40 GB Hard drive. I originally had Ubuntu 8.04 on it and it ran perfect. So I decided to do a fresh install of Kubuntu 10.04 and it worked great for a day or two, then this issue happens. 

Any clue? Can I fix it it in tty with a script? 

I am able to log in tty and tried "sudo startx" in hope of getting my graphics back. I get the following errors "Fatal Server error No screens found" and "xinit no such file or directory (errno 2)" and unable to connect to server..

Thanks in advance for any help...

---

### Post by llawwehttam on 2010-09-02
did you install graphics drivers at all? If you did regenerating the xorg file may work.

---

### Post by I-75 on 2010-09-02
> **llawwehttam said:**
> did you install graphics drivers at all? If you did regenerating the xorg file may work.
 
I did not recall installing any graphics driver.  I tried sudo startx and even tried start kdm to get my desktop back to no avail. I'd hate to reinstall it all over again and for it to happen again... 

 What script could I use to get the desktop back?

---

### Post by bergfly on 2010-09-03
drop the sudo and just try ```
startx
``` Ubuntu does not like you running X as root. might not work but hopefully will give you a better error message

---

