---
title: "Massive bork, 'GNOME Power Manager' error - dpkg corruption?"
date: 2010-06-23
forum: General Help
---

### Post by doubi on 2010-06-23
Hi all,

I've tried to research my issue as best I can before posting here. System is 10.4 32bit on Acer Aspire 5720. Here's the chain of events:


[LIST]
[*]First noticed Firefox couldn't create a file under /tmp to download Virtualbox. Hm.
[*]Try to reload Firefox, it won't restart; freezes with one tab open, blank with transparent square in top-left, not a chrome loaded if I remember right. Both latest stable and Dev Preview.
[*]Maybe a reboot will work...
[*]Normal Ubuntu loading screen appears, but before anything else a message box appears near top right of screen:
[/LIST]
> Install problem!
The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.
[LIST]
[*]Shortly after, an abnormally styled pop-up appears asking me for my default keyring password - seemingly skipping the account login step.
[*]When I put in the keyring and click 'Ok', the button stays pressed down and the system hangs. Have to switch off.
[*]Boot into recovery mode, root with networking.
[*]I read somewhere that "dpkg --configure -a" followed by "apt-get -f install" might help. However, "dpkg --configure -a" fails thusly:
[/LIST]
```
dpkg: parse error, in file '/var/lib/dpkg/status' near line 0:
field name 'FLV' must be followed by colon
```
[LIST]
[*]That file looks like a binary when opened in vi so I assume I can't add said colon manually.
[*]Some users on forums / IRC logs seemed to be having locking issues; for me, prepending "fuser -vki /var/lib/dpkg/lock;" didn't help (not that it looked likely).
[*]One of the commands from the recovery menu (can't remember which... dpkg?) successfully pulls a screen of apt sources before outputting the same error three times, like this (last couple of successful Hit's listed):
[/LIST]
```

Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure  -a' to correct the problem
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure  -a' to correct the problem
root@laptop$

```So now I'm on a new Ubuntu 10.4 install (64bit this time) on a different partition. Someone (JackSparrow, [here]("http://irclogs.ubuntu.com/2008/12/17/%23ubuntu.html") at 00:22) asked if changes had been made to /etc/apt/source.list. This wasn't followed up but I remember I actually *did* try to change my sources. I just added something to the end; not sure what not (might be able to find out by looking through my bash history, if I knew how to do that? Usually have many terminals open at once.) However when I went to examine the sources.list of the failed system, the thing I added seemed to not be there; there were just a couple of minor differences, an 'archive' source under security, and an extra space before the cdrom source right at the top.

So, I come back to the unparseable dpkg status file. I take it I can't just replace it with the one from my new working system, as the status will be unique to the packages I have on the broken one. I'd reeeaally like to get this fixed, and more importantly to understand what happened and how I can not do it again.

Many thanks (for reading this far if nothing else!)

---

### Post by doubi on 2010-07-14
I've come back to trying to save my 32bit install after taking a break to get some real work done...

Thanks to [threads like this]("http://ubuntuforums.org/showthread.php?t=474587")[0] I learned I could replace /var/lib/dpkg/sources with one of its backups (in my case simply copying ./sources-old to ./sources in that folder ).

Then I got a new error:```
dpkg: truncated triggers deferred file '/var/lib/dpkg/triggers/Unincorp'
```Thanks to [these]("http://ubuntuforums.org/showthread.php?t=702324") [threads]("http://ubuntuforums.org/showthread.php?t=681675")[1][2] I learned that the 'natural' state of this file is to be empty. 'truncated' was really right in my case, as when I checked I saw it contained just one line which read something like "# the pres". So I removed that and left the file empty.

Then dpkg could work again, and updated over 100 packages, but I'm getting a different weird error.

Any apt-get command trying to bring my packages up to date ends thusly:```
Errors were encountered while processing:
linux-image-2.6.32-23-generic
linux-image-generic
linux-generic
linux-headers-2.6.32-23generic
linux-headers-generic
```After a couple of attempts I saw this root cause of the problem:```
debconf: Unable to load Debconf::Element::Dialogue. Failed because: Can't locate Debconf/Element/Dialogue.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/site_perl
```Something in the setup scripts for linux-image-2.6.32-23-generic tries to call "new" on a Debconf::Element::Dialogue object, but knowing a little about Perl, I rooted around and couldn't find a Dialogue.pm or a 'new' sub in a Debconf::Element::Dialog package.

Meanwhile my 64bit install on the partition I'm using right now upgraded to the latest kernel with no fuss at all s:

Even after updating all my packages, when I try to log in normally I still get the same original 'GNOME Power Manager' error and weird-looking keyring password.

I'll keep looking around for answers, if anyone has any ideas in the meantime they'd be warmly welcomed.

[0] [http://ubuntuforums.org/showthread.php?t=474587](http://ubuntuforums.org/showthread.php?t=474587)
[1] [http://ubuntuforums.org/showthread.php?t=702324](http://ubuntuforums.org/showthread.php?t=702324)
[2] [http://ubuntuforums.org/showthread.php?t=681675](http://ubuntuforums.org/showthread.php?t=681675)

---

### Post by doubi on 2010-07-14
Thanks to [Joel Cross in this launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/273681") I managed to get around the kernel install thing, which turned out to be related to nvidia-common. The solution was to apt-get purge nvidia-common, then apt-get -f install or whatever it was to get the pending kernel update, then reinstall nvidia-common.

I had to sort that out in order to follow advice from elsewhere on the Power Manager problem. When dpkg was playing ball again I tried --configure -a, apt-get clean, autoclean, autoremove, everything I'd seen mentioned anywhere that was meant to help, with no success.

Some other unsuccessful suggestions:
1. mkdir /var/lib/gconf/default
2. mv ~/.gconfd/saved_state ~/.gconfd/saved_state.old

Eventually I apt-get purge'd gnome-power-manager then reinstalled it.

Now when I try to log in, the power manager acts as normal (which in my case happens to be telling me my battery is on its last legs), but I'm **still** getting the weird-looking (unstyled) keyring login box without any of the rest of the desktop loading, and it still freezes when I enter the password.

About to try reconfiguring / reinstalling gdm & gconf.

Then it'll be matching "cat /var/log/dpkg.log | grep '\ install\ '" against /var/log/auth.log to see which packages I installed between my last successful logon and this massive freakup. Wish me luck!

---

### Post by doubi on 2010-07-15
I gave up.

Staying up all night doesn't help one's motivation to overcome adversity ;)

In the end it had progressed so that I would get a the graphical shutdown options box when pressing ctrl-alt-del after the keyring dialogue hung. Tried reinstalling ubuntu-desktop & gnome-desktop, gdm, gconf, but nothing helped.

Would have been great to find out what the heck was the matter with it. Aw well :)

---

