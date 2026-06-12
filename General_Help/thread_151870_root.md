---
title: "root"
date: 2006-03-28
forum: General Help
---

### Post by HeYeahThat0neGuy on 2006-03-28
What is the root password? When I try to install Limewire (which I finally figured out how to do) it asks for the root password. what is that?:confused:

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=HeYeahThat0neGuy]What is the root password? When I try to install Limewire (which I finally figured out how to do) it asks for the root password. what is that?:confused:[/QUOTE]
Well, if you have a root account then use that password, but if you don't have a root account-use your Admin (account from install, regular account) password.

---

### Post by taurus on 2006-03-28
There is NO root password in Ubuntu.  Instead, you use "sudo" to install stuff to your system...
```

sudo <program name>
(and when it asks you for a password, use the same one that you log in with...)

```

---

### Post by HeYeahThat0neGuy on 2006-03-28
where do I put that in the terminal? Because when I tried it just said:
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
So I tried it as Sudo <limewire> and I got this:
bash: syntax error near unexpected token `newline'

---

### Post by taurus on 2006-03-28
[QUOTE=HeYeahThat0neGuy]where do I put that in the terminal? Because when I tried it just said:
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
So I tried it as Sudo <limewire> and I got this:
bash: syntax error near unexpected token `newline'[/QUOTE]
What exactly is the name of the program, LimeWire, you want to install?  That is the name that you have to type in after sudo from a command prompt...  If not sure, paste the output of this command, assuming that is where LimeWire is, here then!
```

ls -la

```

---

### Post by Qrk on 2006-03-28
Use sudo just before whatever command you are going to run. (on the same line)

For instance, to run nautilus as root, do:

```
sudo nautilus
```

not 

```
sudo
nautilus
```

If you want to run multiple commands without having to type sudo, try ```
sudo su
nautilus
```

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=HeYeahThat0neGuy]where do I put that in the terminal? Because when I tried it just said:
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
So I tried it as Sudo <limewire> and I got this:
bash: syntax error near unexpected token `newline'[/QUOTE]
Try reinstalling limewire. I would recommend using synaptic for the job, just search for it then select it for re-install. Try running limewire as sudo limewire.

---

### Post by HeYeahThat0neGuy on 2006-03-28
sudo: Limewire: command not found


that's what I got

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=HeYeahThat0neGuy]sudo: Limewire: command not found


that's what I got[/QUOTE]
It's just "sudo limewire" no quotes. Try that.

---

### Post by HeYeahThat0neGuy on 2006-03-28
I never did quotes

---

### Post by HeYeahThat0neGuy on 2006-03-28
Od I do this in the applications>accessories>terminal?

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=HeYeahThat0neGuy]Od I do this in the applications>accessories>terminal?[/QUOTE]

> sudo limewire

Just like that. No caps, just copy and paste into the terminal and hit enter.

---

### Post by HeYeahThat0neGuy on 2006-03-28
Got the same thing

---

### Post by taurus on 2006-03-28
[QUOTE=HeYeahThat0neGuy]Got the same thing[/QUOTE]
Again, what is the output of this command from a terminal???
```

ls -la

