---
title: "Automate sudo password in script"
date: 2010-06-15
forum: General Help
---

### Post by e24ohm on 2010-06-15
Folks:
I am building a script; however, I need to run a few commands as sudo from the script. Is it possible to call upon a hidden file, which has my sudo password, or a username and corresponding password from the script? If so, what commands do I use?

Thank.

---

### Post by Chesamo on 2010-06-15
> **e24ohm said:**
> Folks:
I am building a script; however, I need to run a few commands as sudo from the script. Is it possible to call upon a hidden file, which has my sudo password, or a username and corresponding password from the script? If so, what commands do I use?
Not that I'm aware of. I get around this by adding the following lines in my script:
```
if [ $UID -ne 0 ]; then
sudo $0
else

<SCRIPT GOES HERE>

fi
```
This negates the need for sudo commands in the script, as everything is run sudo. If this is not possible for you (certain commands must be executed as non-root, for example), I would suggest running ```
sudo pwd
``` at the start of the script so the user enters the sudo password right off the bat. Assuming the next sudo command happens before the sudo timeout, you should be fine.

---

### Post by jamesorr on 2010-06-15
> **e24ohm said:**
> Folks:
I am building a script; however, I need to run a few commands as sudo from the script. Is it possible to call upon a hidden file, which has my sudo password, or a username and corresponding password from the script? If so, what commands do I use?

Thank.

Don't do that.  Edit the /etc/sudoers file so that you can run that script without providing a password.  For example ...

e24ohm ALL=(ALL) NOPASSWD: myscript

That line means that your username running on any terminal acting as any user "ALL=(ALL)" can run myscript without providing a password.

---

### Post by e24ohm on 2010-06-15
> **jamesorr said:**
> Don't do that.  Edit the /etc/sudoers file so that you can run that script without providing a password.  For example ...

e24ohm ALL=(ALL) NOPASSWD: myscript

That line means that your username running on any terminal acting as any user "ALL=(ALL)" can run myscript without providing a password.would that work if i need to run a command with sudo access from my script?

---

### Post by e24ohm on 2010-06-15
> **Chesamo said:**
> Not that I'm aware of. I get around this by adding the following lines in my script:
```
if [ $UID -ne 0 ]; then
sudo $0
else

<SCRIPT GOES HERE>

fi
```
This negates the need for sudo commands in the script, as everything is run sudo. If this is not possible for you (certain commands must be executed as non-root, for example), I would suggest running ```
sudo pwd
``` at the start of the script so the user enters the sudo password right off the bat. Assuming the next sudo command happens before the sudo timeout, you should be fine.thanks for the help. I am trying to get the script to automatically supply the password for sudo, so no user intervention is needed. I am trying to create backup sets, and run chmod with sudo to modifiy the attributes of the file.

---

### Post by jerome1232 on 2010-06-15
Why not just run the script as root.

ie sudo myscript

---

### Post by e24ohm on 2010-06-15
> **jerome1232 said:**
> Why not just run the script as root.

ie sudo myscriptI hope to use cron to automate the usage of the script. would I be able to run a cron job as root?

---

### Post by vttay03 on 2010-06-15
You can pipe your password into sudo with the following option:

```

echo password | sudo -S command

```

This will allow the script to run without prompting for a password.  However, this method poses a security risk since you're storing your password in plain text.  If you're on a computer with lots of other users, this probably isn't a good idea.

---

### Post by e24ohm on 2010-06-15
> **vttay03 said:**
> You can pipe your password into sudo with the following option:

```

echo password | sudo -S command

```

This will allow the script to run without prompting for a password.  However, this method poses a security risk since you're storing your password in plain text.  If you're on a computer with lots of other users, this probably isn't a good idea.

Understand - and this might be an option. I seem to remember reading somewhere that SUSE uses a hidden password file, when trying to map network drives to NTFS/window domain shares. I was hopping to do something similar.

---

### Post by jerome1232 on 2010-06-15
yes you can, if you add it to roots crontab

---

### Post by bodhi.zazen on 2010-06-15
You can also use expect.

