---
title: "Windows domain not available until after local login"
date: 2010-08-06
forum: General Help
---

### Post by gradysghost on 2010-08-06
Long story made short:

I used Likewise (specifically, likewise-open-gui) to add my computer to the Windows domain at work.  It works great.  I can log into the computer with my domain credentials.

Until I reboot.

If the computer ever shuts down fully, I get an authentication failure when I log in using the domain account.  But if I log in using a local account and run likewise-open-gui again from there, everything works.  I don't have to rejoin the domain, only launch the program, close it, and log out of the local account.  This seems to allow me to log into the domain afterward.

Is there something in specific that I can add to my startup scripts that will connect me to the domain before login?

---

### Post by gradysghost on 2010-08-09
Bump.

Any ideas, anybody?  I know it's just a minor issue, but it's preventing me from deploying Ubuntu to more people in this institution.

---

### Post by atworkwithjf on 2010-10-12
Which version of Likewise-Open are you using?  Are you using the package in the apt-get repo or using the updated version from the Likewise website?

---

### Post by gradysghost on 2010-10-27
So sorry I didn't come back to this thread.  For some reason, I didn't get the subscription email when you responded.

To be honest, I don't know what version it is, but I did manage to solve this.  I will mark as solved in a few minutes.  But here's how I fixed it:

I discovered that what solved the problem when doing this manually was logging onto the system with a local account, then running domainjoin-gui.  I took a look at the CLI commands for Likewise, and discovered that running

```
domainjoin-cli query
```

on a terminal solved the problem as well.  The only remaining trouble was getting this to happen automatically at boot.

So I created a file and populated it:

```
sudo echo 'sudo likewiseopen-cli query' > /etc/init.d/likewise
```

Then I inserted that into the startup process for runlevel 2.

```
sudo ln -s /etc/rc2.d/80likewise /etc/init.d/likewise
```

This causes Likewise to check its domain information after DNS has been established (in Ubuntu 10.04), but before some other things like power management.

---

### Post by atworkwithjf on 2010-10-27
gradysghost,

This is definitely not an ideal way to solve this.  I believe that lsass.d (Likewise Security Authority) is not starting because of the order the services are being started on your system.  Running the domainjoin kicks the daemon.

What I'd like to see if you are willing is if after commenting out the change you made and rebooting the system if lsass is actually running. 

> ps -ef | grep lsass

If not I think a better way to solve this may be to sort out the ordering of the init sequence.

Can you confirm the version of Ubuntu and the version of Likewise-Open you are using?

---

