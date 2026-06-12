---
title: "Cannot install sSMTP"
date: 2009-07-10
forum: General Help
---

### Post by t0p on 2009-07-10
Looking for a program I can use from a script to send email via gmail's smtp server as I explained  [in this thread](http://ubuntuforums.org/showthread.php?t=1209081).

I thought I'd found a solution - **sSMTP**.  As Tombuntu tells us [here]("http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/"):

> Wouldn&#8217;t it be useful if your computer could email you? I&#8217;d like to be notified by email when my server is in trouble, but I don&#8217;t want to run my own mail server. sSMTP is perfect for this; it&#8217;s a simple way to send email from your system to an SMTP mail server, like Gmail&#8217;s.

So I decided to install sSMTP and configure it to send mail via gmail.  I started to follow [Tombuntu's instructions](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/):

```
sudo apt-get install ssmtp
```

But that was as far as I got.  Apt-get told me that to install sSMTP it needed to remove **exim4**.  But it couldn't!

```
t0p@ubunty:~$ sudo apt-get install ssmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  exim4-base exim4-config exim4-daemon-light
The following NEW packages will be installed
  ssmtp
0 upgraded, 1 newly installed, 3 to remove and 20 not upgraded.
Need to get 0B/47.5kB of archives.
After this operation, 3609kB disk space will be freed.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg: exim4-base: dependency problems, but removing anyway as you request:
 exim4-daemon-light depends on exim4-base (>= 4.69).
(Reading database ... 273630 files and directories currently installed.)
Removing exim4-base ...
 * Stopping MTA                                                                 /sbin/start-stop-daemon: warning: failed to kill 7552: No such process
invoke-rc.d: initscript exim4, action "stop" failed.
dpkg: error processing exim4-base (--remove):
 subprocess post-removal script returned error exit status 3
Removing exim4-config ...
dpkg: exim4-daemon-light: dependency problems, but removing anyway as you request:
 mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is to be removed.
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not installed.
  Package mail-transport-agent is not installed.
  Package exim4-daemon-light which provides mail-transport-agent is to be removed.
Removing exim4-daemon-light ...
 * Stopping MTA                                                                 /sbin/start-stop-daemon: warning: failed to kill 7552: No such process
invoke-rc.d: initscript exim4, action "stop" failed.
dpkg: error processing exim4-daemon-light (--remove):
 subprocess pre-removal script returned error exit status 3
Errors were encountered while processing:
 exim4-base
 exim4-daemon-light
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I pondered this for a moment, and decided that trying to install ssmtp again might push apt-get to do something about this:

```
t0p@ubunty:~$ sudo apt-get install ssmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies.
  exim4-daemon-light: Depends: exim4-base (>= 4.69) but it is not going to be installed
                      Conflicts: mail-transport-agent
  ssmtp: Conflicts: mail-transport-agent
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).
```

*Grrr!!*  So, how about I remove exim4-daemon-light myself?

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies.
  lsb-core: Depends: postfix but it is not going to be installed or
                     mail-transport-agent
  mailx: Depends: exim4 but it is not going to be installed or
                  mail-transport-agent
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).

```

I couldn't think of a way out of this.  So, I did 'sudo apt-get -f install' to at least get exim back:

```
t0p@ubunty:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  exim4-config
The following NEW packages will be installed
  exim4-config
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
1 not fully installed or removed.
Need to get 0B/1291kB of archives.
After this operation, 1053kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package exim4-config.
(Reading database ... 273527 files and directories currently installed.)
Unpacking exim4-config (from .../exim4-config_4.69-2_all.deb) ...
Selecting previously deselected package exim4-base.
Preparing to replace exim4-base 4.69-2 (using .../exim4-base_4.69-2_i386.deb) ...
Unpacking replacement exim4-base ...
Setting up exim4-config (4.69-2) ...

Setting up exim4-base (4.69-2) ...

```

So, there we are.  I've got exim4 reinstalled.  But no sSMTP, seemingly because apt-get can't manage to remove exim4.

Can anyone help? What I need is either **a way to install sSMTP** or **another program that can be run from a script and can send mail via smtp.gmail.com**.  Cheers.

---

### Post by t0p on 2009-07-10
Huh!  I just tried to install **postfix**, as described [here]("http://souptonuts.sourceforge.net/postfix_tutorial.html"), as part of my plan to send email to smtp.gmail.com via the command line.  But it failed, down to inability to remove **exim4-config** and **exim4-base**.  Again, I had to run 'sudo apt-get -f install' to fix the problem, leaving me where I started.  Again.  Huh!

C'mon, peeps!  Someone's *gotta* know how I can get round this craziness!  I want to install a command line mail utility that can send via smtp.gmail.com and can be invoked by a script.  Who's gonna help me??

---

### Post by t0p on 2009-07-11
Okay, calm down! You don't have to rush to come help me now, I fixed it myself.  Since I couldn't install sSMTP, I had to see if there was a way to use exim4 to send mail via smtp.gmail.com.   And there is! [as I learned here on the debian wiki]("http://wiki.debian.org/GmailAndExim4").

So, although my failure to install sSMTP was not solved, I achieved what I'd set out to do - send email from command line via gmail's servers.  So I've stuck on a 'solved' tag.

---

