---
title: "scripting help!"
date: 2011-04-14
forum: General Help
---

### Post by Kyomaru on 2011-04-14
Hey all! So, recently, I've been trying to learn more about scripting, and I also heard about crontabs and cronjobs, ect. so I thought to myself, "i could make a script that would upgrade and reset my system, without me having to be there the whole time"
i know that this can be done through echos and sudo -S, but i still need a little help.

my main problem is, i want it to go this order
upgrade-> Reboot
because of this, i cannot use &, because it will just do them both, and i want reboot to be imediate, so it would just reboot. I also do not want to have to execute two seperate scripts, because some upgrades take more or less time than others. ( i dont want an time limit of 1hr, cause it might not get finnished, or it might have to wait forever)

so far this is what i have:

```
#/bin/bash

clear
echo "..."
sudo -S apt-get upgrade -y
...
clear
echo "..."
sudo shutdown -r now
end
```

so yeah, "..." is where the password would go, and where i have the ... is where what i need needs to go. if anyone could help me out, id really appreciate it.

i was intentionaly thinking about using a return value of 0, but idk if when upgrade finishes successfully, if it returns a 0 or not. but id really appreciate the help. thanks:KS

---

### Post by ~Plue on 2011-04-14
> **Kyomaru said:**
> 
my main problem is, i want it to go this order
upgrade-> Reboot

you can use a double &. it'll wait for the previous command to be completed before executing the latter one

> **Kyomaru said:**
> 
echo "..."
sudo -S apt-get upgrade -y

i don't think that would work because the password is echoed before sudo is run.
instead, piping the password to sudo would do it
```
*echo "password" | sudo -S * apt-get upgrade -y
```
i hope you know what you're doing because the password would be visible to anyone who opens the file.
a much better option would be to run the script using sudo instead of including the password within it

**EDIT:** reread your post about running this as a cronjob. in that case, you can simply put it in roots crontab so that it doesn't require a password

---

### Post by idoitprone on 2011-04-14
read command? it allows you recieve input from the console

```
read -p "password?:" pass

echo $pass | sudo -S
```

then you can piple the variable to sudo

you can simplify your script by using &&               ## edit did not realize that guy above me already mention this chracter

cmd1 && cmd2

Which the the konsole excute cmd2 only if cmd 1 exit with status 0
To understand what is status 0 try echo $? when you suceed a command and failed an command
[http://www.gnu.org/software/bash/manual/bashref.html#Lists](http://www.gnu.org/software/bash/manual/bashref.html#Lists)

OR

dont bother adding sudo to in your script

when you start your script
try
```
sudo script.sh

```
it will ask for your password of course

so the script runs in a subshell with root access.

---

### Post by Kyomaru on 2011-04-14
well thanks for the help. i will try what you guys have in mind right now. 

> i hope you know what you're doing because the password would be visible to anyone who opens the file.
a much better option would be to run the script using sudo instead of including the password within it

i dont have to worry about this too much, as i am really the only one who knows enough about linux to find this stuff out. my brother and parents just use this computer for internet, and i wasnt planning on distributing my copy. lol. sorry for the confusion. 

> Which the the konsole excute cmd2 only if cmd 1 exit with status 0
To understand what is status 0 try echo $? when you suceed a command and failed an command
[http://www.gnu.org/software/bash/man...ref.html#Lists](http://www.gnu.org/software/bash/man...ref.html#Lists)

thank you for your help as well. this site looks useful, so i appreciate a link. thanks!

---

### Post by matt_symes on 2011-04-14
Hi

```
sudo apt-get update
```first. Find out what's changed. Run under roots crontab. No need for sudo.

Kind regards

---

