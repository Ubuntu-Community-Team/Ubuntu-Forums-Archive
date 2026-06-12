---
title: "sudo- command not found for binary under /opt/ folder"
date: 2011-04-08
forum: General Help
---

### Post by ramsesiitr on 2011-04-08
Hi all,
I have installed the sparc-elf-gcc binaries under the /opt/ folder as described in Readme file. However, when I run the command
```
sudo sparc-elf-gcc
```it gives "sparc-elf-gcc command not found" error.

the $PATH variables are properly set in ~/.profile so that I can run command

```
sparc-elf-gcc
```without any problem from my user account.

What is the problem? How can I solve this?

Thanks in advance.

---

### Post by sanguinoso on 2011-04-08
IIRC sudo doesn't read your environment variables, so if you have set this path in your user profile it won't load it properly when using sudo. You can set your path in /etc/bash.bashrc (this is the systemwide bashrc) and then you will be able to use sudo.

---

### Post by ramsesiitr on 2011-04-08
> **sanguinoso said:**
> IIRC sudo doesn't read your environment variables, so if you have set this path in your user profile it won't load it properly when using sudo. You can set your path in /etc/bash.bashrc (this is the systemwide bashrc) and then you will be able to use sudo.

Thanks for the reply.
I copied and pasted the same $PATH variable into the /etc/bash.bashrc file and reboot the system. But still gives the same error.

Any other suggestions?

---

### Post by sanguinoso on 2011-04-08
What was the syntax of that $PATH variable did you do something like this? ```
export PATH=/path:/path
```

---

### Post by sanguinoso on 2011-04-08
Ok I figured it out, sorry for not testing my previous instructions first. If you add a line like this to your /etc/sudoers file. ```
Defaults        secure_path+="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/sanguinoso/bin"
```

This will set the path for sudo commands. Replace as necessary on your system.

---

