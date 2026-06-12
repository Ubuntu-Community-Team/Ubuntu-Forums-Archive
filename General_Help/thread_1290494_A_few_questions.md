---
title: "A few questions"
date: 2009-10-13
forum: General Help
---

### Post by lastoneleft07 on 2009-10-13
1. How can I show my desktop to my friends? I want him to connect & be able to see everything i'm doing

2. These Hard Drive shortcuts are stuck on my desktop and I can't send them to the trash bin.

3. Are there any widgets included with Ubuntu 9.04 64 bit? I know Mandriva had them already installed and right on the desktop

4. Im trying to install a plugin into Opera manually, and for some reason when I go to that folder it wont let me set the folder so I can change or copy stuff to it , It tells me "you are not the owner"

---

### Post by doas777 on 2009-10-13
as for your top two, yes, ubuntu's "Remote Desktop" will allow a user to view your desktop while in use (or interact with it as need be), but it is dangerous to expose to the internet, so some further discussion is needed to determine if it is safe for this situation.
you can configure it in System -> Preferences -> Remote Desktop

for your volume icons, this link shoudl help:
[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

can't help with the widgets. I don't believe they exist. in fact that is the point of the term.

"company A sells 39 gross of widgets..." 
"write a program that tallies widgets sold..."

---

### Post by prem1er on 2009-10-13
> **lastoneleft07 said:**
> 1. How can I show my desktop to my friends? I want him to connect & be able to see everything i'm doing

Try tightVNC.

---

### Post by lastoneleft07 on 2009-10-13
How bout question 4? I edited that and added at last second sory

---

### Post by doas777 on 2009-10-13
> **lastoneleft07 said:**
> How bout question 4? I edited that and added at last second sory

if you open a terminal and navigate to the folder that holds your opera folder, what do you get from 
```
 ls -al
```?

you can take ownership of a folder with this command:
```
 sudo chown -R <newusername>:<newgroupname> <path to folder>
```
(replacing all the content in <>).

---

### Post by lastoneleft07 on 2009-10-13
> **doas777 said:**
> if you open a terminal and navigate to the folder that holds your opera folder, what do you get from 
```
 ls -al
```?

I have no idea how to naviagate using a terminal


> **doas777 said:**
> 
you can take ownership of a folder with this command:
```
 sudo chown -R <newusername>:<newgroupname> <path to folder>
```
(replacing all the content in <>).

Where am I supposed to put that command?

Why would I not be the owner of a program I installed as the administrator? Seems kind of stupid

---

### Post by doas777 on 2009-10-13
> **lastoneleft07 said:**
> I have no idea how to naviagate using a terminal




Where am I supposed to put that command?

Why would I not be the owner of a program I installed as the administrator? Seems kind of stupid


well, you put the command, in a terminal (Applications -> Accessories -> Terminal). I don;t know of any way to change the owner on an object via the GUI. you can change directories with the 'cd' command. so to nav to your folder, you would enter
'cd <path to folder>'

as for your ownership question, your answer is in your question. 
you and the admin are always differant users. when you do something "as admin" then you are not yourself, and files created "as admin" will be owned by root:root (root user: root group).

---

### Post by lastoneleft07 on 2009-10-13
> **doas777 said:**
> well, you put the command, in a terminal (Applications -> Accessories -> Terminal). I don;t know of any way to change the owner on an object via the GUI. you can change directories with the 'cd' command. so to nav to your folder, you would enter
'cd <path to folder>'

as for your ownership question, your answer is in your question. 
you and the admin are always differant users. when you do something "as admin" then you are not yourself, and files created "as admin" will be owned by root:root (root user: root group).

Unfortunatly that makes absolutly no sence, when I log into Ubuntu, I logged in with the same login name and same password that I use when it asks me to verify my administrator status when doign admin crap, so I am the administrator any time Im logged in

---

### Post by doas777 on 2009-10-13
> **lastoneleft07 said:**
> Unfortunatly that makes absolutly no sence, when I log into Ubuntu, I logged in with the same login name and same password that I use when it asks me to verify my administrator status when doign admin crap, so I am the administrator any time Im logged in


nope. just like in vista/win7, you are never an admin. when you elevate your access, you impersonate the admin, but she is not thee.

---

### Post by lastoneleft07 on 2009-10-13
> **doas777 said:**
> nope. just like in vista/win7, you are never an admin. when you elevate your access, you impersonate the admin, but she is not thee.

except in windows Ive never been told by the system I can't copy and paste a simple file into a folder

---

### Post by doas777 on 2009-10-13
look at the chown command above. it is the answer to your issue.

---

### Post by lastoneleft07 on 2009-10-13
> **doas777 said:**
> if you open a terminal and navigate to the folder that holds your opera folder, what do you get from 
```
 ls -al
```?

```

total 14760
drwxr-xr-x   3 root root     4096 2009-10-13 04:41 .
drwxr-xr-x 173 root root    61440 2009-10-13 05:42 ..
-rw-r--r--   1 root root     4824 2009-08-30 12:35 missingsyms.so
-rwxr-xr-x   1 root root 14667864 2009-08-30 12:35 opera
-rwxr-xr-x   1 root root     9104 2009-08-30 12:35 operaplugincleaner
-rwxr-xr-x   1 root root     2963 2009-08-30 12:35 operapluginwrapper
-rwxr-xr-x   1 root root   110996 2009-08-30 12:35 operapluginwrapper-ia32-linux
-rwxr-xr-x   1 root root   163056 2009-08-30 12:35 operapluginwrapper-native
drwxr-xr-x   2 root root     4096 2009-08-30 12:35 plugins
-rw-r--r--   1 root root    25136 2009-08-30 12:35 spellcheck.so
-rwxr-xr-x   1 root root     4144 2009-08-30 12:35 works
jared@ubuntu:/usr/lib/opera$ 


```

> **doas777 said:**
> 
you can take ownership of a folder with this command:
```
 sudo chown -R <newusername>:<newgroupname> <path to folder>
```
(replacing all the content in <>).

So is newusername supposed to be the name i log in with? What is suppsoed to be in the gruop part I dont think I have any gruops

---

### Post by doas777 on 2009-10-13
the ls -l shows that your files are owned by root, and that while others can read the files, no one except root can write them. 

ok, so lets assume that my username is 'franklin' and the dir i want to change is located at \home\franklin\test\test1

my chown command would be:
```
sudo chown -R franklin:franklin /home/franklin/test/test1
```

the '-R' means to "recursively" repeat the command on all files and folders within test1.
'sudo' means you want to run the whole command as admin
franklin:franklin is the username that I want to own it. you can also use franklin:root, since your user is admin capable.

---

### Post by lastoneleft07 on 2009-10-13
```


jared@ubuntu:/usr/lib/opera$ sudo chown -R jared:jared
chown: missing operand after `jared:jared'
Try `chown --help' for more information.



```

---

### Post by jeremyswalker on 2009-10-13
You forgot to include the pathname of the file or folder you are changing the ownership of.

Should be like the following:
```
sudo chown -R jared:jared **/path/to/the/file/name**

```

For example, if it was a file named "thisfile.run" and it was on your Desktop, you would issue the following:
```
sudo chown -R jared:jared **/home/jared/Desktop/thisfile.run**
```

---

### Post by lastoneleft07 on 2009-10-13
```


jared@ubuntu:~$ sudo chown -R jared:jared usr/lib/opera 
[sudo] password for jared: 
chown: cannot access `usr/lib/opera': No such file or directory



```

---

### Post by jeremyswalker on 2009-10-13
> **lastoneleft07 said:**
> ```


jared@ubuntu:~$ sudo chown -R jared:jared **usr/lib/opera** 
[sudo] password for jared: 
chown: cannot access `usr/lib/opera': No such file or directory



```

You are missing the leading slash on your filepath. It should be:
```
sudo chown -R jared:jared **/**usr/lib/opera
```

Although, there should be absolutely no reason to be changing the ownership of such a directory to a normal user. It is highly *un*recommended.

---

### Post by lastoneleft07 on 2009-10-13
> **jeremyswalker said:**
> You are missing the leading slash on your filepath. It should be:
```
sudo chown -R jared:jared **/**usr/lib/opera
```

Although, there should be absolutely no reason to be changing the ownership of such a directory to a normal user. It is highly *un*recommended.

Really , Highly unrecommended to manauly install a plugin ? Lol thats the dumbest thing I've heard all day. 

If you have a better way to isntall the expiramental 64 bit linux Adobe Flash Plugin for Opera then by all means speak up

---

### Post by lastoneleft07 on 2009-10-13
Ok I have succesfuly installed the plugin after taking ownership of that folder, it runs ok on Opera now, thank you every one that helped


One last question about the Desktop viewer, does any one know if there is a specific guide I can follow to conenct my friend to me? Does he need a special program? Can he be on Windows or does he need Ubuntu installed?

---

### Post by KlinerDraken on 2009-10-13
i would just run nautilus as root to move the file manually if you don't want to use the terminal.

press Alt+F2 and then run "gksu nautilus" enter your password and then you should be able to move any file to any folder you need to.

---

### Post by lastoneleft07 on 2009-10-13
Thanks for the tip :)

