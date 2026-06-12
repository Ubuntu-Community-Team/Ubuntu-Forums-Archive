---
title: "Keep getting this $HOME/.drmc file is ignored error everytime I log in"
date: 2010-09-19
forum: General Help
---

### Post by MrBiggz on 2010-09-19
Greetings!

I keep getting this error every time I log in.  I can find that file and change the permissions as it state yet .. no luck! =(  (I attached a screen shot of the error)

[attach]169924[/attach]

What do I have do to get rid of this??

Thank you in advance! :)

---

### Post by lmarmisa on 2010-09-19
Maybe this post could help you. Command should be "chmod", not "Chmod":

[http://ubuntuforums.org/showthread.php?p=479186#post479186](http://ubuntuforums.org/showthread.php?p=479186#post479186)

---

### Post by gandaran on 2010-09-19
try running this command in terminal then reboot
```
 sudo  chown  -R user:user /home/user
```
change every "user" to you real user-name

---

