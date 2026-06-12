---
title: "How to get into Sudoers file in 10.04?"
date: 2011-03-25
forum: General Help
---

### Post by Ariya243 on 2011-03-25
I changed my user name, and now the Terminal shows my new user name. I log in with the same user name  and the same password. But after changing the username, I can't get anything done as sudo. It says that I am not in the sudoers file, and I can't get in at all. I tried sudo visudo, sudo -i, sudo -l...

When, I wrote sudo -l the following came in the Terminal.

ariya@Aspire:~$ sudo -l
[sudo] password for ariya: 
Sorry, user ariya may not run sudo on Aspire.

ariya@Aspire:~$ sudo -i
[sudo] password for ariya: 
ariya is not in the sudoers file.  This incident will be reported.

Same answer when I wrote sudo visudo.

How do I get into sudoers file and give my new user name ariya the root privileges. Even my old user name doesn't work at all. 

Thanks!

---

### Post by WorMzy on 2011-03-25
Follow this tutorial: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Ariya243 on 2011-03-25
I tried that too. 
Once in recovery and in root shell, it asks for root password, which I give, for that's the only one I have. But it says that it is not the password.

---

### Post by luceerose on 2011-03-25
To edit sudoers file, type the following into either terminal or run dialog;
```

gksu gedit /etc/sudoers

```
I like to put myself in the sudoers file as such;
(just add the following line at the end of the file)
```

yourusername	 ALL=(ALL) NOPASSWD:ALL

```
Replace 'yourusername' with your own username, of course.
That way you don't have to keep typing your password for sudo & gksu commands.

---

### Post by Ariya243 on 2011-03-25
It won't work too!

gksu gedit /etc/sudoers

I get this in another window;

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by Smart Viking on 2011-03-25
Then run a live CD and do it from there, mount the file system and do something like
```
visudo -f /media/<mountpoint>/etc/sudoers
```

---

### Post by luceerose on 2011-03-25
Recovery won't accept your usual password because it wants the root password. The only way to give it that would be if you had actually assigned a password to the root user.
Did your username actually get changed, or was a new user created ?
Have you tried logging in using your old username ?

---

### Post by WorMzy on 2011-03-25
> **Ariya243 said:**
> I tried that too. 
Once in recovery and in root shell, it asks for root password, which I give, for that's the only one I have. But it says that it is not the password.

Are you using a non-Ubuntu distro? On Ubuntu the root password should be disabled, and, as a result, you shouldn't be asked for it. If you've set a root password, then you'll need to use that, not your personal password. If you haven't set a root password, and you're being asked for one, then follow Smart Viking's instructions.

> **larsenguitars said:**
> To edit sudoers file, type the following into either terminal or run dialog;
```

gksu gedit /etc/sudoers

```

No. Wrong. _**Never**_ edit sudoers like that. One slight mistake and you'll end up in a similar position to Ariya is in now. The only correct way to edit the sudoers file is through the visudo command.

```
sudo visudo
```

The visudo command prevents you from breaking sudo by checking the file before letting you exit. If the changes you've made will cause sudo to stop working, then it'll tell you to fix the file, or abandon the changes.

---

### Post by Ariya243 on 2011-03-25
Thanks!

Got the sudoers file corrected, but not from the Live CD, as I don't know where that is. I used Puppy Linux and changed the sudoers file without a problem. I find that Puppy Linux can go anywhere and change any file in any OS! 
I forgot that I had Puppy Linux, and now I won't let it go!

Thanks for the help, guys! :) 
How to put this as solved?

Larsenguitars, I changed the user name with usermod command, usermod -l newname -m -d /home/newname oldname

By the way, I found that I can change the name of the home folder using Puppy Linux too few minutes ago!

---

### Post by WorMzy on 2011-03-25
> **Ariya243 said:**
> Thanks!

Got the sudoers file corrected, but not from the Live CD, as I don't know where that is. I used Puppy Linux and changed the sudoers file without a problem. I find that Puppy Linux can go anywhere and change any file in any OS! 
I forgot that I had Puppy Linux, and now I won't let it go!

Thanks for the help, guys! :) 
How to put this as solved?

Just above the first post on the page, on the right-hand side, there's the "Thread tools", click that, and choose the "Mark as solved" option. :)

---

### Post by Ariya243 on 2011-03-25
Thank you, guys!

Have nice day!!!:D

---

