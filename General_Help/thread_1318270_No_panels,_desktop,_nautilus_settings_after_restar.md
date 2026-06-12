---
title: "No panels, desktop, nautilus settings after restart"
date: 2009-11-07
forum: General Help
---

### Post by vladu on 2009-11-07
This is an ugly one in Ubuntu 9.10

I noticed my desktop was acting strange - My home folder disappeared and the drag and select transparent box was not working anymore. So I restarted and, here we go, step by step:

1. blank screen with small error window (after the brown splash screen)
> Could not update ICEauthority file /home/vlad/.ICEauthority
2. same blank screen, next message:
> There is a problem with the configuration server.
/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256
3. This one shows up atop of the default orange background (not the one I had set)
> Nautilus could not create the following folders
/home/vlad/Desktop
/home/vlad/.nautilus
4. This error appeared after the first restart and i managed to save it thanks to my data partition showing up on the desktop (although I had disabled it from gconf-editor).
> GConf error: No database available to save your configuration: Unable to store a value at key '/apps/nautilus/preferences/always_use_location_entry', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf

The first time I restarted I could access anything I wanted through Alt+F2. But when I restart now, error 4 is gone and I can't do anything but to switch to a terminal with Ctrl+Alt+1. The only thing working

I also tried selecting the recovery mode in grub but it came to a halt after showing me a long array of the same error
> mountfail: mount /media/windows [2609] terminated with status 21

Any ideas as to why this happened and how I could fix it?
Thanks

---

### Post by vladu on 2009-11-07
I found a way out of this. First, to get the desktop back, simply drop to a tty terminal (Ctrl+Alt+1), login and type
```
sudo gdm stop
```
I don't know why, but this spawns a new, working graphical session instead of the old faulty one.

Now, to the source of the problem. It seems that autologin doesn't behave nicely in Ubuntu Karmic. That's probably because upon install I selected the option of encrypting my home folder. Simply turn off autologin and the system returns to normal.

I'll file a bug report on this later this evening.

---

