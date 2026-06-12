---
title: "environment variable defined but not in profile/bashrc"
date: 2009-08-04
forum: General Help
---

### Post by reader4 on 2009-08-04
Hi all,

I am having the hardest time solving this one.  When I open a new terminal, the environment variable MATLAB_JAVA is set.  The problem is that I don't want it, but cannot figure out why it is getting set.  I've searched ~/.bashrc, ~/.profile, /etc/profile and /etc/bash.bashrc but that variable is never set in those files.  If I unset the variable, it is reset when I open a new terminal.  What else could cause this to be set be default?  Thanks in advance!

---

### Post by Brandon Williams on 2009-08-04
Other places to check: .bash_login and .bash_profile both take precedence over .profile, so check there if either one of those files exists. The directory /etc/profile.d/ can contain any number of init scripts that get sourced by /etc/profile when it is read during bash init. Some packages will drop files there, so that's another good place to look.

---

### Post by Glyndwr on 2009-08-04
I'd try grep

1. In your home directory 
$ grep MATLAB_JAVA .*

2. In /etc
$ sudo grep MATLAB_JAVA *

3. If those don't grep everything
$ sudo find / -type f | xargs grep MATLAB_JAVA

---

### Post by reader4 on 2009-08-07
No luck with grep.  If I open a terminal as a different user (ie, sudo xterm) then the variable is not set, which implies something on the user side is setting this variable but I can't find it.

The other strange thing I noticed is that I have another variable, XLIB_SKIP_ARGB_VISUALS, which *is* set in my .bashrc file.  When I 'sudo xterm' it is then set in the new terminal but is never set in the .bashrc in /root or in any of the /etc/... files.  Getting more confused the more I try to figure this out... any advice?

---

### Post by reader4 on 2009-08-13
Are these the only places this variable might be set?  Is there anyway I can see the operation of a terminal startup to find out when/how this is getting set?

---