How bout this part?

One last question about the Desktop viewer, does any one know if there is a specific guide I can follow to conenct my friend to me? Does he need a special program? Can he be on Windows or does he need Ubuntu installed?

---

### Post by jeremyswalker on 2009-10-13
> **lastoneleft07 said:**
> Really , Highly unrecommended to manauly install a plugin ?
I didn't say it was highly unrecommended to install a plugin manually. I said it was highly unrecommended to change the ownership of a root filesystem directory (such as /usr/lib/whatever) to that of a normal user. 

> **lastoneleft07 said:**
> Lol thats the dumbest thing I've heard all day.
LOL! The process you are going through to install a simple plugin is about the dumbest thing I've heard all day. (I'm sure many others would agree) You obviously sound like a fairly new user to the *nix world. It is not good mannerism to call someone dumb that is trying to help you. (I certainly don't mean to call you dumb, but that's what you are saying about me)

> **lastoneleft07 said:**
> If you have a better way to isntall the expiramental 64 bit linux Adobe Flash Plugin for Opera then by all means speak up
Did you try to copy it as root, or using sudo? Or into the plugin directory in your home folder? I've only installed the experimental flash for Firefox, but I *guarantee* that changing the ownership of that directory is not the most recommended way of doing things.


Not to come off as temperamental, but I don't appreciate your "...dumbest thing I've heard all day" comment. Especially when I guarantee I've been around the *nix block a lot longer than you, and I was just trying to help you out.

