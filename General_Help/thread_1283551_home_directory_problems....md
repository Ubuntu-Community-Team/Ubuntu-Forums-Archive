---
title: "home directory problems..."
date: 2009-10-05
forum: General Help
---

### Post by wardi on 2009-10-05
Hi,
When installing Ubuntu 9.04 on my new laptop, i typed wrongly my user name. So as a beginner using the Linux root command, I've managed to correct the user name(after installing Ubuntu), with 'usermod' command and also changed my home directory manually. the problem is that I've lost all the configuration in my Ubuntu's application(like FireFox adds-ons, Music folder and Pictures and Documents folder in the Place menu).
How?
I used the wrong command :
> sudo usermod -md /home/PREVIOUS /home/New/
the commande didn't change any thing as a result of the command, but when i tried to access to the desktop, the system didn't find the home directory for my NEW user name, so i changed manually using the command > mv
and then i could access but i lost my configurations.
Can I get everything fixed.
Thanks ....

---

### Post by elvisd on 2009-10-05
Maybe a permission problem?
Could be that the confguration's directory is here but not accessible.
try a
```
ls -l .mozilla
``` in the terminal
This prints out content of the .mozilla subdirectory, including permissions.
Ev. a chown and chmod could fix the issue.

Hope this helps

---

### Post by wardi on 2009-10-05
Thanks, but i think there is no problem in users privilages```
drwxr-xr-x  6 NEW_USER_NAME OLD_USER_NAME 4096 2009-10-02 23:37 .
drwxr-xr-x 46 NEW_USER_NAME OLD_USER_NAME 4096 2009-10-05 21:22 ..
drwx------  3 NEW_USER_NAME OLD_USER_NAME 4096 2009-09-29 22:23 extensions
drwxr-xr-x  3 NEW_USER_NAME OLD_USER_NAME 4096 2009-09-03 22:54 firefox
drwxr-xr-x  3 NEW_USER_NAME root   4096 2009-09-03 22:54 firefox-3.5
drwxr-xr-x  3 NEW_USER_NAME root   4096 2009-09-03 22:54 firefox-3.6

```

---

### Post by ajgreeny on 2009-10-05
I suspect that everything in your /home directory is now owned by the old username, making this problem for you.

I suggest you start in recovery mode and try changing the ownership of the files with ```
sudo chown -R username:username /home/username
```Wait for more replies before you do this just in case I've got it wrong and make things worse.

---

### Post by Giblet5 on 2009-10-05
> **ajgreeny said:**
> I suspect that everything in your /home directory is now owned by the old username, making this problem for you.

I suggest you start in recovery mode and try changing the ownership of the files with ```
sudo chown -R username:username /home/username
```Wait for more replies before you do this just in case I've got it wrong and make things worse.

You don't have to do that in recovery mode, but the command is fine and it IS what needs to be done.

Just run that command, log off, log in, presto.

---

### Post by wardi on 2009-10-05
Well, it didn't work and i think that wasn't the real problem here...
the OLD_USER_NAME is the name of the formal group that i change it to root before changing the user name

---

### Post by ajgreeny on 2009-10-05
> **wardi said:**
> Well, it didn't work and i think that wasn't the real problem here...
the OLD_USER_NAME is the name of the formal group that i change it to root before changing the user name
??  Sorry, I don't quite understand what you mean by this.

@ Giblet5.  No, I see now that the OP could login OK, but at a quick read, I understood he couldn't do so at first.
Note to self:-- Read and re-read posts before answering.

---

