---
title: "echo text to /etc/sudoers - permission denied"
date: 2012-02-19
forum: General Help
---

### Post by Kissell on 2012-02-19
I finally figured out that the reason my path never sets is it needs to be set inside the /etc/sudoers file because when I'm doing a lot of admin work I run "sudo -s" so I don't have to type sudo in front of every command...  anyway, I wanted to put this in my installation script and get a weird error...  even when I use sudo I can't append text to that file...  anyone know why or how to "fix" this?  

BTW: It does work if I run do it without "sudo" if I'm already in sudo mode with "sudo -s"...  however, I need the installation script to be run as the regular user so it can do user specific things, like let set power settings using gconf, because "sudo -u" doesn't work to do that from inside the "sudo -s" mode.  I'm just trying to get everything to work with a single script.

```
myuser@PC:~$ sudo echo " " >> /etc/sudoers
```
> 
-bash: /etc/sudoers: Permission denied


---

### Post by jacob.david on 2012-02-19
I'm not sure what you are trying to say here.
Why do you want to append a empty string to /etc/sudoers?
You can't set path inside a sudoers file. You can only edit it using visudo and it is safe to do as it warns of any errors. 
Do you have env_reset in your /etc/sudoers? If yes that will reset all the environment variable being inherited from parent shell.
By default, the env_reset option is enabled. This causes commands to be executed with a minimal environment containing the TERM, PATH, HOME, MAIL, SHELL, LOGNAME, USER, USERNAME and SUDO_ variables in addition to variables from the invoking process permitted by the env_check and env_keep options. This is effectively a whitelist for environment variables.

---

### Post by yetiman64 on 2012-02-19
> -r--r----- 1 root root 574 2011-09-12 05:09 /etc/sudoersJust note that file is **read only** even **for root**. The previously mentioned use of **visudo** (as root with "sudo visudo") is the safest way to edit the file. 

Note, damaging this file, it is possible to lose admin privileges (it controls them) for your current sudo user account, not fun to have to fix ;).

---

### Post by Kissell on 2012-02-19
I don't care about appending an empty string to sudoers, I just used that as an example to show that I can't append a string.

I have locked myself out several times messing with this...  luckily I created an admin backdoor account, because sudo is completely worthless when you lock yourself out by screwing up here...  it would have been a huge pain with Live CDs and rebooting every time, if I couldn't have logged in as a root user.

So I tried changing the permission with "sudo chmod 640 /etc/sudoers" first, then appending to the file with "sudo echo" but sudo refuses to work when the file permissions aren't "440"..  if the file is writable, you're screwed and locked out of admin rights.

The problem with visudo is that it's a visual editor and I want to do this from my installation script automatically...  I want it to ask me for my password for sudo and then modify the path stored inside that file.

---