[http://www.linux.com/archive/feed/56066](http://www.linux.com/archive/feed/56066)

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

In general, if part of a script is to be run as root, the entire script should be owned by root, rw by root only, and run as root (sudo).

If you need to run a command within the script as a non-root user, again use sudo

sudo -u user command

---

### Post by e24ohm on 2010-06-15
> **bodhi.zazen said:**
> You can also use expect.

[http://www.linux.com/archive/feed/56066](http://www.linux.com/archive/feed/56066)

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

In general, if part of a script is to be run as root, the entire script should be owned by root, rw by root only, and run as root (sudo).

If you need to run a command within the script as a non-root user, again use sudo

sudo -u user command
Ok thanks - I will check these out...

---

### Post by jamesorr on 2010-06-15
> **e24ohm said:**
> would that work if i need to run a command with sudo access from my script?

It could, though best would be to run the entire script as root.

If you add it to roots crontab as jerome1232 suggests you don't need to worry about passwords at all.

The solutions for piping a password in seem ... inadvisable.  It may not be a big deal on a closed private PC nobody else is going to use, but it's a bad habit.

---

### Post by e24ohm on 2010-06-25
> **jamesorr said:**
> It could, though best would be to run the entire script as root.

If you add it to roots crontab as jerome1232 suggests you don't need to worry about passwords at all.

The solutions for piping a password in seem ... inadvisable.  It may not be a big deal on a closed private PC nobody else is going to use, but it's a bad habit.How do I add the job to root's cron job?

I found this link, and HowTo link.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

and it says that it is not best practice to modify the /etc/crontab file.

so if i put my job in /etc/cron.d
and use sudo in the file, would that work?

---

### Post by cryptotheslow on 2010-06-25
Correct it is not wise to directly modify the crontab file directly. Use the crontab command.

To add an entry to root's crontab you would use this command:
```
sudo crontab -u root -e

```This will open a text editor. root most likely will have no cron jobs set already so you will be presented with a new crontab which will simply contain one line like this:

```
# m h  dom mon dow   command

```You can enter the new entry on the next line.

For example I have a cron entry to run each day to run a script that rotates some ftp backup files around. The crontab looks like this:

```
# m h  dom mon dow   command
07 23 * * * /home/ftpuser/upload/rotate > /dev/null 2>&1

```What that means is at 23:07 every day the script /home/ftpuser/upload/rotate is run.

The > /dev/null means any standard output from the script is sent to the null device (i.e. blackholed)

The 2>&1 directs any STDERR output to STDOUT which we have already set to route to /dev/null

So effectively the script will produce no output at all i.e. run silently.

---

### Post by e24ohm on 2010-06-25
> **cryptotheslow said:**
> Correct it is not wise to directly modify the crontab file directly. Use the crontab command.

To add an entry to root's crontab you would use this command:
```
sudo crontab -u root -e

```This will open a text editor. root most likely will have no cron jobs set already so you will be presented with a new crontab which will simply contain one line like this:

```
# m h  dom mon dow   command

```You can enter the new entry on the next line.

For example I have a cron entry to run each day to run a script that rotates some ftp backup files around. The crontab looks like this:

```
# m h  dom mon dow   command
07 23 * * * /home/ftpuser/upload/rotate > /dev/null 2>&1

```What that means is at 23:07 every day the script /home/ftpuser/upload/rotate is run.

The > /dev/null means any standard output from the script is sent to the null device (i.e. blackholed)

The 2>&1 directs any STDERR output to STDOUT which we have already set to route to /dev/null

So effectively the script will produce no output at all i.e. run silently.

thanks...this is helpful...

What is the difference between /etc/cron.d and adding it to crontab -e -u root?

---

### Post by cryptotheslow on 2010-06-25
crontab -e -u whateveruser

Creates / edits a crontab for that user.

/etc/cron.d is system wide and you need to specify the user for the action to be run under within the file.

Have a look at /etc/cron.d/anacron and you will see what I mean... the user "root" is specified within the command line.

I guess which method you choose to use comes down to personal preference on a home PC.

---

### Post by e24ohm on 2010-06-25
> **cryptotheslow said:**
> crontab -e -u whateveruser

Creates / edits a crontab for that user.

/etc/cron.d is system wide and you need to specify the user for the action to be run under within the file.

Have a look at /etc/cron.d/anacron and you will see what I mean... the user "root" is specified within the command line.

I guess which method you choose to use comes down to personal preference on a home PC.

Ok understand.

I have a job labled makefolder in /etc/cron.d

# m h dom mon dow command
0-59/1 * * * * sudo /home/user00/Documents/makefolder.sh

my makefolder.sh make a directory with a time stamp of time created. I am running the job every 1 minute for testing purpose; however, the folder is being created to the /home/user00 level, not the /home/user/Document folder. Do you know why this would be?

---

### Post by cryptotheslow on 2010-06-25
Can you post up the contents of makefolder.sh inside CODE tabs here?

You probably need to either do a "cd /home/user00/Documents" command before the make directory one.

Or explicitly give the full path name when making the folder.

It sounds like it is just creating the folder in whatever is the current working directory of the user, which by default will be their home folder.

---

### Post by e24ohm on 2010-06-25
> **cryptotheslow said:**
> Can you post up the contents of makefolder.sh inside CODE tabs here?

You probably need to either do a "cd /home/user00/Documents" command before the make directory one.

Or explicitly give the full path name when making the folder.

It sounds like it is just creating the folder in whatever is the current working directory of the user, which by default will be their home folder.


I copied it into the /bin folder so all I have to do is use makefolder.sh, instead of ./makefolder.sh

makefolder.sh script
```
#!/bin/bash
mkdir $(date +%Y%m%d_%H%M%S)
```

The cron triggers at the correct time; however, the folder is getting made in 
/home/user00.

In addition, I am using

crontab -e

from user00 so it is a user script.

I was wrong in my previous code.

my cron job is the following
```
0-59/2 * * * * makefolder.sh /home/user00/Documents
```

---

### Post by cryptotheslow on 2010-06-26
I don't think you can set the working directory like that within the crontab.

For this one user your script would need to be:

```
#!/bin/bash
cd /home/user00/Documents
mkdir $(date +%Y%m%d_%H%M%S)
```

And your crontab:

```
0-59/2 * * * * makefolder.sh
```


If you need the same script to work for multiple users, the script would be:

```
#!/bin/bash
cd ~/Documents
mkdir $(date +%Y%m%d_%H%M%S)
```

The ~ being the descriptor for the home directory of whatever user is running the script.

---

### Post by e24ohm on 2010-06-27
> **cryptotheslow said:**
> I don't think you can set the working directory like that within the crontab.

For this one user your script would need to be:

```
#!/bin/bash
cd /home/user00/Documents
mkdir $(date +%Y%m%d_%H%M%S)
```

And your crontab:

```
0-59/2 * * * * makefolder.sh
```


If you need the same script to work for multiple users, the script would be:

```
#!/bin/bash
cd ~/Documents
mkdir $(date +%Y%m%d_%H%M%S)
```

The ~ being the descriptor for the home directory of whatever user is running the script.

Since you cannot put ./makefolder.sh, it is assumed that you have copied the script into the /bin folder?

---

### Post by e24ohm on 2010-06-27
> **cryptotheslow said:**
> I don't think you can set the working directory like that within the crontab.

For this one user your script would need to be:

```
#!/bin/bash
cd /home/user00/Documents
mkdir $(date +%Y%m%d_%H%M%S)
```

And your crontab:

```
0-59/2 * * * * makefolder.sh
```


If you need the same script to work for multiple users, the script would be:

```
#!/bin/bash
cd ~/Documents
mkdir $(date +%Y%m%d_%H%M%S)
```

The ~ being the descriptor for the home directory of whatever user is running the script.

```
#!/bin/bash
cd /home/user00/Documents
mkdir $(date +%Y%m%d_%H%M%S)
```
Thank you so much - the recommendations worked great. The folder is now generating in the user's Document folder at the correct level.

Is used crontab -e with the following code
```
0-59/5 * * * * /home/user00/Documents/makefolder.sh
```

Question: why is the script running without me using the
```
./makefolder.sh
```

In addition, I have deleted the script from the /bin folder.

---

### Post by e24ohm on 2010-06-28
Question:
I am reviewing the possiblities of using machine wide cron jobs, which would be located in **/cron.d**; however, do I want to specify root or sudo, to have root access for the job?

Would it be better to just add the job as crontab -e -u root

I am using the follwoing item to help, but it leaves a few questions unanswered, or I'm not understanding.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

thank you.

---

