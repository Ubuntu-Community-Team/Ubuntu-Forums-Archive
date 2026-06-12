---
title: "asking for password in recovery mode"
date: 2010-09-15
forum: General Help
---

### Post by nischalinn on 2010-09-15
I logged in** recovery mode **via grub, it shows several options:
like,

resume normal boot 
failsafeX
dpkg, etc.

When I enter the **resume normal boot** it shows something like this:
[B]Ubuntu 10.04.1 LTS xxx tty 1
xxx login:
password:[/B]
and I entered my _root password_ which I need for the command "_sudo -i_".
But it shows* incorrect password*, why is it so?

Same thing happens with **dpkg **option also?
Why is it so, I dont have any other passwords for my machine?

---

### Post by WorMzy on 2010-09-15
sudo asks for **_your_** password, not root's; unless you've logged in as root, in which case using sudo -i is redundant.

su asks you for root's password.

---

### Post by TwelveGauge on 2010-09-15
yeh, to use sudo you'll have to use your login pass.

---

### Post by aysiu on 2010-09-15
The root password is not set by default.

So what you're really entering is your user password. If it works for ```
sudo -i
``` it should work at the login screen as well. Any chance you're mistyping it or you have caps lock on by accident?

If all else fails, boot into recovery mode and drop to a root shell (no password should be required since the root password is not set by default) and then reset your own user password ```
passwd *username*
``` where *username* is your actual username.

---

### Post by nischalinn on 2010-09-27
I changed my password via:
**passwd username** and set a new password. Then I logged in terminal mode via Ctrl+Alt+F2, it asked for my password and I typed the newly set password but it shows **login incorrect.**

Also, when I do **sudo su** or **sudo -i**, the newly set password works but when I do **su** it shows **authentication failure**. I've the same problem before setting the new password.

I can't understand why is it so???? Can anyone help me??????????

---

### Post by psusi on 2010-09-27
Did you enter your user name at the console, or are you trying to login as root?  Again, su asks for root's password, not yours, and by default root does not have a valid password so you can not log in or use su.

---

### Post by nischalinn on 2010-09-27
I have solved the problem of su and sudo -i \ sudo su. I used the command** sudo passwd root** for setting the password for su. Now I've _*different passwords for su and sudo -i \ sudo su. *_
Still I've problem via logging in terminal mode. I've tried both passwords, but it shows** login incorrect.**

---

