---
title: "Help me boot up!!!!"
date: 2010-01-02
forum: General Help
---

### Post by tad214 on 2010-01-02
[B]Hello,
I have been using ubuntu 9.10 since i upgraded it about a month ago. It has been doing great up until about a week ago. It will not boot up.Here is what is does when i try to boot it up:
It boots up to the log-in screen, then when i put in my info, it goes off that screen like it is fixing to boot up to the desktop, but then it goes back to the desktop and a little box pops up in the top right hand corner and says:
*[COLOR="red"]THE CONFIGURATION DEFAULTS FOR GNOME POWER MANAGER HAVE NOT BEEN INSTALLED CORRECTLY. PLEASE CONTACT YOUR COMPUTER ADMINISTRATOR.[/COLOR]*This is what it does everytime time i try to boot it up. Could someone please help me out with this problem. Thank you in advance for the help. Have a great day. *[COLOR="Red"]Dale[/COLOR]*[/B]

---

### Post by Leppie on 2010-01-02
at the login prompt, switch to a non graphical terminal by pressing CTRL+ALT+F1 (or F2, etc.)
login with your userid and password.
issue these commands:
```
$sudo chmod a+rwxt /tmp
$sudo reboot
```

---

### Post by tad214 on 2010-01-03
[B][COLOR="Blue"]Hi,
Thanks for the quick reply. That is the problem, it will not boot up in order for me to be able to enter any commands. I am new to this so you may need to explain some more, thank you again. Dale[/COLOR][/B]

---

### Post by john newbuntu on 2010-01-03
But didn't you mention that you get a login screen?  At this time, do not enter anything.  Hit the Ctrl+alt+F2 instead.  This is where you will be asked to enter your  id and password. Enter your info and login.

This is called the virtual console.  Now, once you log in, try what Leppie suggested.  Also, type the following command:
df -Th
and post the output of this command.

Remember that to get back to your login menu, you would have to hit the following key sequenct: Ctrl+alt+F7

---

### Post by tad214 on 2010-01-03
**[COLOR="Indigo"]Thank you for the reply. I will give theses options a try, and will get back with you all. Thanks again[/COLOR]**..

---

