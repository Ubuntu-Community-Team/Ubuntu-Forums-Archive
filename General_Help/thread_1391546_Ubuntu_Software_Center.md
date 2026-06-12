---
title: "Ubuntu Software Center"
date: 2010-01-26
forum: General Help
---

### Post by bevboy0223 on 2010-01-26
I'm running ubuntu 9.10. Have used the software centre to download many programs..However, I noticed last night that I can no longer download anything. It just sits there.   It says "waiting for other software managers to finish".   Pardon?

I do have a dropbox account.  Could that be the problem?

Thanks for your help.  

Bev

---

### Post by ladasky on 2010-01-27
> **bevboy0223 said:**
> I'm running ubuntu 9.10. Have used the software centre to download many programs..However, I noticed last night that I can no longer download anything. It just sits there.   It says "waiting for other software managers to finish".   Pardon?

I do have a dropbox account.  Could that be the problem?

Thanks for your help.  

Bev

I've noticed that you can't have Synaptic Package Manager running at the same time as Ubuntu Software Center.  This makes sense, you also couldn't have two instances of Synaptic running at the same time.
 
Bottom line, it looks like Ubuntu puts a global lock on programs which request the privilege of INSTALLING software applications.
 
Would Dropbox do this?  Somehow I doubt it.  That makes me think that another application is installing.  Maybe your automatic update?

---

### Post by raktarok on 2010-01-27
Does the problem persist even after a reboot?

---

### Post by zjagannatha on 2010-01-27
You might try killing all other applications that might be using /var/dpkg/lock
Try this in a command line:
ps -A | grep apt
That should display any program using aptitude.
From there you can kill it with:
sudo killall <name_of_app>
name_of_app should be something like:
apt-get
apt
aptitude

See if that works.

---

### Post by rnerwein on 2010-01-27
hi 
i think it's not a good idea to kill a running apt-get applikation (most people only knows the kill -9 - and that is sending a imediate kill of death - no change for that applikation to finish safe ). if you realy want to kill a process first try: kill -15 (sig TERM). if the applikation is well programed it will flush buffers, colose files, remove locks and ... ).
ciao

---

### Post by bevboy0223 on 2010-01-27
Yes. The problem persists after a reboot.  I first noticed it on Tuesday, but that was the first time I had used the software center in a few weeks.  

Any more thoughts?

Bev

---

### Post by bevboy0223 on 2010-01-27
Ran ps -A | grep apt as suggested in a terminal.  Nothing came back.  

The plot thickens. 

Bev

---

### Post by raktarok on 2010-01-27
Can you use apt-get or aptitude to download packages? It may not work too, but there's no harm in trying:

sudo apt-get update
sudo apt-get install <some_program>

Post any errors that you see.

---

### Post by bevboy0223 on 2010-01-27
I would do that, but can someone give me an example of something  to apt-get?  I don't know much about what is out there. That's why I was so happy to have the ubuntu software centre. Saved me so much hassle, at least until it stopped working for me.

Is everyone else finding the software centre works properly?

Bev

---

### Post by raktarok on 2010-01-27
Just try this:

```
sudo apt-get install nautilus-open-terminal
``` 

nautilus-open-terminal adds the option of opening terminal in the right click menu, when you are in nautilus.

Also check the folder /var/lock/ from the nautilus or post the output of this:
```

ls /var/lock/
```

Don't worry, we will get the software center working. :)

---

### Post by raktarok on 2010-01-27
And using apt-get is not too much of a hassle actually. Most programs can be installed by just using the program name (eg: apt-get install firefox), and then apt-cache can be used to search for a package. (doing  **apt-cache search firefox | grep extension** or just **apt-cache search "firefox extension"** gives you a nice list of firefox extensions available). Then there's synaptic too. 

I understand that installing programs through software center can be much easier, but once you get to know some commandline, apt-get isn't much of a hassle. Then again, that's true with everything - once you get to know...

---

### Post by bevboy0223 on 2010-01-27
ls /var/lock/  

No output  


-----------------------

Theapt-get nautilus command told me that i HAD TO RUN "sudo dpkg configure -a"

Pardon?  

I hope we can get this working.  V. frustrating.


Thanks for your help.

---

### Post by raktarok on 2010-01-27
Do this, as suggested:

```
sudo dpkg configure -a
```

Post error output, if any.

---

### Post by bevboy0223 on 2010-01-29
Sorry for the delay. Life got in the way.

--------

Here's the output for the command.

---------------

bev@bev-laptop:~$ sudo dpkg configure -a
[sudo] password for bev: 
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
bev@bev-laptop:~$ 


--------------
Is this helpful atall?

---

### Post by raktarok on 2010-01-29
Sorry, my mistake. I meant this:
```

sudo dpkg --configure -a
```

---

### Post by bevboy0223 on 2010-01-29
bev@bev-laptop:~$ sudo dpkg --configure -a
[sudo] password for bev: 
Setting up man-db (2.5.6-2) ...
Updating database of manual pages ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
bev@bev-laptop:~$ 

Is this helpful?

---

### Post by bevboy0223 on 2010-01-29
Hey, the software centre seems tto work now.  Just downloaded something

Will report back shortly.

---

### Post by raktarok on 2010-01-29
Looks like everything's good now. Try installing something with apt-get.
```

sudo apt-get update
sudo apt-get install nautilus-open-terminal
```

---

### Post by bevboy0223 on 2010-01-29
The software centre works now.

What does that command do, anyway?

Thanks so much!


Bev

---

### Post by raktarok on 2010-01-29
Glad to hear that,

the man page for dpkg describes the command as this:

```
 --configure package...|-a|--pending
              Reconfigure  an  unpacked  package.  If -a or --pending is given instead of package, all unpacked but unconfigured  packages  are configured.

Configuring consists of the following steps:

1.  Unpack  the  conffiles, and at the same time back up the old
conffiles, so that they can be restored if something goes wrong.

2. Run postinst script, if provided by the package.

```

What could have happened is that while using the software center, the installation process was killed in some way(maybe you did it manually or maybe you powered off the computer without allowing the process to finish) So some packages that were downloaded remained 'unconfigured', leading the software center to complain the next time you used it.

If you find yourself questioning the function of commands, use man. Here, you could have done this:

```
man dpkg
```

and then scroll down to the relevant section, or search for what you want by pressing "/" key and typing your query.

Feel free to post if you have any other problems in the future!

---

### Post by bevboy0223 on 2010-01-29
Thanks so much for your help. Unix is an interesting operating system to say the least.  

I will continue to post here as necessary.  Don't worry.

Thanks again!

Bev

---

