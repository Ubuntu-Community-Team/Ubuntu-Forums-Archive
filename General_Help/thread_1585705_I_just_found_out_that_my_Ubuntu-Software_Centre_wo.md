---
title: "I just found out that my Ubuntu-Software Centre wont work anymore!"
date: 2010-09-30
forum: General Help
---

### Post by chrissy.millichamp on 2010-09-30
Ive got Ubuntu 10.10, and I just found out that my Ubuntu Software Centre wont work after running in the terminal, the command line: [COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] [COLOR=#660033]-y[/COLOR] autoremove mono-runtime. What can I do, in order to fix the problem?

---

### Post by chrissy.millichamp on 2010-09-30
Ive had only two error messages meanwhile starting it, saying deamond something will not permit and Ubuntu software will close unexpectedly? I cant really remember clearly because I couldnt copy and paste the error message because it doesnt come up anymore so....

---

### Post by directhex on 2010-10-01
Autoremove doesn't do what you think it does. You may well have accidentally removed completely unrelated things.

---

### Post by coffeecat on 2010-10-01
Use the -y flag with caution with any terminal command. You are basically giving it carte-blanche to go ahead without letting you checking first. If you had run 'sudo apt-get autoremove mono-runtime', it would have prompted you with what it was wanting to remove and asked you to confirm with a y/n. I tried that and I couldn't see that it was going to remove anything essential to software-center, but obviously something went wrong for you. (I did a 'no' to bail out - I want to keep mono.)

Try:

```
sudo apt-get install software-center
```That will hopefully reinstall any missing dependencies. If not, try 

```
sudo apt-get install --reinstall software-center
```And if that doesn't help, try:

```
sudo apt-get install ubuntu-desktop
```That last, of course, will reinstall anything related to the Ubuntu desktop including anything you might previously have uninstalled. If you really want to remove mono, I suggest you try searching the internet for a suitable howto. Googling 'ubuntu remove mono' brought up many hits for me and it seems you only need to remove a handful of packages. I can't vouch for their reliability as I've never felt the need to remove mono.

---

### Post by fleton on 2010-10-01
I had the same problem, tried opening through terminal and I noticed it was getting some permission errors just to open the program, the file name that was making the problem is "software-center.log".


I used this to fix the problem.

```
sudo chmod 667 /home/[SIZE="6"]**username**[/SIZE]/.cache/software-center/software-center.log
```

---

### Post by percyhahn on 2010-10-01
> **coffeecat said:**
> Use the -y flag with caution with any terminal command. You are basically giving it carte-blanche to go ahead without letting you checking first. If you had run 'sudo apt-get autoremove mono-runtime', it would have prompted you with what it was wanting to remove and asked you to confirm with a y/n. I tried that and I couldn't see that it was going to remove anything essential to software-center, but obviously something went wrong for you. (I did a 'no' to bail out - I want to keep mono.)

Try:

```
sudo apt-get install software-center
```That will hopefully reinstall any missing dependencies. If not, try 

```
sudo apt-get install --reinstall software-center
```And if that doesn't help, try:

```
sudo apt-get install ubuntu-desktop
```That last, of course, will reinstall anything related to the Ubuntu desktop including anything you might previously have uninstalled. If you really want to remove mono, I suggest you try searching the internet for a suitable howto. Googling 'ubuntu remove mono' brought up many hits for me and it seems you only need to remove a handful of packages. I can't vouch for their reliability as I've never felt the need to remove mono.

   my software center now wont run snice upgrading to 10.10.
   i tried your first 2 commands, and got this response from terminal
peter@peter-laptop:~$ sudo apt-get insta;; software-center
bash: syntax error near unexpected token `;;'
peter@peter-laptop:~$ sudo apt-get install --reinstall software center
[sudo] password for peter: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_maverick_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
peter@peter-laptop:~$

---

### Post by coffeecat on 2010-10-01
> **percyhahn said:**
> i tried your first 2 commands

No, you didn't. You made typing errors in both the commands. The terminal is utterly unforgiving with typos. Be very careful when using sudo in the terminal - you can hose your system with one careless error.


> **percyhahn said:**
> peter@peter-laptop:~$ sudo apt-get insta;; software-center
bash: syntax error near unexpected token `;;'

Always read the error message. In this case it is telling you what is wrong. It's 'install', not 'insta;;'.

> **percyhahn said:**
> peter@peter-laptop:~$ sudo apt-get install --reinstall software center

You missed out the hyphen in software-center. The system is complaining because it can't find the packages 'software' and 'center' which is what you told it to re-install and which don't exist.

Anyway, your underlying problem is different from the OP. Those commands won't do any harm (typed properly) but they might not do any good. If they don't then I suggest you start your own help thread.

---

### Post by chrissy.millichamp on 2010-10-01
Ive tried the commands that you have recommended me, and still didnt really fix the problem!

---

### Post by coffeecat on 2010-10-02
> **chrissy.millichamp said:**
> Ive tried the commands that you have recommended me, and still didnt really fix the problem!

Prior to posting before, I tried 'sudo apt-get autoremove mono-runtime' (obviously I did not OK it) and had a look at the other packages it wanted to remove. I couldn't see any that were dependencies of software-center, so I was surprised that autoremoving mono-runtime would have affected software-center. Besides, by reinstalling software-center you would have reinstalled any dependencies that may have been removed.

I have one other thing to suggest. Run:

```
sudo apt-get install mono-runtime
```That will reinstall both mono-runtime and the other packages that the autoremove command removed (I hope). Then see if software-center works. If it does, then you could find a safer way of removing mono if you really want to get rid of it.

If that doesn't fix software-center, then there must be some other problem unrelated to the removal of mono-runtime, and you need to do some more investigating. First, try to start up software-center from the terminal with:

```
/usr/bin/software-center
```.. and post any error messages you get. If you get none and software-center is still not working, try opening Synaptic from the System > Administration menu. Does that open? If not, invoke that from the terminal with:

```
gksu synaptic
```... and post any error messages.

When you say, "didn't really fix the problem", do you mean that it didn't fix it at all, or that it half-fixed it? What do you mean by "really"?

---

### Post by chrissy.millichamp on 2010-10-02
Here is the terminal log, and its error messages that Ive received: chrissy@chrissy-desktop:~$ sudo apt-get install mono-runtime
[sudo] password for chrissy: 
Sorry, try again.
[sudo] password for chrissy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mono-runtime is already the newest version.
mono-runtime set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
chrissy@chrissy-desktop:~$ /usr/bin/software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 38, in <module>
    import softwarecenter.log 
  File "/usr/share/software-center/softwarecenter/log.py", line 92, in <module>
    backupCount=5)
  File "/usr/lib/python2.6/logging/handlers.py", line 112, in __init__
    BaseRotatingHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/handlers.py", line 64, in __init__
    logging.FileHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/__init__.py", line 827, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.6/logging/__init__.py", line 846, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 13] Permission denied: '/home/chrissy/.cache/software-center/software-center.log. To answer the question, it didn't fix at all the problem.

