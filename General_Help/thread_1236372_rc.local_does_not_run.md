---
title: "rc.local does not run"
date: 2009-08-10
forum: General Help
---

### Post by larryalk on 2009-08-10
I just noticed that rc.local never appears in /var/log/syslog as it should.  I don't think it is running.

The last line in my rc.local has:
echo "rc.local: finished without error `date`" >>/var/log/syslog
but that message never appears suggesting that /etc/rc.local never runs.

I also noticed that gpm does not restart as it should by this line in my /etc/rc.local.
/etc/init.d/gpm restart

As you can see it's fully executable:
ls -l rc.local
-rwxr-xr-x 1 root root 2.7K 2009-08-10 05:29 rc.local

I can run it by hand and it appears in syslog with either
/etc/init.d/rc.local start
and
/etc/rc.local
but it does not run when I boot up.

What do you think is wrong?

Larryalk

---

### Post by Brandon Williams on 2009-08-11
Double check to make sure that you have all the expected symlinks to /etc/init.d/rc.local in the /etc/rc*.d directories. I have S99rc.local links for rc2.d, rc3.d, rc4.d, and rc5.d (though only the rc2.d symlink is really important in a standard Debian-based distro like Ubuntu).

---

### Post by martinbaselier on 2009-08-11
I've just checked and I see no reference in /var/syslog to rc.local either, though I'm very sure it's running. Do you have statements after exit 0 ? These statements won't be executed.

---

### Post by larryalk on 2009-08-12
I also have have S99rc.local links for rc2.d, rc3.d, rc4.d, and rc5.d.

Also there is nothing after exit 0 in /etc/rc.local.

I inserted another message to quickly check to see if /etc/rc.local actually ran.  So far I have rebooted and the message did not run.

The line above exit 0 in /etc/rc.local is:
echo "rc.local: finished without error `date`" >>/etc/syslog

BTW, syslog.d is running in ps ax.

Larry

---

### Post by larryalk on 2009-08-12
The problem has been found.

If a command in /etc/rc.local finishes with a return code other 0, rc.local will abort and therefore no entry is made in /var/log/syslog.

That was not mentioned in the brochure!

In my case, near the bottom of rc.local I call
hdparm to turn of the second drive after 21 minutes of inactivity with the command
hdparm -S255 /dev/sdb

If there is no physical sdb drive in the machine,
then hdparm returns an error and rc.local aborts.

Maybe I can 'grep hdb mtable' and not run the command if hdb is not there.

I now have a line just before exit 0 that says:
echo Finished with rc.local.
So I can test rc.local by running ./rc.local
by hand and if the "Finished" line does not appear I know that something aborted rc.local.

I'll put some other "flag" lines in also but at least now I know what to look for.

Larryalk

---

### Post by Brandon Williams on 2009-08-12
The first line of /etc/rc.local is:
```
#!/bin/sh -e
```
The -e means that dash should exit immediately if an untested command exit with a non-zero return. If you don't want it to exit when you hdparm call fails, then simply test for success:
```
if ! hdparm -S255 /dev/sdb
then
    echo "hdparm failed" >&2
fi
```

---

