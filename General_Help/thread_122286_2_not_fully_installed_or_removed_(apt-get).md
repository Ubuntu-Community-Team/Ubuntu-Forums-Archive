---
title: "2 not fully installed or removed (apt-get)"
date: 2006-01-27
forum: General Help
---

### Post by paradox814 on 2006-01-27
I keep getting an error, which I'm assuming is directly related to this (when usign apt-get):
2 not fully installed or removed.
more specifically when using: sudo apt-get install *anything*

I want to cancel those 2 unfinished installs, I don't need them anymore and I hate having to see all those errors whenever I try installing anything else.

this is the exact output of:
sudo apt-get install mozilla-mplayer
```

Reading package lists... Done
Building dependency tree... Done
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up openssh-server (4.1p1-7ubuntu4) ...
Creating SSH2 RSA key; this may take some time ...illegal option -- f
Usage: ssh-keygen [options] [key1 key2 ...]

Where `options' are:
 -b nnn         Specify key strength in bits (e.g. 1024)
 -t dsa | rsa   Choose the key type.
 -c comment     Provide the comment.
 -e file        Edit the comment/passphrase of the key.
 -p passphrase  Provide passphrase.
 -P             Assume empty passphrase.
 -?
 -h             Print this help text.
 -q             Suppress the progress indicator.
 -1 file        Convert a SSH 1.x key.
 -i file        Load and display information on `file'.
 -D file        Derive the public key from the private key 'file'.
 -B number      The number base for displaying key information (default 10).
 -V             Print ssh-keygen version number.
 -r file        Stir data from file to random pool.
 -F file        Dump fingerprint of file.


Creating SSH2 DSA key; this may take some time ...illegal option -- f
Usage: ssh-keygen [options] [key1 key2 ...]

Where `options' are:
 -b nnn         Specify key strength in bits (e.g. 1024)
 -t dsa | rsa   Choose the key type.
 -c comment     Provide the comment.
 -e file        Edit the comment/passphrase of the key.
 -p passphrase  Provide passphrase.
 -P             Assume empty passphrase.
 -?
 -h             Print this help text.
 -q             Suppress the progress indicator.
 -1 file        Convert a SSH 1.x key.
 -i file        Load and display information on `file'.
 -D file        Derive the public key from the private key 'file'.
 -B number      The number base for displaying key information (default 10).
 -V             Print ssh-keygen version number.
 -r file        Stir data from file to random pool.
 -F file        Dump fingerprint of file.


 * Restarting OpenBSD Secure Shell server... Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.
invoke-rc.d: initscript ssh, action "restart" failed.
dpkg: error processing openssh-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssh-server
 ssh
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried looking all over the internet and the man pages but couldn't find anything related to this. I am new so any help would be appreciated.

---

### Post by cotcot on 2006-01-27
You could try with synaptic. Toggle mozilla mplayer and select completely remove.

---

### Post by MartinG on 2006-01-27
In synaptic, first fix broken packages (on the edit menu), then on the Status page look for packages marked residual configuration (I can't remember the exact wording) and remove them completely (right click on the package name to get the menu).

---

### Post by az on 2006-01-27
Do you have any funny sources in your list?

The openssh package install (postinstall) script seems to be broken.  It seems to have a typo.  Or one of it's dependancies is from another source than ubuntu and does not behave in the way it is supposed to.

"Setting up openssh-server (4.1p1-7ubuntu4) ...
Creating SSH2 RSA key; this may take some time ...illegal option -- f
Usage: ssh-keygen [options] [key1 key2 ...]"


Apt will be stuck until this is fixed.  You can try to remove the openssh-server package using dpkg.  You can also try to fix the install script. (/var/lib/dpkg? -  I am not at home and I do not remember exactly the path to the scripts)

---

