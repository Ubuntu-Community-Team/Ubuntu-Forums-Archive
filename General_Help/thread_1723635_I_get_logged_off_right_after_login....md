---
title: "I get logged off right after login..."
date: 2011-04-07
forum: General Help
---

### Post by jgratero on 2011-04-07
I have the following problem: My xubuntu session is literally "kicking me out" every time I login. It appears as if everything is normal, and bam! Back to login screen again. Tried to switch to TTY, but no success, I got kicked out as well... :confused:

I've searched online, and the only thing related to what I'm experiencing is this:

[http://askubuntu.com/questions/20929/gnome-x-logs-off-immediately-after-login-which-logfiles-are-relevant](http://askubuntu.com/questions/20929/gnome-x-logs-off-immediately-after-login-which-logfiles-are-relevant)

Any ideas?

---

### Post by 3Miro on 2011-04-07
You are getting kicked out of a tty session? Have you let anyone mess with your machine?

Try booting with a live CD, then mount your /home partition and look at your
```
/home/your_usernam/.bashrc
```
file. You will need to hit Ctr + H to see the hidden files.

Does it end with "logout"?

---

### Post by jgratero on 2011-04-07
No, I am the only one using this machine in my office. Everybody else use Windows Vista, or XP.

I'll try what you suggest... I will confirm you the results in a moment!

Thanks for your reply!

---

### Post by 3Miro on 2011-04-07
Putting "logout" at the end of .bashrc is a common Linux prank. If XFCE fails to start, then it may be a problem with the saved session and sometimes the themes, but if the tty fails, then it is a bigger problem.

You can try to boot into recovery mode, then that may fix the issue. You can also try to make another user and then login as that user to see if the issue is with your user alone or the system in general.

You can try also to go into /home/your_username and delete all .something files and folders that have to do with xfce. This will mess all of your settings, but hopefully it will get you back to a working environment.

---

### Post by jgratero on 2011-04-07
No, there's nothing wrong on the .bashrc file (no "logout" at the end of the file)... I'm trying to delete the xfce configuration files on my home folder, but no success... I mounted the HD, but I am accessing the files as read only...

One question: Would it be possible from the Live CD add the guest account I created (and the one I have to use, because the login problem with the other one) to the sudo group? Change its privileges?

Thanks in advance...

---

### Post by jgratero on 2011-04-07
I can delete the files... sudo thunar... I will let you know the results...

Thanks in advance...

---

### Post by 3Miro on 2011-04-07
For graphical program you should use:
```
gksudo thunar
```
instead as sudo.

I think you can make a guest account with the LiveCD, but the only way I can think of is by using chroot, but this is rather involved.

Can you boot in failsafe mode (hold shift while booting to get the Grub menu up). Or can you select a failsafe session from the login screen.

---

