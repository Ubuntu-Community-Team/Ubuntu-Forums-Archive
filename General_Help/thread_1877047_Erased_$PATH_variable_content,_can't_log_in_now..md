---
title: "Erased $PATH variable content, can't log in now."
date: 2011-11-07
forum: General Help
---

### Post by jayjones01 on 2011-11-07
I accidentally changed the PATH variable to nothing, after that i couldn't even use the ls command. Thought reloging to ubuntu would reset the PATH variable value, but now it doesn't let me log in as admin (when i try to login it writes some stuff in a terminal, then go back to login window). All i can do now is access to the guest account, but I don't know how to get admin privileges as a guest. I can't boot from a CD or flash drive, don't know why but my laptop just won't boot Ubuntu (i had to install from windows).

I'm using ubuntu 11.10, any help is greatly appreciated :D

---

### Post by tors on 2011-11-07
Does "sudo" work?

guest@localhost> sudo -s

or

guest@localhost> sudo vim /etc/environment

---

### Post by matt_symes on 2011-11-07
Hi

You can always use full paths

```
/usr/bin/sudo /usr/bin/nano /etc/environment
```Enter your password. It will not be echoed to the screen.

Add you path back. This is mine.

```
matthew@matthew-laptop:~$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
matthew@matthew-laptop:~$
```Ctrl + o to save and ctrl + x to exit.

Then reboot.

```
/usr/bin/sudo /sbin/reboot
```**EDIT:** From where did you remove the path variable or set it to nothing ? What did you do ?

Kind regards

---

### Post by jayjones01 on 2011-11-07
I can't use sudo in a guest account, but i managed to boot into recovery and do "sudo nano /etc/environment". The file displays:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"

which seems fine to me. I guess that when i try to login as admin it loads its own admin PATH variable? (reason why guest and root have different PATH values) so how do i change my admin user PATH variable from root? because the /etc/environment file is fine and i still can't login as admin. 


As additional info, what I did under my admin account was type "sudo export PATH=*smthing*" and i missed typing $PATH: before what i wanted to add.

---

### Post by ajgreeny on 2011-11-07
What does the command ```
echo $PATH
``` output in terminal.  In my case it is slightly different from the output of **cat /etc/environment** as it has the **/home/*username*/bin** folder added, so presumably gets the information from another source?

Or is the added path folder simply a result of my ~/.bashrc file?

---

### Post by jayjones01 on 2011-11-07
from the root terminal (recovery mode) the **echo $PATH** command output is slightly different from **cat /etc/environment**. The order of the folders is different and the second has the folder **/usr/games** folder which the first one doesn't.

About your questions... I have no idea how users and PATH variables work.

---

### Post by matt_symes on 2011-11-07
Hi

How did you overwrite your PATH variable ? Where did you do it ? Did you edit your .bashrc file or any other of the files.

/etc/environment is only one place where you can change your path so where did you do it ?

We can't really help you until you tell us what you did. Otherwise we can only suppose and guess at best.

Kind regards

---

### Post by jayjones01 on 2011-11-07
What i wanted to do was to change the java path, I followed some guides and edited some files like .profile .bashrc and maybe others. Nothing really happened after editing those files, but then i tried the command **export PATH=*java location*** and i forgot to write **$PATH:** before adding the java location, so the PATH variable was replaced with only the java location. After this i could not issue any command (not even ls) so i restarted the system and now i can't login into my admin account.

---

### Post by matt_symes on 2011-11-07
Hi

It's very hard to help you as you are the most vague poster i have tried to help for a long while.

I have no idea what you have changed and i am not now even sure if your problem is the fact that you have changed your PATH variable or that you cannot log in.

For you to get any help you have to be far more specific than vague hand waving such as 'i changed some files and followed some guides'.

Can you log into the recovery console ? If you can, have you tried to  create a new user and login as that user ? If you can login as that  user can you run commands ?

Kind regards

---

### Post by jayjones01 on 2011-11-07
Once again:

I typed **export PATH=*java location*** so therefor my PATH variable had no content other than the java location. After that i could not issue any command in the terminal, i restarted the system and after that i cannot login with my admin account. This is obviously a result of removing the content of the admin account path variable, because the guest account works just fine. So how do I fix the admin account PATH variable from the recovery console (I already said I can log into the recovery console), that is my question and nothing else.

---

### Post by ajgreeny on 2011-11-08
> **jayjones01 said:**
> Once again:

I typed **export PATH=*java location*** so therefor my PATH variable had no content other than the java location. After that i could not issue any command in the terminal, i restarted the system and after that i cannot login with my admin account. This is obviously a result of removing the content of the admin account path variable, because the guest account works just fine. So how do I fix the admin account PATH variable from the recovery console (I already said I can log into the recovery console), that is my question and nothing else.
I am not sure about this, so don't rush to do it until others have made comment, but perhaps if you boot into recovery mode and from there run the command ```
export PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
``` it may set your path back to what it should be.

As I say, I am not an expert in this situation, but as far as I can see, that command should undo what you did and put things back to the default.

Good luck!

---

### Post by matt_symes on 2011-11-08
Hi

> **jayjones01 said:**
> Once again:

I typed **export PATH=*java location*** so therefor my PATH variable had no content other than the java location. After that i could not issue any command in the terminal, i restarted the system and after that i cannot login with my admin account. 


How did you restart your PC ? Did you just hit the power button ?

> 
This is obviously a result of removing the content of the admin account path variable, because the guest account works just fine. Not necessarily, because the command 'export PATH=...' - assuming you typed it at the command line and did not add it to a file - should have just affected your current shell and should have been reset after reboot; unless you entered it into a file that is sourced every time you login.

This is why you may have deeper problems than you think and why we have been trying to find out exactly what you did. You may not be able to login due to an issue with X.

If all you did was type 'export PATH=....' at the command line but you then hit the power button without shutting down correctly then your issue may be elsewhere.

> So how do I fix the admin account PATH variable from the recovery  console (I already said I can log into the recovery console), that is my  question and nothing else.Your issue here may not be your PATH variable and that is all i am trying to ascertain.

A slight modification to ajgreeny's command.
[FONT=monospace]
[/FONT]```
export PATH=$PATH**:**/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

EDIT: I am, of course, assuming you are using a GUI.

Kind regards

---

### Post by ajgreeny on 2011-11-08
> **matt_symes said:**
> A slight modification to ajgreeny's command.
[FONT=monospace]
[/FONT]```
export PATH=$PATH**:**/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```EDIT: I am, of course, assuming you are using a GUI.

Kind regards
Whoops.  I forgot the colon in the command after $PATH.

I have edited my post to take account of that.

---

