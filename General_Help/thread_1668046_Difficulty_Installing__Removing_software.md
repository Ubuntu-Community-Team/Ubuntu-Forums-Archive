---
title: "Difficulty Installing / Removing software"
date: 2011-01-15
forum: General Help
---

### Post by jwally on 2011-01-15
I apologize in advance if I'm posting this in the wrong forum;
but I've been hacking away at this for awhile and am afraid I
can't solve it.

I tried to install Ruby 1.9 this morning, 
the install was going well until this appeared
in the terminal and was stuck:

```

Unpacking replacement libruby1.9 ...

```Now anytime that I try and install / uninstall anything, terminal runs
across the same line and freezes.

In addition, I've tried to remove the package through synaptic,
however; I get the following response:

> libruby1.9: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

How do I make this stop?

---

### Post by Pollox on 2011-01-16
This may sound like a silly question, but did you try following the advice Synaptic gave you? (i.e. right click -> reinstall package) Does it still give you the same error/freeze? Also, have you tried waiting to see if the unpacking step finishes eventually?

---

### Post by James78 on 2011-01-16
Try these. Apt-get will probably continue trying to reinstall the package.
```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by jwally on 2011-01-16
> **Pollox said:**
> This may sound like a silly question, but did you try following the advice Synaptic gave you? (i.e. right click -> reinstall package) Does it still give you the same error/freeze? Also, have you tried waiting to see if the unpacking step finishes eventually?

Did, and it goes through the same process until it hangs at
```

Unpacking replacement libruby1.9 ...

```

only inside of Synaptic instead of Terminal.

Longest I've waited so far is 15 minutes;
what's the longest I should wait before killing a process
if nothing's showing progress?

---

### Post by jwally on 2011-01-16
@ James78

sudo apt-get install -f
sudo dpkg --configure -a
gives me the following from terminal:

```

jwally@jwally-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  emacs ruby-elisp nvidia-settings libgdbm-ruby1.8 libgdbm-ruby
  libreadline-ruby libdbm-ruby dkms libtcltk-ruby1.8 ruby1.8-elisp
  libtcltk-ruby libdbm-ruby1.8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libruby1.9
The following packages will be upgraded:
  libruby1.9
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/5,646kB of archives.
After this operation, 16.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libruby1.9.
(Reading database ... 
dpkg: warning: files list file for package `libruby1.9' missing, assuming package has no files currently installed.
(Reading database ... 190898 files and directories currently installed.)
Preparing to replace libruby1.9 1.9.0.5-1ubuntu1 (using .../libruby1.9_1.9.0.5-1ubuntu1_i386.deb) ...
Unpacking replacement libruby1.9 ...


```

---

### Post by cchhrriiss121212 on 2011-01-16
> Longest I've waited so far is 15 minutes;
Try waiting longer, some things just take a while to unpack.

---

### Post by ggarron on 2011-01-16
I may be completely away from the right answer, but, what repositories do you have?

I mean, try to change the server of your repositories, they may have a corrupted version of that package.
Or maybe you can download the library by yourself, and install with 

dpkg -i ....

---

### Post by jwally on 2011-01-16
James,
After re-starting; and re-running your commands,
the problem appears corrected!

thanks!

---

### Post by jwally on 2011-01-17
false hope;
its doing it with fslint now...

---

### Post by James78 on 2011-01-17
> **jwally said:**
> false hope;
its doing it with fslint now...
If you can remove the packages safely, because you don't need them installed, you *could* do.. (make sure it's not needed by anything else, otherwise you'll just break more packages)
```
sudo dpkg -P --force-all <package>
```

---

### Post by jwally on 2011-01-17
Worked 2x now on that package
until I gave up on it; installed something else with success!

Appears to work!
thanks

---

### Post by jwally on 2011-01-17
James,

Worked perfect,
thank you.

Not sure if it means anything, but this error
seems to happen more often
when I have my USB-hub plugged in.

it doesn't happen on all app installs, but I've had it hang on
-libruby1.9
-fslint
-liberror-perl

of which the latter 2 have been installed after reboot, usb unplugged

---

### Post by James78 on 2011-01-17
> **jwally said:**
> James,

Worked perfect,
thank you.
Glad you got it to work. :P
> **jwally said:**
> Not sure if it means anything, but this error
seems to happen more often
when I have my USB-hub plugged in.
I'm afraid I can't really help you on that part. It could be a USB hub problem, or not be related too it. You could probably try seeing when you get the problem when there's a USB plugged in. Try USB keys, external hard drives, etc, and if it only happens on the USB-hub, then it must be the USB-hub, oddly.

---

