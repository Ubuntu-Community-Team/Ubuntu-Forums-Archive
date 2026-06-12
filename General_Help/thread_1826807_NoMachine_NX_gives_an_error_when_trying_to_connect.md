---
title: "NoMachine NX gives an error when trying to connect?"
date: 2011-08-17
forum: General Help
---

### Post by i-o on 2011-08-17
Hi,

I bump into an problem with NoMachine NX software. It gives following error message when trying to make an connection:
"Your subscription doesn't match the installed NX server product"

I have NX Free Edition for Linux installed on both systems with latest sw versions.
nxclient - 3.5.0-7
nxnode - 3.5.0-4
nxserver - 3.5.0.5

System A has 64-bit Ubuntu 10.10 and System B has 32-bit Ubuntu 11.04. 
Connections from System B to system A succeed. But when trying to make the connection other way, from A to B it gives this error message. Since it clearly indicates to some kind of license issue while I'm using free version on both systems I really dont see what I could do. Re-installing NX to system A makes no difference.

Any hints or ideas?

---

### Post by i-o on 2011-08-23
Someone, anyone?

---

### Post by promet on 2011-09-12
I know that there are several versions of the NoMachine software on the website, one of which is an Enterprise version and one is a specifically indicated "Free" version for Linux, if I remember correctly. 

You may want to uninstall your current .debs and return to the site and make sure that you've retrieved the aforementioned "free" versions. This is just off the top of my head mind you.

Good Luck!

---

### Post by i-o on 2011-09-13
NX versions are all 'Free'. I have re-downloaded and re-installed them to both systems with no change to situation.
Any other ideas?

---

### Post by wonderdrug on 2011-11-05
A bit late, but I just rant into the same issue.
What I did to fix it was uninstall, delete all
files from /usr/NX and then re-install.

I think I got into the issue because I installed
NX 4 Preview and then tried downgrading back to
NX 3.x.

---

### Post by hi-phile on 2012-04-12
Not sure if this will help, but this is what I did to get it all working.  

Remove any existing nomachine installation.

Re-install all the files again (nxserver, nxnode, nxclient).

Edit the /etc/hosts file to include the hostname of the server then restart the network.

Also, I had to uncheck the option under the 'Advanced' tab in the nxclient "Disable encryption of all traffic."

---

### Post by promet on 2012-04-12
I've also noticed in messing around with this issue, that somehow the login user's .Xauthority file (in the user's home directory) will often interfere, somehow, with an otherwise workable NX installation.

I've taken to "ssh-ing" into the server and doing a quick:

```
rm ./.Xauthority
```

and then connecting with my nxclient when I have problems. It's a little "hacky", but hey...

---

### Post by kiirokurisu on 2012-04-13
I'm not sure if NoMachine NX is somehow superior (it could well be), but I found FreeNX ridiculously easy to get going. Just installed the server components from their PPA and the Remmina client plugin, and I was in business. Took all of 2 minutes.

PPA: [https://launchpad.net/~freenx-team/+archive/ppa](https://launchpad.net/~freenx-team/+archive/ppa)

---

