---
title: "Ubuntu can boot, but won't log in"
date: 2011-04-20
forum: General Help
---

### Post by ttshivers on 2011-04-20
This problem is very puzzling. My computer has been working fine up until this afternoon.  I turned on my computer and it booted normally and displayed the login screen as usual.  I tried to log in, and it looked like it accepted my password, and it then prompted me for the passphrase for my ssh private key.  I was not expecting this to happen, since I had already inputed and added my ssh identity a couple months ago.  I inputed the passphrase, but then when I submitted it, the screen turned black and brought me back to the login screen.  I tried a couple of times, and every time, it still prompted me for my ssh passphrase, and the screen still turned black.  I then deleted the id_rsa and id_rsa.pub from ~/.ssh.  That stopped the computer from asking for the passphrase, but it did not stop the screen from turning black.  So now what happens is that the computer boot up and diplays the login screen.  I type in my password, and submit it and the screen turns black and the login screen comes up again.  After that, I tried to login from one of the virtual consoles, and it worked.  I ran ```
sudo apt-get -f install
``` and ```
sudo dpkg --configure -a
```  The first time I ran it, it said that language-common was partially installed, so I ran ```
sudo apt-get update
``` and then ```
sudo apt-get dist-upgrade
```  It fixed the language-common package, but not the login problem.  This is where I am stuck right now.  Thanks for any help.  Tell me if you need a lshw for my system specs.

Update:  I have found a temporary fix.  I do not want to do this every time I boot though.  The main problem still remains.  I was able to get the graphical user interface up by selecting recovery mode from grub, and then selecting resume normal boot.  I then logged in and typed startx, which brought up the GUI without prompting me for a password since I already logged in in the terminal.

---

### Post by 00arthuryu on 2011-05-07
I've had this problem since 10.10, which I couldn't find a fix for, in the end I put my account on "auto-login" as soon as I start Ubuntu

it's not the best fix in the world..... but it works..

---

