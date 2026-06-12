---
title: "run a script as root after 4-5 sec of gnome startup?"
date: 2009-12-01
forum: General Help
---

### Post by roozbeh on 2009-12-01
Hi...

i have problems using all network managers to create an adhoc connection and connect to it automatically.
But using iwconfig.ifconfig i can do that.

The only problem is that i have to run my script twice to make it work.
running first time..it doesnt work.

Also i've used startup manager to add to it,but it seems there also it doesnt work.

So is it possible to run it twice for example after 3-4 sec. after gnome is started?

---

### Post by doas777 on 2009-12-01
just create a script like this:
```

#!/bin/bash
sleep 5 #number of seconds
gksu <command>

```

then point your startup manager to execute the script. the script will sleep for the predetermined amount of time, and then run your command using gksu (which will run it as admin, and prompt for your password).

---

### Post by Primefalcon on 2009-12-01
you could also add the script to roots crontab, it'd exeecute the script as root then

read this
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

but to enter the roots crontab use this

```
sudo crontab -e
```

---

### Post by roozbehid on 2009-12-01
> **doas777 said:**
> just create a script like this:
```

#!/bin/bash
sleep 5 #number of seconds
gksu <command>

```

then point your startup manager to execute the script. the script will sleep for the predetermined amount of time, and then run your command using gksu (which will run it as admin, and prompt for your password).

is it possible to use gksu with my password,so it doesnt prompt for password?

thnks so much

---

### Post by raktarok on 2009-12-01
Or you can add the lines of the above script in the file /etc/gdm/PostLogin/Default. (If there is no such file there, create it.) The file is read after login and the commands are run as root. You have other options too, like adding the commands to the file /etc/rc.local. 
Post again if you can't make it work and good luck!

---

### Post by roozbeh on 2009-12-02
i'll try this thank you so much

---

### Post by roozbeh on 2009-12-03
> **raktarok said:**
> Or you can add the lines of the above script in the file /etc/gdm/PostLogin/Default. (If there is no such file there, create it.) The file is read after login and the commands are run as root. You have other options too, like adding the commands to the file /etc/rc.local. 
Post again if you can't make it work and good luck!

this seems to be broken.
i searched in google and it seems 2-3 years it is broken.

anyway didnt worked for me.


by the way, is it possible to use sudo like this
sudo <your_password> program 
?
so i dont have to enter it?

---

### Post by raktarok on 2009-12-03
Hmm..I just checked in my laptop and creating the file /etc/gdm/PostLogin/Default is working for me. 
anyway, there are plenty of other routes you can take.

1) You can add the sleep line and the command in the file /etc/rc.local. They will be run as root, so no need for password.

2) You can add this line to the file /etc/crontab.
```
@reboot root sleep <no_of_secs>; <your other command>
```
Without the brackets of course. The commands will be executed in order as the root user,as specified after @reboot.

3) You can add this line to the file /etc/sudoers so that you don't need password for your particular command. 
Use the command **sudo visudo** to edit that file.
```
<your_user_name> ALL=(root) NOPASSWD: <command_needing_password>
```
Again, without the brackets <>..If you decide to use the above line, then you will still need to add sudo before the command to use it, but it won't ask for a password now.


4) Regarding your last question, you can try this:
```
echo <your_password> | sudo -S <command>
```

As you see, there are many ways of doing things! All of them should work, but feel free to pick any.

---

### Post by roozbeh on 2009-12-04
thank you...
well i guess you said it more than enough.

thanks again

PS. is there a way i mark topic as solved?i've seen some topics marked this way....

---

### Post by maximilianyuen on 2009-12-04
> **roozbeh said:**
> thank you...
well i guess you said it more than enough.

thanks again

PS. is there a way i mark topic as solved?i've seen some topics marked this way....

love to know too:p

---

### Post by bodhi.zazen on 2009-12-04
> **roozbeh said:**
> thank you...
well i guess you said it more than enough.

thanks again

PS. is there a way i mark topic as solved?i've seen some topics marked this way....

> **maximilianyuen said:**
> love to know too:p

The OP ([oozbeh]("http://ubuntuforums.org/member.php?u=213882") on this thread) can do so via "Thread tools" at the top.

---

