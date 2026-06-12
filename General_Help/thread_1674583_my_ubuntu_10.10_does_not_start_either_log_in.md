---
title: "my ubuntu 10.10 does not start either log in"
date: 2011-01-24
forum: General Help
---

### Post by karemlb on 2011-01-24
Hello,
i have the ubuntu 10.10 on my acer aspire laptop. 
recently the update manager was running to install packages updates, and  it has requested restart to complete changes, hence when the restart  began it has been corrupted in some way mentioning the message "error"  after several operations (in command, sorry i am not expert in it) and  then the system does not operate at all. 
so i tried to enter the menu, and reboot the ubuntu 10.10 recovery mode,  so it showed a table of choices among them (resume, dpkg, root...).  first of all i tried the dpkg (try to fix packages) and then when it  finish the system put the following: 
karem(my name)-laptop log in: 
here i get confused, what word or command shall i insert? because  whatever you put it requests your password, so when i fill in my  password, it says that the word is invalid. 
can you please provide me help. i like ubuntu 10.10 but it seems very complicated to a normal user like me.

i am ready to provide help as much as i know.

---

### Post by ajgreeny on 2011-01-24
When you see the **karem-laptop log in:** prompt, enter your username that you setup when you installed, hit enter, then when asked enter your password.  Nothing will show as you type your password, but it will still be seen by the system, so hit enter again and you should be logged in and see the prompt **username@karem-laptop:~$**

If needed, and you are still in a command line, now try the command ```
startx
```

---

### Post by xzinkx on 2011-01-24
exact same thing happened to me after a few updates. Will try this when I get home and post results.

---

### Post by karemlb on 2011-01-24
i tried it it didn't work what should i do?

---

### Post by ajgreeny on 2011-01-24
Try reinstalling any graphics card driver you had running before the updates.  It may be that a new kernel has been installed, and needs the driver reinstalled for it, if you are running a proprietary driver.

Can you boot properly to an older kernel from the grub menu?  If you can, that certainly points to the driver of your card being missing.

---

### Post by karemlb on 2011-01-25
can you put it as points to follow? i don't know how to do it. 
thanks

---

