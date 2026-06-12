---
title: "privoxy not starting up"
date: 2009-11-28
forum: General Help
---

### Post by Shea7993 on 2009-11-28
Hi, ive ran into alil problem, I use privoxy on my desktop to allow me to browse annonymously and without adds, ofcourse im sure most people do... but i suddenly have a problem since upgrading.

Now ive never realy had an issue with it at all, untill recently when i installed a fresh copy of 9.10 Karmic 64bit, its not a major problem, its just I have to manually start privoxy up via sudo command everytime i start up my Desktop, and also after a long while it seems to automaticly disable itself, forcing me to restart the daemon.

Ive checked my starup services, and privoxy is listed and active to start but it doesnt, Im assuming its permission related issues so yes ive even tried to alter the permissions as root, making myself as user the owner, my group -rw perm, even the others -rw, and all combinations therof, and no matter what, starting it up through command without sudo just gives me permission denied errors...

Can anybody maybe help me to just get privoxy running from startup without having to manually command it?

Thanx

---

### Post by crm71 on 2009-11-30
Greetings,

I ran into this problem with privoxy 3.0.13-1 after a clean install upgrade to ubuntu 9.10.  Below is a functional workaround for me.

Check your normal runlevel:

```
runlevel
```Most likely in ubuntu yours will default to 2.

Next we'll glance at the existing rc?.d links:

```
ls -l /etc/rc?.d/*privoxy
```lrwxrwxrwx 1 root root 17 2009-11-27 21:32 /etc/rc0.d/K20privoxy -> ../init.d/privoxy
lrwxrwxrwx 1 root root 17 2009-11-27 21:32 /etc/rc1.d/K20privoxy -> ../init.d/privoxy
lrwxrwxrwx 1 root root 17 2009-11-27 21:32 /etc/rc2.d/**S99privoxy** -> ../init.d/privoxy
lrwxrwxrwx 1 root root 17 2009-11-27 21:32 /etc/rc3.d/S20privoxy -> ../init.d/privoxy
lrwxrwxrwx 1 root root 17 2009-11-27 21:32 /etc/rc4.d/S20privoxy -> ../init.d/privoxy
lrwxrwxrwx 1 root root 17 2009-11-27 21:32 /etc/rc5.d/S20privoxy -> ../init.d/privoxy
lrwxrwxrwx 1 root root 17 2009-11-27 21:32 /etc/rc6.d/K20privoxy -> ../init.d/privoxy

Your output should show similar with the exception being  /etc/rc2.d/S99privoxy, you should show a *default install* of S20privoxy.  Permissions show fine, but there seems to be a sequence timing issue with something else.  So, let's bump that up.  The NN number involved is the sequence order used by init for running the scripts in the respective rc#.d paths.  Upping mine to 99 at a runlevel of 2 was a workaround.  You can try values >20 <99 if you wish to experiment. (for more details *man update-rc.d*)

```
sudo mv /etc/rc2.d/S20privoxy /etc/rc2.d/S99privoxy
```Substitute rc2.d above with rcN.d with N being whatever runlevel you had other than 2 (or change them for 2-5 entirely) and confirm the change:

```
ls -l /etc/rc?.d/*privoxy
```Where this problem is discussed further:
[https://bugs.launchpad.net/ubuntu/+source/privoxy/+bug/427625](https://bugs.launchpad.net/ubuntu/+source/privoxy/+bug/427625)

As an aside, adding the code below into the do_start() portion of /etc/init.d/privoxy script as mentioned in the bug report **didn't** work for me.

```
        start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
                $DAEMON_ARGS \
                && return 0

```Cheers :)

---

### Post by Shea7993 on 2009-11-30
Thanx alot, it worked for me =] im not very familiar with the method and commands, so im going to start looking into it just incase for future problems, but thanx alot you were a great deal of help.

---

### Post by crm71 on 2009-11-30
Glad to help, especially on issues I needed to resolve. ;)

Now for the more appropriate and less *quick n' dirty* workaround (using provided admin scripts and not manually renaming links), following the update-rc.d perl script documentation.

The problem: without trying to dig in logs further, privoxy is failing to run due to a dependency issue by being ran too early.  You can verify this on your own by manual startup at your regular runlevels, e.g.:

```
sudo /etc/init.d/privoxy status
```Now confirm it runs fine manually:
```
sudo /etc/init.d/privoxy start
sudo /etc/init.d/privoxy status

```**If it's not running at this point something more dubious is wrong than just the init scripts.**

The installer is defaulting by an older method of a sequence value of 20 as we saw on initial links from the prior reply.  Privoxy has some dependency issues and I found that a start value of 40 works (99 is somewhat extreme and the stop values were not modified appropriately to compensate).  We should generally have sequence start + stop value relationship  = 100.  So, in this case, stop values at runlevels 0 1 6 (K prefix name links) should be 60.  Here's how we're meant to fix this the ubuntu(debian) way:

Remove the existing runlevel links to the /etc/init.d/privoxy script.```
sudo update-rc.d -f privoxy remove
```Create our specific revised runlevel links.```
sudo update-rc.d privoxy start 40 2 3 4 5 . stop 60 0 1 6 .
```Sanity check to see the respective S/K runlevel links created by the update-rc.d perl script:
```
ls -l /etc/rc?.d/*privoxy
```If everything looks good, reboot and check for success.  Increment/decrement the start/stop values respectively as needed until functional.

This is what my first reply should have stated, but I tend to whip out the manual swiss army knife and dig to find a quick solution. :biggrin:

Cheers

---

