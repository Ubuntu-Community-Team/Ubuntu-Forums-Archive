---
title: "problem with file permission help! help ! help  !"
date: 2010-03-05
forum: General Help
---

### Post by rahulxx on 2010-03-05
:p i have just created a ubuntu server.  its too easy to setup but very very hard to maintain and run

:confused:please help me:
i installed joomla in my domain, every thing is right but whenever i try to install or try to change config from joomla admin then its sows error :  unable to move file or error changing files.

i gussed the problem and i run this command by terminal [HTML]gksu nautilus[/HTML] , then every thing goes right, no problem,

after restarting my pc i have to again run those command to work,
but today morning it is not working i tried many times, and also a new problem                                                               
> **Warning**:  mkdir() [[function.mkdir]]("http://ubuntuforums.org/#"): Permission denied in tell me how do change the permission for ever (i need sequrity also cause my server is hosting many sites)](*,)

> my configuration is:
PC: dual core- 2.8 gHz, ram-2 gb, 
OS: UBUNTU 8
Hosting control panel: EHCP
 i am new to ubuntu and hosting so please dont use technical language, 
thanks for any help

---

### Post by grittyminder on 2010-03-05
> gksu nautilus

I don't think that you should be running the above command. If you want to run a command that requires elevated privileges just use the sudo command.

E.g. sudo mkdir directoryName

---

### Post by flippo on 2010-03-05
In Unix (and Linux) files have different permissions.  If you go to your home directory in a terminal and type "ls -l" you'll see a listing like this:```
drwxr-xr-x  3 flippo flippo    4096 Aug 19  2009 My Games
drwxr-xr-x  3 flippo flippo    4096 Jan 24 21:28 RealView Workspaces
-rw-r--r--  1 flippo flippo   18432 Feb  2 20:04 Resume.doc
-rw-r--r--  1 flippo flippo  132608 Jan 19 10:34 VirtMemSystem..ppt
-rw-r--r--  1 flippo flippo    2142 Feb  8 20:40 asdf
drwxr-xr-x  2 flippo flippo    4096 Jan 24 19:55 bin

```

the important parts are the first few letters on the left.
the rwx lines tell the permissions it the order goes:

user group other

and rwx stand for

read write execute

then there is the owner and group, as you can see all of my files are owned by flippo and the group is flippo.

These permissions say who can open, write, and execute each file.  You can change permissions and owners with "chown" and "chmod".

You can look up the man pages on how to run these yourself (man chown or man chmod in a terminal).

To allow all users to do everything to all files in a directory <dir> you can type:```
chmod 777 -R <dir>
```But you don't want to do this if your running a server, you need a more secure setup.  I'll let you figure out your own setup, but please post for help.

Does this answer (or partially answer) your question? or was I way off the mark?

---

### Post by rahulxx on 2010-03-05
> > gksu nautilus

I don't think that you should be running the above command. If you want to run a command that requires elevated privileges just use the sudo command.

E.g. sudo mkdir directoryName

friend i told you that i am not crating folder, its joomla script which need to permission to create folder, but how

whenever i run 

gksu nautilus

command then no problem appears, joomla works proprly, but today it is not working

---

### Post by rahulxx on 2010-03-05
> **flippo said:**
> In Unix (and Linux) files have different permissions.  If you go to your home directory in a terminal and type "ls -l" you'll see a listing like this:```
drwxr-xr-x  3 flippo flippo    4096 Aug 19  2009 My Games
drwxr-xr-x  3 flippo flippo    4096 Jan 24 21:28 RealView Workspaces
-rw-r--r--  1 flippo flippo   18432 Feb  2 20:04 Resume.doc
-rw-r--r--  1 flippo flippo  132608 Jan 19 10:34 VirtMemSystem..ppt
-rw-r--r--  1 flippo flippo    2142 Feb  8 20:40 asdf
drwxr-xr-x  2 flippo flippo    4096 Jan 24 19:55 bin

```the important parts are the first few letters on the left.
the rwx lines tell the permissions it the order goes:

user group other

and rwx stand for

read write execute

then there is the owner and group, as you can see all of my files are owned by flippo and the group is flippo.

These permissions say who can open, write, and execute each file.  You can change permissions and owners with "chown" and "chmod".

You can look up the man pages on how to run these yourself (man chown or man chmod in a terminal).

To allow all users to do everything to all files in a directory <dir> you can type:```
chmod 777 -R <dir>
```But you don't want to do this if your running a server, you need a more secure setup.  I'll let you figure out your own setup, but please post for help.

Does this answer (or partially answer) your question? or was I way off the mark?

i tried comod option too, but joomla is unable to install any file from my local pc,
i give permission to 777 to all my files but,

---

### Post by grittyminder on 2010-03-05
Assuming that apache is running under the www-data user you'll need to give www-data permissions to run the script. You'll also need to give www-data write permissions for the base directory under which you want to create the new directory. The easiest way to do that would be to make www-data the owner of the directory:

sudo chown www-data:www-data /path/to/directory

---

### Post by grittyminder on 2010-03-05
BTW, as the other poster stated, granting 777 permissions is not a very good idea.

---

### Post by rahulxx on 2010-03-05
friend i know but how to solve problem,

please tell me by running gksu nautilus coomand
whom i grant permission is it root or anyone else, 
currently permission is for gpftp 

one more help how i secure my server, i just updated my system except i didnot done anything

---

