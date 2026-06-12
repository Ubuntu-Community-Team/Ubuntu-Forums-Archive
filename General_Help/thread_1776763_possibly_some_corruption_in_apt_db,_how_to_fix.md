---
title: "possibly some corruption in apt db, how to fix ?"
date: 2011-06-06
forum: General Help
---

### Post by icarus74 on 2011-06-06
Hi,

Yesterday while installing Google-Talk plugin, my system went into
heavy swapping (too many apps open, and 2 builds runnings), and I had
to "switch-off" ungracefully. I think that act has caused some
corruption of the apt db. I am getting these errors. Can anyone advice
on what to do to fix these ?

Doing a "sudo apt-get clean; apt-get update" didn't seem to help, as I
still get this error in the end --

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList
/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Here are the other errors I got earlier...

icarus@optimus:~/Work$ sudo apt-get update
[sudo] password for bdutta:
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates InRelease
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
 Something wicked happened resolving 'security.ubuntu.com:http' (-5 -
No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg
 Something wicked happened resolving 'extras.ubuntu.com:http' (-5 -
No address associated with hostname)
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
 Something wicked happened resolving 'dl.google.com:http' (-5 - No
address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release.gpg
 Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5
- No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release
Ign [http://dl.google.com](http://dl.google.com) stable Release
...
W: Failed to fetch
[http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)
Something wicked happened resolving 'dl.google.com:http' (-5 - No
address associated with hostname)
W: Failed to fetch
[http://in.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Something
wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No
address associated with hostname)
W: Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)
Something wicked happened resolving 'security.ubuntu.com:http' (-5 -
No address associated with hostname)
W: Failed to fetch
[http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)
Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 -
No address associated with hostname)
E: Some index files failed to download. They have been ignored, or old
ones used instead.

icarus@optimus:~/Work$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
...
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 30.2 kB in 21s (1,397 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList
/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

cheers,
Icarus

---

### Post by 67GTA on 2011-06-06
Running ```
sudo rm /var/lib/apt/lists/* -vf
``` and ```
sudo apt-get update
``` should take care of this error. You may also have to run ```
sudo dpkg --configure -a 
``` to finish the last interrupted installation if it complains.

---

### Post by icarus74 on 2011-06-06
Thanks @67GTA. That solved/fixed my problem completely.

---

### Post by psychonelo on 2012-06-27
@67GTA: Thank you.

---

### Post by MUK3SH on 2012-08-22
sudo apt-get update
worked, solved the problem :)

---

