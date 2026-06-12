---
title: "Synaptic acting funny"
date: 2006-02-12
forum: General Help
---

### Post by flummoxed on 2006-02-12
I've tried to set up the Universe and MultiVerse repositories, but for some reason it's giving me this error everytime i start synaptic:

```
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ca.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

Anyone have any idea what's wrong?

---

### Post by heimo on 2006-02-12
Does it work if you change ca to us? At least at the moment  [http://ca.archive.ubuntu.com/]("http://ca.archive.ubuntu.com/") doesn't respond. Put the address in your browser and see if it's the same for you.

---

### Post by nanotube on 2006-02-12
did you try hitting the "reload" button in synaptic, once synaptic is started? and if so, does is successfully do that?

if that fails as well, then try editing your /etc/apt/sources.list file, and remove the "ca." prefix from your servers. that is, instead of 
[http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) <more stuff>
make them look like
[http://archive.ubuntu.com](http://archive.ubuntu.com) <more stuff>
and then open up synaptic and try "reload" again.

---

### Post by bruce205 on 2006-02-12
Sorry no clue Flum as I just installed Ubuntu and am total newbie. I just thought I would borrow your title as I am getting this error message when I reload Synaptic:
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
Any clue ?   and good luck with your problem Flum

---

### Post by AgenT on 2006-02-12
If you have the correct GPG key and are still having problems this **fix** should help.

There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this: 
 Back up the sources.list with this command: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
```  Then edit the sources.list by typing ```
sudo gedit /etc/apt/sources.list
``` and delete everything.  
```
 sudo apt-get update 
```with your empty repositories list. 
Finally, ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
``` ```
sudo apt-get update
``` [Source]("http://www.psychocats.net/linux/sources.php")

---

### Post by flummoxed on 2006-02-12
Thanks a lot heimo and nanotube, it worked. :D

---

