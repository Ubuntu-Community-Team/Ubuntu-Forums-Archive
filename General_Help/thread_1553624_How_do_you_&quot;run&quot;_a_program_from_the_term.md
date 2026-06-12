---
title: "How do you &quot;run&quot; a program from the terminal?"
date: 2010-08-15
forum: General Help
---

### Post by lwalper on 2010-08-15
OK, I'm stuck again.

I've downloaded VMware Server (the 428mb tarball), untarred it into its own directory.

In the help at [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo") I have followed the steps to the point where I am told

"If you already installed the packages listed on Step 1, you just need to change to your /usr/local/src directory (cd /usr/local/src) and run the commands that are listed."

How do I "run" the commands that are listed? I navigated to the correct directory and in the list I have,

bin doc etc FILES installer lib man sbin vmware-install.pl vmware-vix

The file vmware-install.pl is supposed to be a script I downloaded from one of the approved Ubuntu instructionals which is supposed to do all the "heavy lifting."

I've tried just entering the name of the file, doing the same with sudo, as well as trying any number of other words that I thought might remotely be what would actually "run" a file - to no avail. What file do I run and what is the command to run the file? I tried

run installer

and came up with several options:

No command 'run' found, did you mean:
Command 'zrun' from package 'moreutils' (universe)
Command 'runq' from package 'exim4-daemon-heavy' (main)
Command 'runq' from package 'exim4-daemon-light' (main)
Command 'runq' from package 'sendmail-bin' (universe)
Command 'grun' from package 'grun' (universe)
Command 'qrun' from package 'torque-client' (multiverse)
Command 'rn' from package 'trn' (multiverse)
Command 'rn' from package 'trn4' (multiverse)
Command 'rup' from package 'rstat-client' (universe)
Command 'srun' from package 'slurm-llnl' (universe)
run: command not found

And I don't see any "Run" command in the "HowTo" documentation.

If I can get VMware to run successfully I just may be able to divorce myself from my M$ box.

---

### Post by mhgsys on 2010-08-15
try running with ./ in front of it.

---

### Post by WorMzy on 2010-08-15
If you just type the file name, Ubuntu will look in your Path variable directories (/bin, /usr/bin, /sbin, /usr/sbin, etc) for a file with that name, which it probably won't find. Prepending "./" to the file's name makes Ubuntu look in the current directory for the file; likewise, "../" makes it look in the parent directory. You could use an absolute path too, so "/usr/local/src/vmware-install.pl" should do the same thing.

Also, you could open the file in the language's interpreter, so ```
perl vmware-install.pl
``` will run the script too.

---

### Post by oldos2er on 2010-08-15
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by DarthScape on 2010-08-15
sudo ./vmware-install.pl

---

### Post by lwalper on 2010-08-15
**mhgsys**
Thanks, sudo ./ worked. pbkac error? Absolutely!!

**WorMzy**
I was executing the command from within the folder. It doesn't read it's own local folder?

**oldos2er**
You gotta start somewhere?

---

### Post by mhgsys on 2010-08-15
nice, 

Don't forget to mark this thread as solved

---

### Post by WorMzy on 2010-08-15
> I was executing the command from within the folder. It doesn't read it's own local folder?

No, unless you explicitly tell it to look in the current directory with ./, it'll assume you're trying to run something from one of the Path variable directories. You can make it so that it always looks in the current working directory by adding ./ to the Path variable.```
PATH=$PATH:./
``` will temporarily add ./ to the Path variable for the shell you type it into.
```
echo 'PATH=$PATH:./' >> ~/.bash_profile
```
Should make the change permanent, but you'll probably need to log out and back in for it to take effect.

There's probably a good reason why ./ isn't in the Path variable by default, so use the above commands at your own risk.

---

### Post by Vaphell on 2010-08-15
i guess that . present in PATH would blur the distinction between system tools and custom scripts of the user. Also there are security risks attached.
Scenario:
1. as an ordinary user plant a malicious script named ls in let's say /tmp which is writable by all
2. wait for admin to enter /tmp and run ls to list files
3. ???
4. profit

---

### Post by WorMzy on 2010-08-15
That's more of an argument against logging in as root (or giving a normal user root privileges), but still, it's a possibility.

---

