---
title: "Desperately need help with a Ubuntu OS server"
date: 2012-08-20
forum: General Help
---

### Post by JunkyPic on 2012-08-20
Hello ladies and gents,

Recently I have bought a dedicated server to host a medium [Tekkit]("http://www.technicpack.net/tekkit/") (it's a [Minecraft]("http://www.minecraft.net/") related thingy) server. The server specks are as follows: 
CPU - Intel Xeon E3 1230
RAM - 16 GB DDR3
HDD - 120 GB SSD
and unmetered 100Mbps internetz.

I'm fairly new to Linux and, for the most part, have no idea what I'm doing. My questions are these.
1. Thru a configurable file located in the Tekkit pack the amount of RAM that Tekkit can use can be set. Given that I will be hosting the Tekkit server and a Mumble/Teamspeak, how much RAM should I leave aside just for the OS to run as smooth as possible?

2. Can a complete installation of Tekkit and Mumble/Teamspeak be done via only the terminal?
If not, I'm considering installing KDE or Gnome, however, how will this affect the server's performance(if any)?
Please keep in mind that Tekkit itself uses a lot of CPU power and hogs up a lot of RAM. 

3. For file transfers I'm thinking of using FileZilla with Putty. Would you suggest otherwise?

4. As far as I know Java doesn't have a "designate OS"(Tekkit runs on Java). Could it be possible to pre-configure Tekkit on a Windows machine and simply transfer the files to the server after that? 

5. Where exactly could I find a detailed list of all the available commands in the terminal GUI?
I mean the "explain it to me like I'm 5" kind of detailed.

Thank you.

---

### Post by vandorjw on 2012-08-21
Hey JunkyPic,

You have bought a dedicated server with impressive specs. I would strongly recommend against installing gnome or kde.

Is Ubuntu server already installed, or are you in in charge of installation?

If it is already installed, then open-ssh is likely already installed and good to go.

if it is not, then take a look at this page.
[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

Putty and filezilla should work fine.

Installing and configuring tekkit on windows and transfering those files to Ubuntu server will likely fail.


I am not sure what tekkit configuration files contain, but I can only guess they record where everything that it needs is. Your java libraries on windows will not be in the same place as they will be on linux.

Another thing to consider is that windows machines use JRE by Sun/Oracle.

Ubuntu server will use open-jdk by default. This shouldn't cause any problems but tekkit might complain and say it wants JRE from Sun.


A list of all commands available in terminal you will not find.
What I can do, is this.

List Everything you need to do, and I'll tell you how to do it. "Copy and paste commands". and ill give an explanation as to what the commands do.

Cheers - CC7

Edit: Seems like I didn't answer everything. When I start my computer, it uses only 64MB ram. With 16GB of RAM, you can tell tiki to use 15.5GB and you'll be fine. (almost missed TS) I don't quite know how much TS needs, I cannot imagine it'll need more than a couple hundred mb. Linux memory management is awesome, so I wouldn't worry much about it.

If you wish, here is a list of my most frequently used commands and what they do.
I am going to assume you use a debian based linux distro.

COMMANDS
1. ls ~ list all the files and folders in your current folder.
2. dir ~ list all the files and folders in your current folder.
3. pwd ~ tells you what folder you are currently in.
4. cd ~ change directory/folder.
4 EXAMPLES:: 
cd /home/john :: this will put you in the folder john. 
cd .. :: This will put you in the folder "above", if you were in /home/john, you would be put in /home
cd - :: this will put you in the last folder you were in.

 
5. mv :: This is to move command. Use this to mv something from one folder to another.

6 rm :: remove file. Carefull with this. There is no recylce bin. Instead of using this, what I suggest is to create a folder called /recylcle-bin and mv files and folder to it. Delete them once you are sure you dont need them anymore.

7. mkdir - make a new directory. (create new folder)

8. nano ~ This is your text-editor.
Pressing controll+o (OH!) saves
Pressing controll+x exits.
pressing controll+w searches for words
pressing controll+c cancels whatever you were doing.
I dont remember if there is an undo. what I do, is exit, and re-open.

nano /path/to/file/file.txt will open file.txt

9. sudo - put this in front whenever you see "permission denied. Simular to sudo is,
su -c "command you wish to execute"

The difference is: sudo needs your password. su -c needs "root" password.

10. apt-get install "program name here"
11. apt-get remove "program name(s) here"
12. apt-cache search "search for program name here"

13. apt-get purge "program name" ==== same as remove, except that it nukes your configuration files as well. If you don't remove configuration files, then they will still be there next time you re-install. and if you did something wrong, that same mistake remains.

14. free -m  ::: this will show you your RAM usage in mega-bytes.


[B][COLOR="Red"]The terminal doesn't really contain have commands. What it does is allow you to execute programs. mv, rm, rmdir, mkdir, sudo, ... are all programs. You will find them in /bin, or /usr/bin, or in /usr/local/bin ... Linux has thousands of programs, most or all of which you can execute via terminal. That is why it is not possible to make an exhaustive list of everything.
[/COLOR][/B]

[http://en.wikipedia.org/wiki/Classpath_(Java)#Setting_the_path_to_execute_Java_programs](http://en.wikipedia.org/wiki/Classpath_(Java)#Setting_the_path_to_execute_Java_programs)

(I am sure you will need to read that sometime)

---

