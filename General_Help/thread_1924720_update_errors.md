---
title: "update errors"
date: 2012-02-13
forum: General Help
---

### Post by Malcy on 2012-02-13
Every time that I update or try to install files, the same error is posted.

> Setting up cups (1.5.0-8ubuntu6) ...
/etc/init.d/cups: 8: basename: not found
/usr/sbin/invoke-rc.d: 449: basename: not found
: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up php5-cli (5.3.6-13ubuntu3.5) ...
/usr/bin/ucf: line 39: basename: command not found
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 cups
 php5-cli
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up php5-cli (5.3.6-13ubuntu3.5) ...
/usr/bin/ucf: line 39: basename: command not found
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 php5-cli
I can't seem to get rid of these problems. It's probably quite simple.

Any ideas?

---

### Post by mmsmc on 2012-02-13
First of all what kind of updating are you doing (updating specific programs, the OS... etc)
and to clarify, this happens when installing new software or just updating
and does it happen with every program

---

### Post by philinux on 2012-02-13
> **Malcy said:**
> Every time that I update or try to install files, the same error is posted.

I can't seem to get rid of these problems. It's probably quite simple.

Any ideas?

Try these 

```
sudo dpkg --configure -a
```

then

```
sudo apt-get install -f
```

---

### Post by Malcy on 2012-02-13
It's Kubuntu 11.10 and I get errors based around the same files if I use Muon or Synaptic, apt-get upgrade, dpkg -- configure -a etc.

Here is the output from apt-get install -f

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up cups (1.5.0-8ubuntu6) ...
/etc/init.d/cups: 8: basename: not found
/usr/sbin/invoke-rc.d: 449: basename: not found
: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up php5-cli (5.3.6-13ubuntu3.5) ...
/usr/bin/ucf: line 39: basename: command not found
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 cups
 php5-cli
E: Sub-process /usr/bin/dpkg returned an error code (1)

And from dpkg --configure -a

> Setting up php5-cli (5.3.6-13ubuntu3.5) ...
/usr/bin/ucf: line 39: basename: command not found
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 php5-cli

---

### Post by mmsmc on 2012-02-13
well im no expert, but im pretty sure your files have been corrupted, no clue how, I'd wait for other posts for help, but if they dont work it may come to booting live and replacing those files

---

### Post by philinux on 2012-02-13
I checked my system and the same script exists with basename in it. (See man basename, no idea what it's for never used it). You can see it with this.

```
cat /usr/bin/ucf
```

The problem is with the php5-cli app. Lets see if it's installed.

```
apt-cache policy php5-cli
```

---

### Post by Malcy on 2012-02-13
Here is the output from that command:

> php5-cli:
  Installed: 5.3.6-13ubuntu3.5
  Candidate: 5.3.6-13ubuntu3.5
  Version table:
 *** 5.3.6-13ubuntu3.5 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.3.6-13ubuntu3.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages


It seems to be installed (to me anyway).

---

### Post by philinux on 2012-02-13
> **Malcy said:**
> Here is the output from that command:



It seems to be installed (to me anyway).

Ok lets remove it for now. We'll put it back after.

```
sudo apt-get purge php5-cli
```


```
sudo apt-get update && sudo apt-get upgrade
```

What errors do you see now.

---

### Post by Ceratopsia on 2012-02-13
Are you updating or upgrading?


 If your updating

1.Install your system.

2. when you login go to terminal

3. type:  sudo apt-get update

4. it will ask you for you password and it will start
    after it stops and the prompt returns, exit the terminal.

5. go to you update manager and run that.

I hope this helps you. if not my apologies..

Ceratopsia

---

### Post by Malcy on 2012-02-13
The output for sudo apt-get purge php5-cli is

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  php5-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  php5-cli*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 8,204 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162609 files and directories currently installed.)
Removing php5-cli ...
dpkg: warning: while removing php5-cli, directory '/etc/php5/cli' not empty so not removed.
Processing triggers for man-db ...
Setting up cups (1.5.0-8ubuntu6) ...
/etc/init.d/cups: 8: basename: not found
/usr/sbin/invoke-rc.d: 449: basename: not found
: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 cups
E: Sub-process /usr/bin/dpkg returned an error code (1)And from sudo apt-get update && sudo apt-get upgrade

> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cups (1.5.0-8ubuntu6) ...
/etc/init.d/cups: 8: basename: not found
/usr/sbin/invoke-rc.d: 449: basename: not found
: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 cups
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by philinux on 2012-02-13
> **Malcy said:**
> The output for sudo apt-get purge php5-cli is

And from sudo apt-get update && sudo apt-get upgrade

Lets make sure you have this package installed as it includes basename.

```
apt-cache policy coreutils
```

---

### Post by Malcy on 2012-02-13
That package seems to be there.

> coreutils:
  Installed: 8.5-1ubuntu6
  Candidate: 8.5-1ubuntu6
  Version table:
 *** 8.5-1ubuntu6 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages
        100 /var/lib/dpkg/status


---

### Post by philinux on 2012-02-13
> **Malcy said:**
> That package seems to be there.

Have you been playing with scripts cos something messed in your system.

Try this in a terminal.

```
basename /usr/bin/sort
```

It should just return sort as the output.

---

### Post by Malcy on 2012-02-13
No, I haven't been playing with scripts or anything exotic. I did have backports enabled for some reason but it is not now.

Here is the output

> The program 'basename' is currently not installed.  You can install it by typing:
sudo apt-get install coreutils
I tried sudo apt-get install coreutils but it was no help.

---

### Post by philinux on 2012-02-13
> **Malcy said:**
> No, I haven't been playing with scripts or anything exotic. I did have backports enabled for some reason but it is not now.

Here is the output
> The program 'basename' is currently not installed. You can install it by typing:
sudo apt-get install coreutils 

I tried sudo apt-get install coreutils but it was no help.

This is why you are getting errors regarding basename as the system cant find it. You've done something to cause a script redirect or something. So when the system looks for basename it cant find it.

You could try reinstalling coreutils. After that I cant help. Someone else might though.

```
sudo apt-get install --reinstall coreutils
```

---

### Post by Malcy on 2012-02-13
That did it, everything looks fine now.

Thank you very much for spending the time sorting this out for me.

---

### Post by philinux on 2012-02-13
> **Malcy said:**
> That did it, everything looks fine now.

Thank you very much for spending the time sorting this out for me.

Nice one. You can reinstall that php app now.

I did find one other thing to try for this situation.

```
which basename
``` should have returned
/usr/bin/basename

I wonder where yours was lol. :P

Dont forget to marked this as Solved.

---

