---
title: "What is the counterpart of csh.login.local for bash?"
date: 2009-11-08
forum: General Help
---

### Post by iamgzy on 2009-11-08
Thanks in advance !
Try to install Oracle 10g on my lovely Ubuntu, following the instruction from oracle website,
but find following lines:

-------------------------
**For RHEL4,** use the following: 
                                                                      cat >> /etc/profile <<EOF
if [ \$USER = "oracle" ]; then 
 if [ \$SHELL = "/bin/ksh" ]; then
 ulimit -p 16384
 ulimit -n 65536
 else
 ulimit -u 16384 -n 65536
 fi
 umask 022
fi
EOF

cat >> /etc/csh.login <<EOF
if ( \$USER == "oracle" ) then
 limit maxproc 16384
 limit descriptors 65536
 umask 022
endif
EOF
                                                                     **For SLES 9,** use the following: 
                                                                      cat >> /etc/profile.local <<EOF
if [ \$USER = "oracle" ]; then 
 if [ \$SHELL = "/bin/ksh" ]; then
 ulimit -p 16384
 ulimit -n 65536
 else
 ulimit -u 16384 -n 65536
 fi
 umask 022
fi
EOF

cat >> /etc/csh.login.local <<EOF
if ( \$USER == "oracle" ) then
 limit maxproc 16384
 limit descriptors 65536
 umask 022
endif
EOF
-----------------------------------

[FONT=Times New Roman]I found "profile" but i think default shell in Ubuntu should be bash (or maybe I can install tcsh, but the question is how can I find counterparts for csh.login.local for either bash or tcsh?
Thanks a lot[/FONT]
[FONT=Times New Roman] [/FONT]

---

### Post by efflandt on 2009-11-09
Type **man bash** in a terminal, then hit enter and see what it shows for invocation files used by bash under what conditions.  The scroll keys work or **q** quits.  Or install and use another shell of your choice.

---

