---
title: "How do you make a program not ask for password at start?"
date: 2009-12-14
forum: General Help
---

### Post by killer1000001 on 2009-12-14
I added ipblock to the program startup list, but every time i login it asks for the password which gets really annoying, the path that it says the password is needed is as follows, "/usr/sbin/ipblock start_gui".
How would i change ipblocks privileges so it doesnt ask for a password everytime? Thanks.

---

### Post by killer1000001 on 2009-12-14
bump, tried google and couldnt find any help

---

### Post by llamabr on 2009-12-14
How do you start it?  does the gui ask for a password?  And did you put it somewhere to autostart on login or something?  If so, where?

I'm not familiar with this program, but I don't see why it should be asking for your password.

---

### Post by scragar on 2009-12-14
```
echo "%users  ALL= NOPASSWD: /usr/sbin/ipblock start_gui" | sudo tee -a /etc/sudoers
```

That should work.

For reference this gives all members of the users group ( %users ) access on any machine name(only really worth changing if you're copying this to lots of different places and want to be more security concious) to be not asked for the password (NOPASSWD) when running that program. Which it does by appending ( writing to the end) that rule to the sudoers configuration file.

---

### Post by killer1000001 on 2009-12-14
yea i dont see why it requests a password as start. I just right clicked the program in menu and checked "launch at startup".

---

### Post by llamabr on 2009-12-14
[http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

In looking further, is it because you need to run it with sudo?  If that's the case, this is a sudo question, not an ipblock question.

[http://maestric.com/doc/unix/ubuntu_sudo_without_password](http://maestric.com/doc/unix/ubuntu_sudo_without_password)

---

### Post by scragar on 2009-12-14
> **llamabr said:**
> [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

In looking further, is it because you need to run it with sudo?  If that's the case, this is a sudo question, not an ipblock question.

[http://maestric.com/doc/unix/ubuntu_sudo_without_password](http://maestric.com/doc/unix/ubuntu_sudo_without_password)

I find that very insecure and only steps away from running everything as root, which will seriously screw up your system. The password is there for multiple reasons, the most important is to make you think "do I really need to be doing this as root?"

Besides, writing your username in the sudoers file? That's what groups are for, to avoid breaking the sudoers file if you ever change or delete a user.

---

### Post by killer1000001 on 2009-12-14
yea thats what i mean it needs to run with sudo but i dont want to type my password just so the program can run

---

### Post by sgosnell on 2009-12-14
See if [this post](http://ubuntuforums.org/showpost.php?p=3280778&postcount=28), and the thread in general, help you out.

---

### Post by killer1000001 on 2009-12-14
ok weird. Even if i remove the program from startup programs, it "still runs". I already configured it in the gui to block https, so i try to connect to a few that i know it will block, it still blocks them. Then i open the program (which also goes to the system tray when hidden) and it shows the blocked websites. So for what ever reason ubuntu doesnt like the gui....

---

### Post by Puzzled Guy on 2009-12-14
If Ubuntu didn't ask you for your password for administrative tasks, it wouldn't be any safer from hackers that Windows is.

---

### Post by killer1000001 on 2009-12-15
I understand now! The gui is in administrator task. I expected the "Autostart" option in the gui to start the gui, but it just launches the ipblocker portion of it, not the gui portion of it. Im to used to peerblock :P

---

