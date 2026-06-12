---
title: "How can I Change my Username?"
date: 2012-09-24
forum: General Help
---

### Post by w201 on 2012-09-24
Hey guys- I've been searching around for instructions on how to change my username and found a few how-to's but not sure which is the right method for ubuntu.

Basically, will the following command do the trick?

> usermod -l <New Name> -d /home/<New Name> <Old Name>Thanks!

[SOLVED]
1. From desktop, CTRL+ALT+F1
2. log in as root
3. Use the **who **command to see which users are logged in and force them out by typing **pkill -KILL -u &#8220;username&#8221;**
4. type [B]usermod -l <new_name> <old_name>
[/B]5. type **usermod -d /home/new_name -m new_name**

---

### Post by raja.genupula on 2012-09-24
[http://askubuntu.com/questions/34074/how-do-i-change-my-username](http://askubuntu.com/questions/34074/how-do-i-change-my-username)

---

### Post by w201 on 2012-09-24
Thanks that worked, however, network manager goes down after making this change.

Any idea how to get things sorted out? I don't know if this is the right command, but I remember seeing it somewhere so I tried **service NetworkManager restart** but I get unrecognized service.


thanks

---

### Post by funicorn on 2012-09-24
service network-manager restart

But I guess it won't solve your problem.

---

### Post by w201 on 2012-09-24
service network-manager restart won't fix it. I can send a ping request and get a response but network manager got disabled when I made those changes.  

I'm trying this out  on virtualbox before I make the changes on my host machine so if anyone knows a solution please help.

Thanks!

---

### Post by w201 on 2012-09-24
Just a quick update, the network manager problem was solved by rebooting my computer.  Steps to change your username:

1. From desktop, CTRL+ALT+F1
2. log in as root
3. Use the **who **command to see which users are logged in and force them out by typing **pkill -KILL -u “username”**
4. type [B]usermod -l <new_name> <old_name>
[/B]5. type **usermod -d /home/new_name -m new_name**

the last step changes the name of your home directory.  Reboot and you should be good to go. Some files may reference your old home directory, if you experience this issue see:
[http://askubuntu.com/questions/34074/how-do-i-change-my-username](http://askubuntu.com/questions/34074/how-do-i-change-my-username)

---

### Post by daslinkard on 2012-09-24
Good info here....thanks for adding the detail for the fix!  I just had someone asking me today about changing their username!

---

### Post by w201 on 2012-09-25
No problem man, love to help.

---