---

### Post by directhex on 2010-10-02
You don't have write permissions to the software center log - presumably you ran it with sudo the first time.

Try:

chown chrissy /home/chrissy/.cache/software-center/software-center.log

---

### Post by coffeecat on 2010-10-03
> **directhex said:**
> You don't have write permissions to the software center log - presumably you ran it with sudo the first time.

Try:

chown chrissy /home/chrissy/.cache/software-center/software-center.log

Wouldn't the OP need to run chown with sudo because of the permissions issue?

@chrissy.millichamp, if you get an error running the chown command like that, try:

```
sudo chown chrissy: /home/chrissy/.cache/software-center/software-center.log
```Note that I've added a colon immediately after 'chrissy'. That ensures that you get the correct group ownership as well.

---

### Post by chrissy.millichamp on 2010-10-05
Why do i get this error message?
chown: cannot access `/home/chrissy/.cache/software-center/software-center.log': No such file or directory

---

### Post by mc4man on 2010-10-05
you could confirm first if desired, though the error message seems straightforward
```
ls -la /home/chrissy/.cache/software-center

```

Try 
```
sudo chown chrissy /home/chrissy/.cache/software-center/software-center.log
```

---

### Post by coffeecat on 2010-10-05
In Maverick, at least - I've just looked - there is no ~/.cache/software-center/software-center.log. Which begs the question why software-center, when started from the terminal, throws out this error message for the OP:

> **chrissy.millichamp said:**
> IOError: [Errno 13] Permission denied: '/home/chrissy/.cache/software-center/software-center.log

---

### Post by directhex on 2010-10-05
> **coffeecat said:**
> In Maverick, at least - I've just looked - there is no ~/.cache/software-center/software-center.log. Which begs the question why software-center, when started from the terminal, throws out this error message for the OP:

perms on the folder?

sudo chown -R chrissy ~/.cache/software-center/

---

### Post by chrissy.millichamp on 2010-10-05
Thank you so much everybody it worked. But I also want to know how did it cause to be like this?

---

### Post by directhex on 2010-10-05
> **chrissy.millichamp said:**
> Thank you so much everybody it worked. But I also want to know how did it cause to be like this?

At a guess, the first time you ran software-centre, you used sudo. So the folder was created with root as the owner, not you. Subsequently, you couldn't write to it.

---

### Post by mc4man on 2010-10-05
> In Maverick, at least - I've just looked - there is no ~/.cache/software-center/software-center.log.

It will be created once you use the software-center to install something - I didn't have it, used the sc and 
> doug@doug-laptop:~$ ls ~/.cache/software-center
agent.etag  icons  software-center-agent.db
doug@doug-laptop:~$ ls ~/.cache/software-center
agent.etag  icons  software-center-agent.db  software-center.log


---

### Post by coffeecat on 2010-10-05
> **mc4man said:**
> It will be created once you use the software-center to install something - I didn't have it, used the sc and

As I discovered after I posted. :oops:

Thanks!

---

