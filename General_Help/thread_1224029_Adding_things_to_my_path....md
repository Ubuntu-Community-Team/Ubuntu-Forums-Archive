---
title: "Adding things to my path..."
date: 2009-07-26
forum: General Help
---

### Post by Bradj47 on 2009-07-26
I'm trying to put /root/bin in my path. On Solaris I always just edited my .cshrc file but in Ubuntu there is no .cshrc file. How do I put things in my path?

---

### Post by synapsys on 2009-07-26
.bashrc

---

### Post by Bradj47 on 2009-07-26
Ah thanks. Now for my next problem. When I used Solaris there were a list of file paths already there that I just added on to. That's how I knew where to put the new path I wanted to add. Here there are no list of paths. Is there some command or something I have to add to the file or can I just add the path to the end? I have no idea what this code is or how it works.

---

### Post by jm2 on 2009-07-26
at the $ prompt, type echo $PATH (press return)
this will show you your current PATH.

to add to the path

edit your .bashrc file

add the line near the bottom 
PATH=$PATH:<your new path>
export PATH

logout and back in and see if it works now.

---

### Post by Bradj47 on 2009-07-27
It didn't work. Maybe you can help if I provide more information. I'm trying to set up this ventrilo script I downloaded a while ago. Here's the README file: 

```

Ventrilo Script v2.1.0_02 written by Crypt Keeper
For ventrilo server v2.x

How to use these scripts:

1. Edit the ventrilo script and change VENPATH,
VENSRV, and VENUSER to match your setup (it is
currently setup for linux and the install path
and user account specified in the ventrilo_srv.htm)

2. Copy the ventrilo script to /root/bin
If you decide to put the ventrilo script somewhere
else there are two things to note: 1. Placing
the ventrilo script in the path makes life easier
and 2. You will need to change the VENSCRIPT
variable in S99ventrilo to the path where you
installed the ventrilo script if you use it to
start at ventrilo at boot/runlevel

3. Edit S99ventrilo to start or stop the servers
that you want and then copy it to the runlevel you
would like those actions to occur on (ie /etc/rc.d/rc3.d/
for startup at boot)

4. If you copied S99ventrilo to the rc3.d directory you 
can safely remove the ventrilo startup commands from your
rc.local

5. As long as root bin is in you path you can now type
ventrilo -h to get the usage of ventrilo script

Have Fun
  Crypt Keeper

```

Reading it more carefully I think I may have found the problem. It has nothing to do with the path now (so I'm changing the title). At number 4 it says "If you copied S99ventrilo to the rc3.d directory". Where is the rc3.d directory? Is that a normal system directory?

---

### Post by ibutho on 2009-07-27
To add things to your path if you are using Ubuntu, then you can do this in /etc/environment to make the changes global and ~/.bash_profile for an individual user e.g.
```
export PATH=$PATH:/new/path/bin
```

---

### Post by RetchingRabbit on 2009-07-27
AFAIK, there is no /root/bin directory in a LSB compliant distro.

---

### Post by Bradj47 on 2009-07-27
> **RetchingRabbit said:**
> AFAIK, there is no /root/bin directory in a LSB compliant distro.

There is. That's where I first copied the ventrilo script.

---

### Post by lukeiamyourfather on 2009-07-27
Why would you want to run an application from the root users home directory? Better place to put it would be /opt/whatever, or frankly anywhere besides the root users home directory would be better. Aside from setting the path to look in the root users home directory you'd have to change file permissions to be able to run it from there anyway or run it as root. Either way its messy and potentially unsafe to use the root account in this manner. Cheers!

---

### Post by Bradj47 on 2009-07-27
> **ibutho said:**
> To add things to your path if you are using Ubuntu, then you can do this in /etc/environment to make the changes global and ~/.bash_profile for an individual user e.g.
```
export PATH=$PATH:/new/path/bin
```

There is no .bash_profile file in my home directory so I just edited the /etc/environment file as so: 
```

brad@rockstar:~$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/root/bin"

```
I added the path to the end separating it from the others with a colon because that's how all the others did it. But the 'ventrilo' command still won't work. 
```

brad@rockstar:~$ ventrilo
bash: ventrilo: command not found

```
I think it's because of the rc3.d thing I mentioned. This thread really isn't about changing the path anymore. Sorry I can't figure out how to change the title when viewed from the list of threads on the 'General Help' board.

---

### Post by Bradj47 on 2009-07-27
> **lukeiamyourfather said:**
> Why would you want to run an application from the root users home directory? Better place to put it would be /opt/whatever, or frankly anywhere besides the root users home directory would be better. Aside from setting the path to look in the root users home directory you'd have to change file permissions to be able to run it from there anyway or run it as root. Either way its messy and potentially unsafe to use the root account in this manner. Cheers!

Ah ok I hadn't thought of that. The only reason I put it in the /root/bin directory is because the README that I previously mentioned had told me to put it there. I'll check what's in my path and put it under something else. Thanks!

---

### Post by ibutho on 2009-07-27
> 
There is no .bash_profile file in my home directory so I just edited the /etc/environment...
You can create the ~/.bash_profile yourself if its not already present. When you changed your PATH in /etc/environment, did you log out and back in again?

---

### Post by Bradj47 on 2009-07-27
> **ibutho said:**
> You can create the ~/.bash_profile yourself if its not already present. When you changed your PATH in /etc/environment, did you log out and back in again?

Yes I did. I'll create the ~/.bash_profile then try again.

---

### Post by Bradj47 on 2009-07-27
Still no luck: 
```

brad@rockstar:~$ ventrilo -h
bash: ventrilo: command not found

```
But I think the path is set right. I'm wondering about the rc3.d thing mentioned in step 3 and 4 of the README. 
```

brad@rockstar:~$ cd /etc/rc.d/rc3.d
bash: cd: /etc/rc.d/rc3.d: No such file or directory
brad@rockstar:~$ cd /etc/rc.d
bash: cd: /etc/rc.d: No such file or directory

```
Since /etc/rc.d doesn't exist can I make it and have it still work?

---

### Post by Bradj47 on 2009-07-27
After creating /etc/rc.d/rc3.d and moving the S99ventrilo file there, the 'ventrilo -h' command still doesn't work. 
```

brad@rockstar:~/Desktop/ventrilo$ cd /etc
brad@rockstar:/etc$ sudo mkdir rc.d
[sudo] password for brad: 
brad@rockstar:/etc$ cd rc.d
brad@rockstar:/etc/rc.d$ sudo mkdir rc3.d
brad@rockstar:/etc/rc.d/rc3.d$ cd ~/Desktop/ventrilo
brad@rockstar:~/Desktop/ventrilo$ ls
README  S99ventrilo  ventrilo  VERSION
brad@rockstar:~/Desktop/ventrilo$ sudo cp S99ventrilo /etc/rc.d/rc3.d
brad@rockstar:~/Desktop/ventrilo$ cd
brad@rockstar:~$ ventrilo -h
bash: ventrilo: command not found

```

Any suggestions?

---

### Post by nmobrien4 on 2009-07-29
I'm having a similar problem. I'm pretty new at writing scripts and I don't seem to have a .bash_profile

I'm trying to set the path to ~/bin

Sorry if any part of that was dumb. 

edit** nevermind I figured it out.

---

