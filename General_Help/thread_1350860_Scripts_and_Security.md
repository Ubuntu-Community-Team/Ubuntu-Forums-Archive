---
title: "Scripts and Security"
date: 2009-12-09
forum: General Help
---

### Post by Hunter2379 on 2009-12-09
I'm still sorta new to bash. Anyone have any idea's on different scripts that i could do that would give me a challenge while also allowing me to learn some more.

Also, i intend to go into a security field, like network security, Penetration Testing, software security, etc. 
My other question is how would i make money with linux while also working in one of these fields. Linux is free and it's open source so how would it work.

---

### Post by jbrown96 on 2009-12-09
How about this for an idea: 
Create a script that attaches to a mysql database, calculates md5sums of all files and stores them in the database (for added complexity store a checksum of the database in itself that is still valid when the ckecksum is stored), and logs all the changes to a file. 
That's a reasonably complex thing to do that will give you experience with many layers of Linux.

As far as making money from Linux, people make money because they are experts. There are very few people who really know Linux. Businesses need these people to keep their computers running, so they hire the experts (at a premium).

---

### Post by audiomick on 2009-12-09
The way to make money with Linux seems to be to offer services doing that which the client doesn't want to / doesn't have time to /  can't do himself.

the first two links at the bottom of this:
[https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html)
might help you with yout scripting.

---

### Post by Hunter2379 on 2009-12-09
Thank-you both

---

### Post by Hunter2379 on 2009-12-09
Any other less complex idea?

---

### Post by jbrown96 on 2009-12-09
A good beginning script is one that will transverse directories and output the file names of all directories, recursively. 

One thing that I've found recently that relates to security is sudo. You can do all kinds of neat things in /etc/sudoers. That's not specifically script related, but it will help you understand Linux security better. Here's my /etc/sudoers > # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%admin ALL=NOPASSWD: /usr/sbin/powertop
%admin ALL=NOPASSWD: /usr/bin/apt-get update
%admin ALL=NOPASSWD: /usr/bin/apt-get upgrade
%admin ALL=NOPASSWD: /usr/sbin/pm-suspend
%admin ALL=NOPASSWD: /sbin/reboot
%admin ALL=NOPASSWD: /sbin/fdisk -l


You can't edit the file with a normal text editor, so you need to use > sudo visudo

Another good thing to look into is cron. It's a scheduler that will automatically run commands at certain times. This is used a lot to automatically runs commands/scripts. 

If you really want to learn scripting, then I recommend learning a "real" scripting language. There's nothing wrong with bash, but I think that if you are new to programming, something like Python is much friendlier, and is used outside of Linux programming. You can do everything in Python that you can do in Bash, but not the opposite (although bash is very powerful).

---

### Post by Hunter2379 on 2009-12-09
Can cron be used for python programs also, and do you know any good website with pythin tutorials. I looked on google a bit and found a few.

---

### Post by jbrown96 on 2009-12-10
Python is supposed to have really good documentation. I've never read the beginning tutorials, so maybe I'm mistaken. If you are new to programming, I would buy a book that introduces you to programming. It will teach some good design practices, and hopefully you won't just be copy-and-pasting code examples. I recommend [this]("http://www.prenhall.com/goldwasser/") (shameless plug for two of my professors' book).

Cron can run any command. To execute a python command you do ```
python2.6 program.py
``` obviously you can use a newer version of python (I think 3.1 is current), and program.py gets replaced by the path and file name. So for a cron entry (assuming crontab and not cron.daily, cron.hourly, etc.), you would fill out the frequency columns, user, and then the command listed above.

Example /etc/crontab entry to run program.py at the top (0 minutes) of every hour, day, and month as user justin.
```
00 * * * * justin python2.6 /home/justin/program.py
```

---

