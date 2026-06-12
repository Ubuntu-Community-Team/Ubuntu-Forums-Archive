---
title: "Run script at boot"
date: 2010-05-02
forum: General Help
---

### Post by anton_pm on 2010-05-02
OK,

So the default mediatomb script isn't starting anything for me or even logging so kind of hard to diagnose.

Created the following basic script:

root@anton-desktop:/etc/init.d# cat mediatomb2
#/bin/bash

mediatomb -u anton -c /home/anton/.mediatomb/config.xml -d --logfile /home/anton/.mediatomb/mediatomb.log 
root@anton-desktop:/etc/init.d# 

This starts mediatomb fine when running manually:

root@anton-desktop:/etc/init.d# ./mediatomb2 
root@anton-desktop:/etc/init.d# ps -efww |grep mediatomb
anton     1577     1  0 20:24 ?        00:00:00 mediatomb -u anton -c /home/anton/.mediatomb/config.xml -d --logfile /home/anton/.mediatomb/mediatomb.log


Added it rc using:

root@anton-desktop:/etc/init.d# update-rc.d -f mediatomb2 defaults
update-rc.d: warning: /etc/init.d/mediatomb2 missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/mediatomb2 ...
   /etc/rc0.d/K20mediatomb2 -> ../init.d/mediatomb2
   /etc/rc1.d/K20mediatomb2 -> ../init.d/mediatomb2
   /etc/rc6.d/K20mediatomb2 -> ../init.d/mediatomb2
   /etc/rc2.d/S20mediatomb2 -> ../init.d/mediatomb2
   /etc/rc3.d/S20mediatomb2 -> ../init.d/mediatomb2
   /etc/rc4.d/S20mediatomb2 -> ../init.d/mediatomb2
   /etc/rc5.d/S20mediatomb2 -> ../init.d/mediatomb2
root@anton-desktop:/etc/init.d# 


Reboot and nothing. Disabled the default mediatomb script using update-rc.d and also set NO_START="yes" in /etc/default/mediatomb

Not sure where else to go from here or which logs to check to see if there's some errors loading the script at boot. Nothing in any mediatomb.log

Would be great to find a way to debug this if anyone knows.

Running 10.04 here, 64-bit distro

Cheers

Anton

---

### Post by renkinjutsu on 2010-05-02
put the script in /etc/rc.local and make the rc.local file executable.

---

### Post by krismatth3 on 2010-05-02
To expand on what renkinjutsu said, just placing a file in /etc/init.d will not make it be magically executed at startup - it has to be symlinked to from the current runlevel in a specific syntax - see the links in /etc/rc2.d/ for example.

But by far the easiest solution is to just put what you want in /etc/rc.local

---

### Post by anton_pm on 2010-05-04
Thanks for getting back to me. I will try that out.

---

### Post by StuartN on 2010-05-04
> **anton_pm said:**
> Thanks for getting back to me. I will try that out.

As per **man 5 crontab** you can use **@reboot** in you crontab to execute something at each reboot.

---

### Post by anton_pm on 2010-05-04
@krismatth3

root@anton-desktop:/etc/init.d# update-rc.d -f mediatomb2 defaults
update-rc.d: warning: /etc/init.d/mediatomb2 missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Adding system startup for /etc/init.d/mediatomb2 ...
/etc/rc0.d/K20mediatomb2 -> ../init.d/mediatomb2
/etc/rc1.d/K20mediatomb2 -> ../init.d/mediatomb2
/etc/rc6.d/K20mediatomb2 -> ../init.d/mediatomb2
/etc/rc2.d/S20mediatomb2 -> ../init.d/mediatomb2
/etc/rc3.d/S20mediatomb2 -> ../init.d/mediatomb2
/etc/rc4.d/S20mediatomb2 -> ../init.d/mediatomb2
/etc/rc5.d/S20mediatomb2 -> ../init.d/mediatomb2
root@anton-desktop:/etc/init.d# 

