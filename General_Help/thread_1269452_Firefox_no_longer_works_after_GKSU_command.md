---
title: "Firefox no longer works after GKSU command"
date: 2009-09-18
forum: General Help
---

### Post by JGMS on 2009-09-18
I have started Firefox in the terminal via "gksu firefox" which has left me with a cripple browser: unable to navigate and no bookmarks nor history. I tried reinstalling via Synaptic but nothing helped. Please help me out! 

Many thanks ahead. 

JGMS

---

### Post by fogNL on 2009-09-18
> **JGMS said:**
> I have started Firefox in the terminal via "gksu firefox" which has left me with a cripple browser: unable to navigate and no bookmarks nor history. I tried reinstalling via Synaptic but nothing helped. Please help me out! 

Many thanks ahead. 

JGMS

You may have a permissions issue, try rename your firefox folder in your home directory.  I'm not at my computer right now, so I don't know if the folder is .mozzila or .firefox, but try closing down your browser and going into Terminal and doing:

chown -R yourusername:yourusername ~/.firefox  
(or ~/.mozilla whatever it is)

Then restart firefox.

---

### Post by warp99 on 2009-09-18
This happen to me before and the fix is simple. Go into your root directory and delete the hidden /root/.mozilla directory if it exists. It may also be a ownership problem with your /home/$user/.mozilla directory, but unless you're comfortable with changing ownership I would do the following if deleting the root mozilla folder fails:

Backup the hidden mozilla directory in your home share, then delete the directory. It will be recreated with the correct structure, ownership, and permissions when you restart Firefox. You can then import you bookmarks from the bookmarks.html file in the backup directory. You have to redo your settings and re-install any extensions that you may have.

---

### Post by 3rdalbum on 2009-09-18
> **JGMS said:**
> I tried reinstalling via Synaptic but nothing helped.

No. Removing and then reinstalling software generally doesn't solve any problems on Linux. It only solves problems on Windows when the program has become corrupted, and it's rare that this happens on Linux.

Removing the per-user preferences? Works often. If you've having sudden trouble with a program that you've never had before, removing the per-user preferences (in the hidden folders in your home directory) is the first thing to try.

I think the other posters have it - the permissions on the ~/.mozilla folder have been changed because you ran Firefox with 'sudo'. You might be able to change them back by right-clicking on .mozilla, going to Properties and then Permissions. You might need to open Nautilus as root; you know how to do that :-P

Firefox doesn't like being run with *sudo*, and I can't think of a good reason to do it either. I can think of several reasons why not to do it, especially when you consider the number of websites out there with malicious content.

Anyway you don't need a lecture from me, you've already learnt not to do it :-)

---

### Post by lovinglinux on 2009-09-18
I agree with 3rdalbum.

The solution to this problem is simple and there is no need to delete any mozilla folder. All you have to do is to regain ownership of ~/.mozilla. To do that simply run the following command without replacing anything. Run it exactly as it is. Don't forget to close Firefox first:

```
sudo chown -R $USER:$USER ~/.mozilla
```

This issue is described in the **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

Would you mind explaining why you tried to run Firefox as root? 

> **warp99 said:**
> This happen to me before and the fix is simple. Go into your root directory and delete the hidden /root/.mozilla directory if it exists.

That's not a solution. The folder **/root/.mozilla** is the location of the root user mozilla settings. When  you run firefox as root, using gksudo, it uses the profiles on that folder. Once you start firefox again as regular user, it will use the user profile, which is under ~/.mozilla/firefox. The OP problem is that he started firefox with sudo command, so Firefox started as root, but using the user profile folder instead of the one at /root/.mozilla. In this situation, the user looses the ownership of ~/.mozilla and then experience all sorts of problems. So deleting /root/.mozilla won't help. He needs to regain the ownership of ~/.mozilla folder. That's it.

---

### Post by JGMS on 2009-09-18
Many thanks for your help. Just perfect!

Although, I did experience a difficulty since I appeared not to be listed in the file "/etc/sudoers", which prevented me to become a super user in order to enter the command "sudo chown -R $USER:$USER ~/.mozilla". I still am really puzzled why I could no longer become "SU". Any way, I rebooted the computer in recovery mode and added myself in the file via the ROOT start mode (command: "nano /etc/sudoers"). Then, after restarting I could enter the command and I was glad to see  all my bookmarks again. Great!

Thanks a lot indeed.

---

### Post by SuperSonic4 on 2009-09-18
> **JGMS said:**
> Many thanks for your help. Just perfect!

Although, I did experience a difficulty since I appeared not to be listed in the file "/etc/sudoers", which prevented me to become a super user in order to enter the command "sudo chown -R $USER:$USER ~/.mozilla". I still am really puzzled why I could no longer become "SU". Any way, I rebooted the computer in recovery mode and added myself in the file via the ROOT start mode (command: "nano /etc/sudoers"). Then, after restarting I could enter the command and I was glad to see  all my bookmarks again. Great!

Thanks a lot indeed.

That's very unusual, normally only visudo or an environment variable works for that file but meh. For example

```
EDITOR=nano visudo
```

---

