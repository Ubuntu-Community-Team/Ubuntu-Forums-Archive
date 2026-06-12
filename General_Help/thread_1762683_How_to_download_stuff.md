---
title: "How to download stuff??"
date: 2011-05-19
forum: General Help
---

### Post by lakshmen on 2011-05-19
I need to download stuff like software sources but i cant seem to be able to do it.I cant even update the new installs using update center

---

### Post by lmn. on 2011-05-19
is there an error message?

---

### Post by lakshmen on 2011-05-19
the error is 

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 1 in source list /etc/apt/sources.list.d/ros-latest.list (dist parse)'

---

### Post by lmn. on 2011-05-19
[http://ubuntuforums.org/showthread.php?t=1211959](http://ubuntuforums.org/showthread.php?t=1211959)

try that ;)

---

### Post by lakshmen on 2011-05-19
am i suppose to type 

sudo chmod 644 /etc/apt/sources.list.d/ros-latest.list

??

---

### Post by StrayEddy on 2011-05-19
yep

---

### Post by lakshmen on 2011-05-19
it says

missing operand after '644 /etc/apt/sources.list.d/ros-latest.list' try 'chmod--help' for more information

---

### Post by lakshmen on 2011-05-19
sorry guys i am very nuke to ubuntu.. i need to for ROS. i need to download ROS diamondback software...

---

### Post by StrayEddy on 2011-05-19
Did you type it with the spaces:
 
"sudo chmod 644 /etc/apt/sources.list.d/ros-latest.list"
 
Cause i think your error is due to too much or not enought spaces between your arguments.
 
sudo(space)chmod(space)644(space)/etc/apt/sources.list.d/ros-latest.list

---

### Post by lakshmen on 2011-05-19
sorry i forgot a space, this time it worked but when i went back into update manager same problem

---

### Post by mhgsys on 2011-05-19
'E:Malformed line 1 in source list /etc/apt/sources.list.d/ros-latest.list (dist parse)'

**please post /etc/apt/sources.list.d/ros-latest.list**

```
gedit /etc/apt/sources.list.d/ros-latest.list
```

it seems there is an error on line 1

---

### Post by lakshmen on 2011-05-19
a text editor with this 

deb [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) maverickmain

came up....

---

### Post by StrayEddy on 2011-05-19
Do you use maverick right now?
 
Did you use this tutorial?
 