---

### Post by jeremyswalker on 2009-10-13
> **lastoneleft07 said:**
> One last question about the Desktop viewer, does any one know if there is a specific guide I can follow to conenct my friend to me? Does he need a special program? Can he be on Windows or does he need Ubuntu installed?

I haven't had to much experience in this area. However, a quick Google search came up with this link --> [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html"). It includes an area about connecting from a Windows system.

---

### Post by doas777 on 2009-10-13
as suggested on page 1, tightvnc is a vnc client for windows (and linux) and can connect to ubuntus remote desktop.  remember though, remote desktop is not safe to expose to the internet.

---

### Post by lastoneleft07 on 2009-10-13
Why does it tell me in the Remote Desktop box that users can only connect thru a local network?

---

### Post by doas777 on 2009-10-13
> **lastoneleft07 said:**
> Why does it tell me in the Remote Desktop box that users can only connect thru a local network?
because vnc (ubuntus remote desktop) is not safe to expose to the outside world, unless you tunnel it with an app like ssh. here is a howto.
[http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/](http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/)

---

### Post by lastoneleft07 on 2009-10-14
OK I managed to coonect to my own desktop and it seemed to work ok. Now I jsut need to configure it so my friends can connect, that link you posted , the tutorial he had was for soemthign called vnc, I'm not sure what it is or where to find it.

---

### Post by doas777 on 2009-10-14
> **lastoneleft07 said:**
> OK I managed to coonect to my own desktop and it seemed to work ok. Now I jsut need to configure it so my friends can connect, that link you posted , the tutorial he had was for soemthign called vnc, I'm not sure what it is or where to find it.

vnc is the ubuntu remote desktop server (specifically vino). tightVNC is a client you can use to connect to it. on ubuntu you can use vncviewer or vinagre which should be installed by default. on windows just download tight or realVNC

---

### Post by lastoneleft07 on 2009-10-14
ok but the tutorial you posted says 

```


If you look at the man page for vncviewer (man (1) vncviwer) you&#8217;ll notice there is a small section for -via.  The -via option, as outlined in the man page will do:

Makes the connection go through SSH to a gateway host.  The gateway should be the target host for best connection secrecy.

Basically this is saying that you can tunnel VNC over SSH within your connection command.  Let&#8217;s give it a try.

vncviewer -via user@host localhost:0


```

There is no where in the Remote Desktop Preferences to add that line there

---

### Post by doas777 on 2009-10-14
> **lastoneleft07 said:**
> ok but the tutorial you posted says 

```


If you look at the man page for vncviewer (man (1) vncviwer) you’ll notice there is a small section for -via.  The -via option, as outlined in the man page will do:

Makes the connection go through SSH to a gateway host.  The gateway should be the target host for best connection secrecy.

Basically this is saying that you can tunnel VNC over SSH within your connection command.  Let’s give it a try.

vncviewer -via user@host localhost:0


```There is no where in the Remote Desktop Preferences to add that line there

you don't set it on the server, you invoke it on the client.

for instance on linux, if you wanted to connect to the server you would just run:
```
vncviewer -via user@server:port localhost:0
```

on a windows machine, you will have to use putty to tunnel the ssh. I believe instructions are provided in the tutorial.

---

### Post by lastoneleft07 on 2009-10-14
How am i supposed to set it on a client when the Desktop Prefrenes tells me that no one can conenct unless there on my Local network?

---

### Post by doas777 on 2009-10-14
> **lastoneleft07 said:**
> How am i supposed to set it on a client when the Desktop Prefrenes tells me that no one can conenct unless there on my Local network?

ssh is a tunneling protocol. when you establish an ssh connection to another host on another network, you appear as part of that network. so in this case, your friend would ssh into your network, and then access your VNC service as though they were already on the network.

---