Is that not me putting symlinks in to all run-levels?

Cheers,

Anton

---

### Post by anton_pm on 2010-05-04
Tried the following:

```

anton@anton-desktop:~$ cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mediatomb -u anton -c /home/anton/.mediatomb/config.xml -d --logfile /home/anton/.mediatomb/mediatomb.log

exit 0



```

```

anton@anton-desktop:~$ cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/etc/init.d/mediatomb2

exit 0



```

where mediatomb2 refers to the script in the first post

Neither of these worked - nothing in mediatomb log to show it attempting to start, no process. Calling 

```


sh rc.local 


```

Works fine in both instances.

I'm not sure why neither of the approaches I've tried fail. I have symlinks in all rc.* dirs as created by update-rc.d and there's an entry in rc.local. Removed symlinks from rc.* in case there was a conflict there, but mediatomb allows multiple instances, so unlikely.

---

### Post by icco on 2010-05-04
I'm having the same issue as you are. update-rc.d does exactly what these guys were asking you to do, and is the appropriate tool, at least it was as of 9.10. I heard rumors of ubuntu switching from sysvinit to upstart. 

I did some research and it looks like they actually switched in 6.10: [http://www.linux.com/archive/feed/57213](http://www.linux.com/archive/feed/57213)

I wasn't able to find it much help, but there is [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

### Post by StuartN on 2010-05-04
> **anton_pm said:**
> Tried the following:
```
mediatomb -u anton -c /home/anton/.mediatomb/config.xml -d --logfile /home/anton/.mediatomb/mediatomb.log
```

Doesn't this assume that the command mediatomb is in the path available to the cron process, an assumption that may not be valid? If so, then adding the full path should work.

---

### Post by anton_pm on 2010-05-04
@StuartN - I don't think cron would need to see these if they're launched at boot. The scripts all work, it's just interesting that they're not being called.

---

### Post by StuartN on 2010-05-04
> **anton_pm said:**
> @StuartN - I don't think cron would need to see these if they're launched at boot. The scripts all work, it's just interesting that they're not being called.

Sorry, my typing error. I meant the shell (not cron) can not be assumed to share your path, and the command within the script should be absolute.

---

### Post by sisco311 on 2010-05-04
> **icco said:**
> I'm having the same issue as you are. update-rc.d does exactly what these guys were asking you to do, and is the appropriate tool, at least it was as of 9.10. I heard rumors of ubuntu switching from sysvinit to upstart. 

I did some research and it looks like they actually switched in 6.10: [http://www.linux.com/archive/feed/57213](http://www.linux.com/archive/feed/57213)

I wasn't able to find it much help, but there is [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

Yep, that's true.

@OP
write an Upstart job or try:
```

cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**sleep 10**
/etc/init.d/mediatomb2

exit 0
```

---

### Post by anton_pm on 2010-05-04
> **sisco311 said:**
> Yep, that's true.

@OP
write an Upstart job or try:
```

cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**sleep 10**
/etc/init.d/mediatomb2

exit 0
```

Yeah, tried the second option, but without the sleep which shouldn't make too much difference.

---

### Post by anton_pm on 2010-05-04
> **StuartN said:**
> Sorry, my typing error. I meant the shell (not cron) can not be assumed to share your path, and the command within the script should be absolute.

Not a bad shout, just tried this using rc.local and update-rc, but still no joy. Other apps that aren't standard to the base install like mysql are starting on boot fine.

---

### Post by sisco311 on 2010-05-04
> **anton_pm said:**
> Yeah, tried the second option, but without the sleep which shouldn't make too much difference.

You missed icco's reply. Upstart is **not** synchronous.
[http://en.wikipedia.org/wiki/Upstart](http://en.wikipedia.org/wiki/Upstart)

---

### Post by anton_pm on 2010-05-04
> **sisco311 said:**
> You missed icco's reply. Upstart is **not** synchronous.
[http://en.wikipedia.org/wiki/Upstart](http://en.wikipedia.org/wiki/Upstart)

Yeah, I saw it, been having a read. I meant that I tried his rc.local entry. I just don't understand why these sysvinit things I'm trying are failing. Is this something forcing me to upstart? Are they trying to make  sysvinit redundant by making nothing added to it work?

---

### Post by sisco311 on 2010-05-04
> **anton_pm said:**
> I just don't understand why these sysvinit things I'm trying are failing.

Ubuntu uses Upstart since 6.10(Edgy Eft). Back in the old days, backward compatibility with sysvinit was an explicit design goal, but come on it's 2010. While I do understand that the Upstart documentation is incomplete, it's not so hard to rewrite a System-V style init script to an Upstart job. Well, I may be be wrong.

---

### Post by ezsit on 2010-05-04
Plymouth is now used, new as of 10.04. Plymouth is the new boot up system and is different from both upstart and the old sysvinit. This will require you to learn the details of Plymouth to debug why your startup scripts are not called.

---

### Post by anton_pm on 2010-05-04
> **sisco311 said:**
> Ubuntu uses Upstart since 6.10(Edgy Eft). Back in the old days, backward compatibility with sysvinit was an explicit design goal, but come on it's 2010. While I do understand that the Upstart documentation is incomplete, it's not so hard to rewrite a System-V style init script to an Upstart job. Well, I may be be wrong.

It just seems odd that if they don't intend for you to use sysvinit that it's even there and it allows other apps to install startup scripts to it. Seems slightly childish to just stop you using it and not really add any warning. 

It seems as though you have experience of upstart, all I need to do is run the mentioned mediatomb command:

```
 exec /usr/bin/mediatomb -u anton -c /home/anton/.mediatomb/config.xml -d --logfile /home/anton/.mediatomb/mediatomb.log
```

What is an appropriate "start on" command to get this going, nothing I've tried works. Using 

```
start mediatomb
```

Is working fine when the system has booted

---

### Post by anton_pm on 2010-05-04
> **ezsit said:**
> Plymouth is now used, new as of 10.04. Plymouth is the new boot up system and is different from both upstart and the old sysvinit. This will require you to learn the details of Plymouth to debug why your startup scripts are not called.

Jesus, they're not making this very easy.

---

### Post by sisco311 on 2010-05-05
hmmm, I just installed mediatomb. You can set the user & group in /etc/default/mediatomb & you have to edit the DAEMON_ARGS variable in the /etc/init.d/mediatomb init script:
```
...
DAEMON_ARGS="-c **/home/anton/.mediatomb/config.xml** -d -u $USER -g $GROUP -P $PIDFILE -l $LOGFILE $INTERFACE_ARG $OPTIONS"

```This is clearly a BUG, the init script should read the location of the config file from /etc/default/mediatomb.

---

### Post by anton_pm on 2010-05-05
> This is clearly a BUG, the init script should read the location of the config file from /etc/default/mediatomb.

Definitely is and seems well known. I'm trying to get around this. I think the best way is to remove the entry from rc.* using update-rc so that script isn't called and then maybe use upstart.

Do you know what I would put in an upstart conf to make it load on boot?

---

### Post by sisco311 on 2010-05-05
> **anton_pm said:**
> Definitely is and seems well known. I'm trying to get around this. I think the best way is to remove the entry from rc.* using update-rc so that script isn't called and then maybe use upstart.

Do you know what I would put in an upstart conf to make it load on boot?

This one works for me:
/etc/init/mediatomb.conf:
```
# mediatomb
#

description     "mediatomb"
author          "sisco311"

start on net-device-up

stop on runlevel [016]

emits starting-mediatomb


script
  mediatomb -u sisco -g sisco -m /home/sisco
end script

```

---

### Post by anton_pm on 2010-05-05
> This one works for me:
/etc/init/mediatomb.conf:

And for me too :) 

I guess I need to learn more about upstart.

---

