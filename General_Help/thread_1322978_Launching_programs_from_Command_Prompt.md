---
title: "Launching programs from Command Prompt"
date: 2009-11-11
forum: General Help
---

### Post by Bat-man on 2009-11-11
Hello, I'm relatively new to linux/ubuntu.
I like doing a lot of my work through the terminal because it really gives you a feel for the system.
When i launch a program via symbolic link such as, for example, firefox.
I would type root#firefox
A firefox browser launches but i can't do anything else with that terminal window until i hit "ctrl c" to break that firefox launch. If i hit "ctrl c" it will close the firefox window and i can resume using the terminal.
Option 2 is to use the exec command: root# exec firefox
This will launch firefox and close the terminal window.

How can i launch a program and be able to resume using my terminal window normally?

Thank you in advance :)

---

### Post by Somme on 2009-11-11
```
 
<command> &

```
 
You'll be able to use it, tough, upon closing it, forked application will exit too.

---

### Post by Niko Johnson on 2009-11-11
i know its not the answer you were looking for....but why dont you just use 2 terminals?

---

### Post by Keith Hedger on 2009-11-11
just a point of interest you really should not be launching firefox as root! in fact its best not to use a root shell at all just use sudo if you need to use root privileges for a particular command

---

### Post by Bat-man on 2009-11-11
Awesome!

Thank you Somme! :)

That is exactly what i was looking for.

Any place where a newbie like me can go and read up on all these wonderful tips and tricks?

I was using root as a simplified example. I don't do much as root unless I'm fiddling with system files. --> [Keith Hedger]("http://ubuntuforums.org/member.php?u=77445")

I don't want to open 2 terminal windows because I've been in situations where I'm in the middle of something and just want to launch something else and continue working in the same directory i was working in. This would eventually lead to me having 8 terminals open and multiple programs launched from them. So I have 16 programs open and i am only using 8.

---

### Post by northern lights on 2009-11-11
> **Bat-man said:**
> Any place where a newbie like me can go and read up on all these wonderful tips and tricks?[http://www.linuxcommand.org/learning_the_shell.php]("http://www.linuxcommand.org/learning_the_shell.php")

---

### Post by Bat-man on 2009-11-11
Thank you Norther Lights.
This looks like a good read.

---

