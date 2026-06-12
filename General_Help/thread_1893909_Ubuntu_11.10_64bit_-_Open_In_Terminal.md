---
title: "Ubuntu 11.10 64bit - Open In Terminal"
date: 2011-12-11
forum: General Help
---

### Post by stressed on 2011-12-11
I've installed Open In Terminal to the right click menu of Ubuntu 11.10 64bit by using the below command line syntax:

sudo apt-get install nautilus-open-terminal
nautilus -q

I've also installed the "Konsole" terminal built on the KDE platform from the Ubuntu Software Center.  Now, when I select the Open In Terminal, the terminal that appears is the default Ubuntu terminal.  The question is, how do I get the Open In Terminal to actually open the "Konsole" terminal from the Ubuntu Software Center install and not the default Ubuntu terminal?  Any suggestions would be helpful and I thank you in advance.

---

### Post by yeats on 2011-12-11
Seen this?:

[http://www.howtogeek.com/howto/ubuntu/set-the-default-terminal-emulator-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/set-the-default-terminal-emulator-on-ubuntu-linux/)

---

### Post by stressed on 2011-12-11
Thank  you for the post.  I had not seen that.  When I use that syntax, I get:
error: unknown argument '-config'

---

### Post by yeats on 2011-12-11
> **stressed said:**
> Thank  you for the post.  I had not seen that.  When I use that syntax, I get:
error: unknown argument '-config'

try "--config" - the double dash doesn't always come through correctly on the web.

---

### Post by stressed on 2011-12-11
Interestingly enough, the --config worked in the Konsole terminal but not in the default Ubuntu terminal.  

When the choices appeared in the Konsole terminal, of course I chose Konsole.  However, for whatever reason, Open In Terminal still uses the default Ubuntu terminal and not the Konsole terminal that I chose.

When I check it by running the command again, it shows that the Konsole is selected.

---