```

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=HeYeahThat0neGuy]Got the same thing[/QUOTE]
hmmm... try synaptic. It's under SYSTEM>Administration>Synaptic. Then search for "limewire" and select re-install-if you installed it at all. If that doesn't work, try Automatix.

---

### Post by HeYeahThat0neGuy on 2006-03-28
that's the thing it won't even let me install it.

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=HeYeahThat0neGuy]that's the thing it won't even let me install it.[/QUOTE]
try 

sudo apt-get install limewire

put it in terminal

---

### Post by HeYeahThat0neGuy on 2006-03-28
everette@everette:~$ sudo apt-get install limewire
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package limewire

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=HeYeahThat0neGuy]everette@everette:~$ sudo apt-get install limewire
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package limewire[/QUOTE]
replace your current sources.list with this one (see bottom of my post). I know that you may be getting discouraged but you will get it working :) I had these problems when I first started using Ubuntu.

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by HeYeahThat0neGuy on 2006-03-28
when I got to the last step, this is what I got:

everette@everette:~$ $sudo apt-get update ; sudo apt-get upgrade
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  juk
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
everette@everette:~$ sudo apt-get install limewire
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package limewire
everette@everette:~$

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=HeYeahThat0neGuy]when I got to the last step, this is what I got:

everette@everette:~$ $sudo apt-get update ; sudo apt-get upgrade
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  juk
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
everette@everette:~$ sudo apt-get install limewire
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package limewire
everette@everette:~$[/QUOTE]

In the sudo apt-get update command, you don't need the $. Try just:

sudo apt-get update

then

sudo apt-get install limewire

Edit: Just tried it with the $ sign and it gives me the same error ! Just don't use it and I think that you'll have it :)

---

### Post by HeYeahThat0neGuy on 2006-03-28
so now what do I do?




PS: I still can't get my computer to recognize when I plug in my ZEN to the USB port....

---

### Post by Qrk on 2006-03-28
Edit: Try Masterchief's way first, I'm afraid I waited too long before hitting submit. Using the repositories is the easiest way to do anything. But if you do want Frostwire, I'll leave my post.




Try the .deb package of Limewire's clone, Frostwire.

[http://prdownloads.sourceforge.net/frostwire/FrostWire-4.10.9-1.i586.deb?download](http://prdownloads.sourceforge.net/frostwire/FrostWire-4.10.9-1.i586.deb?download)

Save to your desktop, and install it with 

```
cd ~/Desktop
sudo dpkg -i *.deb
```

You'll need Java to use either Frostwire or Limewire.

---

### Post by HeYeahThat0neGuy on 2006-03-28
ok I did that and it looks like it went swimmingly, but how do I access it? I'm so used to windows where it just puts an icon on the desktop and there ya go.

---

### Post by xXx 0wn3d xXx on 2006-03-28
[QUOTE=HeYeahThat0neGuy]ok I did that and it looks like it went swimmingly, but how do I access it? I'm so used to windows where it just puts an icon on the desktop and there ya go.[/QUOTE]
Alright ! I should be under Applications>Internet or somewhere under Applications. Just click the limewire icon. I don't use p2p/bittorrent software but I would try frostwire too. To see which one that you like better.

---

### Post by trent dillman on 2006-03-28
Let's suppose you installed Limewire in /opt.

```

sudo -s
cat > /usr/bin/limewire

```

This will give you a blinking cursor, no prompt. Type this:

```

#!/bin/bash
cd /opt/LimeWire
./runLime.sh

```

then, press CTRL+D to end typing.

Make the script executable:

```
sudo chmod 755 /usr/bin/limewire
```

Run with the command

```
limewire
```

---

### Post by Qrk on 2006-03-28
If you got frostwire...

You can open frostwire by typing

frostwire 

in a terminal.

---

### Post by HeYeahThat0neGuy on 2006-03-28
everette@everette:~$ frostwire
/bin/bash: cd /opt/Frostwire./runfrost.sh: No such file or directory
everette@everette:~$

GOD this is so frustrating!

I see the icon in my internet menu but nothing happens when I click it. 


And ******* my ZEN still doesn't work.

---

### Post by HeYeahThat0neGuy on 2006-03-28
everette@everette:~$ sudo apt-get install frostwire
Reading package lists... Done
Building dependency tree... Done
frostwire is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emacs21 (21.4a-1ubuntu1) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50autoconf (source)...
Loading 50dictionaries-common (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading 50psvn (source)...
Loading 50vc-svn (source)...
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-autogen.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-compat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-edebug.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-load.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/ezimage.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/inversion.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/mode-local.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/pprint.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/sformat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/working.elc
Done
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Done
install/eieio: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50autoconf (source)...
Loading 50dictionaries-common (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading 50psvn (source)...
Loading 50vc-svn (source)...
Source file `/usr/share/emacs21/site-lisp/eieio/eieio.el' newer than byte-compiled file
Loading /usr/lib/emacs/21.4/i386-linux/fns-21.4.1-x.el (source)...
Source file `/usr/share/emacs21/site-lisp/eieio/eieio-comp.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/eieio/chart.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-base.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-comp.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-custom.elc
Source file `/usr/share/emacs21/site-lisp/eieio/eieio-opt.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-doc.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-load.elc
Error loading speedbar... ignored.
Wrote /usr/share/emacs21/site-lisp/eieio/eieio-opt.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/eieio/eieio-speedbar.el:
  !! Wrong type argument ((stringp nil))
Done
emacs-install: /usr/lib/emacsen-common/packages/install/eieio emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)

That is what I get when I try to install frostwire

---

### Post by Qrk on 2006-03-28
Hmm. Try this, I got it from another thread.

```

wget http://voxel.dl.sourceforge.net/sourceforge/frostwire/FrostWire-4.10.5-0.i586.deb
sudo dpkg -i FrostWire-4.10.5-0.i586.deb
```

If you still have trouble, post the output of the following command here.

```
java -version
```

---

### Post by trent dillman on 2006-03-30
Sorry about the /opt thing there, I thought you were installing LimeWire, not frostwire....You replied while I was typing...

---

