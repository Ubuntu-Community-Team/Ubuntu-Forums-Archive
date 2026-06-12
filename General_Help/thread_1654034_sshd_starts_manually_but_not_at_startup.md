---
title: "sshd starts manually but not at startup"
date: 2010-12-27
forum: General Help
---

### Post by hawkmage on 2010-12-27
Not sure if this belongs here or in the upgrade forum but since the upgrade went OK I figured I would post this here.  I come from a RedHat background and am not too familiar with the Ubuntu/Debian way of dealing with service startup so this may be simple. 

I was running 10.04 LTS on a Sony Vaio and did a distribution upgrade to  10.10.  When running 10.04 LTS the sshd daemon started on boot and I was able  to ssh into the PC.  

Now that did the update I can start the daemon using the command "sudo  /etc/init.d/ssh start" but it doesn't start when the systems boots.  

I even tried creating the entries in the /etc/rc.#.d directories like this:
/etc/rc0.d/K20ssh -> ../init.d/ssh
/etc/rc1.d/K20ssh -> ../init.d/ssh
/etc/rc2.d/S20ssh -> ../init.d/ssh
/etc/rc3.d/S20ssh -> ../init.d/ssh
/etc/rc4.d/S20ssh -> ../init.d/ssh
/etc/rc5.d/S20ssh -> ../init.d/ssh
/etc/rc6.d/K20ssh -> ../init.d/ssh

I also tried removing and reinstalling openssh-server and that did not help either.

Any suggestions would be appreciated.

---

### Post by hawkmage on 2010-12-27
I have double checked the /etc/init/ssh.conf file for upstart and comparing the content and the stat info on of the file with a 10.10 system that is working and I can't find a difference.  

The upstart commands 'stop' and 'start' work to stop and start the sshd daemon.

---

### Post by hawkmage on 2010-12-28
I am trying to duplicate the issue, I have a VIrtualBox VM of Ubuntu 10.04 LTS that I have just created a snapshot of and I am doing the upgrade to 10.10.  I will report back with the results.

---

### Post by hawkmage on 2010-12-28
OK, I got to the bottom of the issue.  

I updated the ssh.conf file to output detailed debugging to a text file and this is what I got:
```
Auto configuration failed
1991:error:0E065068:configuration file routines:STR_COPY:variable has no value:conf_def.c:629:line 8
```After some googleing around the error in referance to openssl and its config file.  It had nothing to do with the ssh.conf upstart script at all.  It has to do with the /etc/ssl/openssl.cnf.  On line 8 of my /etc/ssl/openssl.cnf I had the line:
```
HOME                   = $ENV::HOME
```The new version of the sshd references this default openssl.cnf file.  Since there is no environment variable named HOME for it to use the it fails.  Once I set the line back to the default ssh starts up normally.

I just testes annother fix that will allow me to keep my openssl.cnf changes.  I change the ssh.conf file so that the "exec /usr/sbin/sshd" is in a script block like this:
```
script
    export HOME=/
    exec /usr/sbin/sshd
end script
```
This way the HOME variable is set.

---

### Post by NFblaze on 2010-12-28
Nice. Thanks for the update. Hopefully, someone else experiencing this problem can benefit.

---

### Post by hawkmage on 2010-12-28
No problem, I had to wrap my head around how upstart works to get the debug info I needed.

---

