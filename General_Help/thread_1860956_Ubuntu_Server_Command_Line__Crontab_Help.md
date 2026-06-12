---
title: "Ubuntu Server Command Line / Crontab Help"
date: 2011-10-15
forum: General Help
---

### Post by dkdsmk on 2011-10-15
Hi.

My experience with ubuntu and command line consists of 1 day trial and error.

What im trying to accomplish:
When computer gets turned on or reboots: logon automatically, and run a script that starts a minecraft server.

Problems i've encountered:

1.Need to login each time (any way to bypass this)?

2.Don't really understand the directory tree. Say it looks like this:
minecraft@minecraft:~$ (i do cd ..)
minecraft@minecraft:/home$ (cd .. again)
minecraft@minecraft:/$ (another folder but prompt looks almost like the first. Im used to oldschool dos where you could always tell if you were at the bottom of the tree (c:\) or in a subfolder (c:\minecraft). Sorry if this seem too basic :)

Im guessing the tilde symbol is "too many characters to show".
Any way to list the whole path?

3. Is there any directory specially made for saving data? The home folder for instance? Right now i have it deposited at minecraft@minecraft:~$ next to home and disk.

4. I would like the server to start at reboot. I've looked at crontab for this. The problem is i dont know how to formulate the path. (at least i think thats the problem) In oldschool dos i guess it would be c:\home\minecraft\minecraft\ and the command in that folder: "Java -Xmx1024M Xms1024M -jar minecraft_server.jar nogui"

I didnt know if crontab could handle all those additional settings so i put them all in a "sh" script file and thought i'd run just the script from crontab. Im sure both ways probably work though.

Havent gotten crontab to do what i want though. Im guessing the path gets messed up.

I've tested everything by manually navigating and giving the command. It works flawlessly. All i wanna do is remove the need for login and issue the command at startup.

Keep in mind that i am a total beginner at linux. Thank you for any help. ;)

---

### Post by dcstar on 2011-10-15
> **dkdsmk said:**
> 
What im trying to accomplish:
When computer gets turned on or reboots: logon automatically, and run a script that starts a minecraft server.


/etc/rc.local

Do a search for detailed info on using this.

---

### Post by dkdsmk on 2011-10-16
I tried following the info in this thread:

[http://ubuntuforums.org/showthread.php?t=1709280](http://ubuntuforums.org/showthread.php?t=1709280)

Nothing starts at boot. Cant find anything in syslog either.
This is driving me crazy.

---

