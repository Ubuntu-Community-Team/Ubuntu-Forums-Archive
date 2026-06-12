---
title: "Trouble with &quot;mkdir&quot; permissions in root directory"
date: 2009-06-28
forum: General Help
---

### Post by steve_akh076 on 2009-06-28
**Dear Ubuntu community,**
 
**I am rewording a posting I initiated 20 hrs ago to a more tangible form. **
 
**I am having problems running a bash script named "testfile" that attempts to create and write to a new directory ("steve_test") in the root directory (/). I did this in order to reproduce a problem I am having running an executable (IPW 2.1) that attempts to do the same thing. Script "testfile" has root suid priveleges (I even tried "chmod 7777 testfile" to no success), and I have privileges to execute "testfile", so I don't understand what the problem is. The funny thing is, when I "sudo su" to root, it works just fine. Isn't setting suid root privileges to "testfile" supposed to do the same thing? Maybe I'm totally confused... The shell output is below. I would so much appreciate any help so that I can get my software running.**
 
**BTW: I am running Ubuntu 9.04 and Windows XP on dual boot. **
 
**--Steve **
 
**shell output: **
 
**steven@stevens-computer:~/test$ bash testfile**
 
**mkdir: cannot create directory `/steve_test': Permission denied**
**testfile: line 5: /steve_test/mytext.txt: No such file or directory**
 
**steven@stevens-computer:~/test$ **

---

### Post by vidgen13 on 2009-06-28
i'm not an expert but have you tried "sudo testfile" i think that will give your script root permissions

---

### Post by steve_akh076 on 2009-06-28
vidgen13,
 
Yes, I mentioned in my original post that I could execute the script after switching to root. But it doesn't seem like I should have to do this if I set the suid byte and the script is owned by root (?). Also, and more importantly, the software I am running executes a script that tries to do the same thing. The running process needs "mkdir" permissions in root, I don't know how to my "sudo ..." might carry through all of the running processes.
 
Steve

---

### Post by SuperSonic4 on 2009-06-28
Have you tried giving your user permission to run the script without a password in /etc/sudoers?

Try adding the following line to /etc/sudoers

```
user steven=NOPASSWD: /usr/bin/testfile
```

where /usr/bin/testfile is where the script is located

---

### Post by cariboo on 2009-06-28
You shouldn't be creating other directories in / as it may break the lsb [(Linux Standards Base)]("http://www.linuxfoundation.org/collaborate/workgroups/lsb"), The correct place for user created directories is /usr/local. If you make your script executable, and run it from /usr/local/bin and set it to create a directory in /usr/local, then use sudo to run it, you may have better luck.

---

### Post by steve_akh076 on 2009-06-28
SuperSonic4,
 
The permissions of /etc/sudoers was r--r-----. I added write permissions to sudoers and now sudo is all balled up. At this point I cannot use "sudo" at all. When I do, I get the message "sudo: /etc/sudoers is mode 0640, should be 0440". I get the same message when I try to set the permissions of sudoers back the way it was (0440). Do you know how to undo the permission change I made to the file? Thanks.
 
 
cariboo907,
 
I do not want to write to the root directory. I am trying to figure out how to get permissions to do so in order to see ways of possibly getting my software running. It is apparently trying to write temporary files to the root directory. Do you think doing this may de-stabilize (mess up, etc etc) my system? Also, I tried following SuperSonic4's suggestion and now I cannot use sudo. This was caused by me adding write privileges to /etc/sudoers in order to edit the file. Now I keep getting the message "/etc/sudoers is mode 0640, should be 0440" when I try use sudo or modify permissions of sudoers. In retrospect I should not have tried this. Thanks.

---

### Post by jocko on 2009-06-28
> **steve_akh076 said:**
> SuperSonic4,
 
The permissions of /etc/sudoers was r--r-----. I added write permissions to sudoers and now sudo is all balled up. At this point I cannot use "sudo" at all. When I do, I get the message "sudo: /etc/sudoers is mode 0640, should be 0440". I get the same message when I try to set the permissions of sudoers back the way it was (0440). Do you know how to undo the permission change I made to the file? Thanks.

Try to reboot into recovery mode and:
```
chmod 0440 /etc/sudoers
```then reboot.
And never ever change permissions on important system files to edit them. The permissions are set the way they need to be, and if you change them things will stop working.
To edit /etc/sudoers without messing it up:
```
sudo visudo
```

---

### Post by Augsburg on 2009-06-28
Another way to edit the sudoers file, in case you aren't used to vi is:

EDITOR=<nano/gedit> sudo visudo

Have you tried simply chmod +s ?

---

### Post by steve_akh076 on 2009-06-28
jocko and Augsburg,
 
Thank you so much for helping me reset my file permissions. Yeah, that was not the way to go... No, I have not tried "chmod +s". Do you mean "chmod +s sudoers"? I shan't try that in retrospect.
 
Steve

---

### Post by wojox on 2009-06-28
```
(I even tried "chmod 7777 testfile" to no success)
``` 

try

```
chmod 777
```

---

