---
title: "cannot log to any user with 'su' but ok with ssh"
date: 2009-12-24
forum: General Help
---

### Post by benj.david on 2009-12-24
Hi all,
I have a really strange issue.
I have several accounts on my computer, and I can successfully log-in to these through ssh, BUT, I can't log-in using 'su' command !!

Ok, I do the following, as normal user 'ben':
$ ssh root@localhost         # I know this is bad, but I can't do 
                             # anything else with this bug
# usermod -U admin
# usermod -p `mkpasswd theadminpwd` admin
# exit
$ su admin
Password: 
su: Authentication failure
$

But I can log-in though ssh
$ ssh admin@localhost

Does anybody know what could here?

Thank you very much and mery christmas!
ben

---

### Post by benj.david on 2009-12-24
I solved the mystery !
/bin/su had lost hist 's' bit !!
# ls -lh /bin/su 
-rwxr-xr-x 1 root root 31K 2009-12-24 12:00 /bin/su
but should be :
# ls -lh /bin/su 
-rw**s**r-xr-x 1 root root 31K 2009-04-04 07:49 /bin/su

---

