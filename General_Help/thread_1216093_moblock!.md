---
title: "**** moblock!"
date: 2009-07-17
forum: General Help
---

### Post by litechocolate on 2009-07-17
It has screwed up my entire networking setup. Vuze downloads are capped at 400k and I can no longer retrieve my email with thunderbird. When I tried to remove the software I got this error message in the terminal.

litechocolate@litechocolate-laptop:~$ sudo dpkg --remove --force-remove-reinstreq moblock
[sudo] password for litechocolate: 
dpkg: dependency problems prevent removal of moblock:
 blockcontrol depends on moblock (>> 0.9~rc2-19) | nfblock; however:
  Package moblock is to be removed.
  Package nfblock is not installed.
dpkg: error processing moblock (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 moblock
litechocolate@litechocolate-laptop:~$ 

Can someone please help me? Thanks.

---

### Post by zeronothing on 2009-07-17
Try removing the package blockcontrol along with moblock. That is a dependency that associated to moblock for some reason. Also you should try flushing the IP tables that moblock creates. Try doing this command in terminal:

sudo iptables -F

This will flush out any rules that moblock put into place. if you want to try another program similar without the hassle, try iplist. Its much easier in my opinion. 

[http://sourceforge.net/projects/iplist/](http://sourceforge.net/projects/iplist/)

---

### Post by jre on 2009-07-19
If you decide to stay with moblock have a look at 
[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) 

Indeed there´s some configuration necessary for any IPBlocker (moblock and iplist both check your whole system´s traffic, so they both may block more sites/ports than you really want).

You may further consider using mobloquer as GUI.

---

### Post by ciscoman10 on 2010-11-22
I have searched around a bit and am having difficulty purging blockcontrol off my system.  I am running Ubuntu 10.04 LTS 64bit.  I have been able to remove some of the programs attached to blockcontrol but cannot remove blockcontrol.  The synaptics package manager and console root access will not rip out blockcontrol.  I want the entire Moblock/Blockcontrol set off the system.
root@computer-desktop:/home/nas# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up blockcontrol (1.6.13-1~lucid) ...
/etc/blockcontrol/blockcontrol.conf: 15: Syntax error: Unterminated quoted string
dpkg: error processing blockcontrol (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 blockcontrol
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@computer-desktop:/home/nas# 

then I tried to remove blockcontrol via the synaptic package manager and got the following popup
E: blockcontrol: subprocess installed pre-removal script returned error exit status 2


please help...  I have too much setup on this system to just blow it all out and start again.

;)

---

### Post by jre on 2010-11-23
Please start a new thread for new problems!

> **ciscoman10 said:**
> ```
/etc/blockcontrol/blockcontrol.conf: 15: Syntax error: Unterminated quoted string
```
So you have to edit that line and add a ```
"
```

---

### Post by ciscoman10 on 2010-11-23
I will thanks.

---