[http://www.ros.org/wiki/diamondback/Installation/Ubuntu](http://www.ros.org/wiki/diamondback/Installation/Ubuntu)

---

### Post by lakshmen on 2011-05-19
thats exactly right....

---

### Post by mhgsys on 2011-05-19
the link itself is valid...but you miss a space

open up the file again with 
```
gksudo gedit /etc/apt/sources.list.d/ros-latest.list
```
(it will ask for your password since you need to be root to edit this file)

And _put a space between_ maverick and main 
so ```
deb http://packages.ros.org/ros/ubuntu maverickmain
```
becomes
```
deb http://packages.ros.org/ros/ubuntu maverick main
```

**save the file**

after that run 
```
sudo apt-get update
```

---

### Post by lakshmen on 2011-05-19
thanks a lot.... now i can continue with the rest of installation like the desktop full rite??

---

### Post by mhgsys on 2011-05-19
your apt problem is solved

so you can continu installing it

---

### Post by lakshmen on 2011-05-19
thanks....

---

### Post by mhgsys on 2011-05-19
your welcome

---

### Post by lakshmen on 2011-05-19
another problem... sorry... it was updating properly... before it stopped and now it says failed to download package files... check my connection...

---

### Post by mhgsys on 2011-05-19
check your connection?

and please close all synaptic , software centre , update-manager bla etc
and instaid open a terminal and do a 
```
sudo apt-get update
```

post error(s) back here

---

### Post by lakshmen on 2011-05-19
it says reading package lists... done....and there were the whole list of commands above it...

---

### Post by mhgsys on 2011-05-19
I'm not sure I'm understanding your question ...

Are you having problems now to install the ros-desktop files only?
because apt seems to be fine, and connection seems to be fine with apt-update right?

```
sudo apt-get install ros-diamondback-desktop-full
```

Gives me a whole list of packages it wants to install for ros
> 0 upgraded, 284 newly installed, 0 to remove and 5 not upgraded.
Need to get 860 MB/861 MB of archives.
After this operation, 2,206 MB of additional disk space will be used.


---

### Post by lakshmen on 2011-05-24
hi guys, its me again... I am not able to download files such opencv, meshlab... what is the steps to follow??

---

### Post by lakshmen on 2011-05-24
Guys any idea?? really need your help....

---

### Post by oldos2er on 2011-05-24
Can you run the following command in a terminal, and copy and paste all the output here? ```
sudo apt-get update && sudo apt-get install meshlab
```

---

### Post by lakshmen on 2011-05-24
sudo apt-get update 

Output : 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg         
Hit [http://packages.ros.org](http://packages.ros.org) maverick Release.gpg                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://packages.ros.org/ros/ubuntu/](http://packages.ros.org/ros/ubuntu/) maverick/main Translation-en           
Ign [http://packages.ros.org/ros/ubuntu/](http://packages.ros.org/ros/ubuntu/) maverick/main Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en    
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Hit [http://packages.ros.org](http://packages.ros.org) maverick Release                         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://packages.ros.org](http://packages.ros.org) maverick/main i386 Packages                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Ign [http://packages.ros.org](http://packages.ros.org) maverick/main i386 Packages              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release            
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://packages.ros.org](http://packages.ros.org) maverick/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Reading package lists... Done

---

### Post by lakshmen on 2011-05-24
sudo apt-get install meshlab

output:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib3ds-1-3 libmuparser0
The following NEW packages will be installed:
  lib3ds-1-3 libmuparser0 meshlab
0 upgraded, 3 newly installed, 0 to remove and 279 not upgraded.
Need to get 6,614kB of archives.
After this operation, 17.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe lib3ds-1-3 i386 1.3.0-4 [52.6kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe libmuparser0 i386 1.32-1 [134kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe meshlab i386 1.2.2-2 [6,428kB]
Fetched 6,614kB in 21s (313kB/s)                                               
Selecting previously deselected package lib3ds-1-3.
(Reading database ... 204117 files and directories currently installed.)
Unpacking lib3ds-1-3 (from .../lib3ds-1-3_1.3.0-4_i386.deb) ...
Selecting previously deselected package libmuparser0.
Unpacking libmuparser0 (from .../libmuparser0_1.32-1_i386.deb) ...
Selecting previously deselected package meshlab.
Unpacking meshlab (from .../meshlab_1.2.2-2_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up lib3ds-1-3 (1.3.0-4) ...
Setting up libmuparser0 (1.32-1) ...
Setting up meshlab (1.2.2-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Reading package lists... Done
Reading: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Building dependency tree       
Building: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Reading state information... Done
Reading: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ The following extra packages will be installed:
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$   lib3ds-1-3 libmuparser0
lib3ds-1-3: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ The following NEW packages will be installed:
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$   lib3ds-1-3 libmuparser0 meshlab
lib3ds-1-3: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ 0 upgraded, 3 newly installed, 0 to remove and 279 not upgraded.
0: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Need to get 6,614kB of archives.No command 'Need' found, did you mean:
 Command 'seed' from package 'seed' (universe)
Need: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ After this operation, 17.9MB of additional disk space will be used.
After: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Do you want to continue [Y/n]? yDo: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe lib3ds-1-3 i386 1.3.0-4 [52.6kB]
Get:1: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe libmuparser0 i386 1.32-1 [134kB]
Get:2: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe meshlab i386 1.2.2-2 [6,428kB]
Get:3: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Fetched 6,614kB in 21s (313kB/s)                                               
bash: syntax error near unexpected token `('
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Selecting previously deselected package lib3ds-1-3.
Selecting: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ (Reading database ... 204117 files and directories currently installed.)
Reading: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Unpacking lib3ds-1-3 (from .../lib3ds-1-3_1.3.0-4_i386.deb) ...
bash: syntax error near unexpected token `('
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Selecting previously deselected package libmuparser0.
Selecting: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Unpacking libmuparser0 (from .../libmuparser0_1.32-1_i386.deb) ...
bash: syntax error near unexpected token `('
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Selecting previously deselected package meshlab.
Selecting: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Unpacking meshlab (from .../meshlab_1.2.2-2_i386.deb) ...
bash: syntax error near unexpected token `('
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Processing triggers for bamfdaemon ...
Processing: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Rebuilding /usr/share/applications/bamf.index...
Rebuilding: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Processing triggers for desktop-file-utils ...
Processing: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Processing triggers for python-gmenu ...
Processing: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Rebuilding: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Processing triggers for man-db ...
Processing: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Processing triggers for python-support ...
Processing: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Setting up lib3ds-1-3 (1.3.0-4) ...
bash: syntax error near unexpected token `('
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Setting up libmuparser0 (1.32-1) ...
bash: syntax error near unexpected token `('
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Setting up meshlab (1.2.2-2) ...bash: syntax error near unexpected token `('
user@ubuntu:~/ros_tutorials/beginner_tutorials$ Processing triggers for libc-bin ...
Processing: command not found
user@ubuntu:~/ros_tutorials/beginner_tutorials$ ldconfig deferred processing now taking place
/sbin/ldconfig.real: relative path `deferred' used to build cache

---

### Post by oldos2er on 2011-05-25
What exactly is going on there? It looks like you've pasted output from "sudo apt-get install meshlab" back into the terminal.

---

### Post by lakshmen on 2011-05-25
yes because the person asked to do so and in the previous comment...

---

### Post by oldos2er on 2011-05-26
So can we assume everything is working ok now?

---

