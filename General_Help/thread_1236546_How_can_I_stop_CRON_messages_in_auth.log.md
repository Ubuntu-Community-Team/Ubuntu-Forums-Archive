---
title: "How can I stop CRON messages in auth.log?"
date: 2009-08-10
forum: General Help
---

### Post by iandol on 2009-08-10
Hi, my auth.log has lots of messages triggered by authentication of cron (and dbus) each time cron runs one of its scheduled actions:

Aug  7 08:09:01 ianu CRON[29203]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  7 08:09:01 ianu dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=4418 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.348" (uid=0 pid=29203 comm="/USR/SBIN/CRON "))

This repetitive information obscures useful entries and I wondered if there was an easy way to stop these messages in auth.log?

Thanks in advance for any help!

---

### Post by SyL on 2009-08-11
This might answer your question:
[http://www.linuxquestions.org/questions/linux-software-2/removing-cron-entries-from-auth.log-449010/](http://www.linuxquestions.org/questions/linux-software-2/removing-cron-entries-from-auth.log-449010/)

> Go to the cron.hourly directory and edit the files.  For example:
/usr/sbin/mcelog --ignorenodev --filter >> /var/log/mcelog

Removing the ">>/var/log/mcelog" will stop the logging.OR

Add a filter to syslog-ng conf file:
```
# all messages from the auth and authpriv facilities
filter f_auth { facility(auth, authpriv);};

#filter the CRON messages
filter f_cron_msgs { not match("CRON*"); };


# auth,authpriv.*                 /var/log/auth.log
# + filter the CRON messages out
log {
        source(s_all);
        filter(f_auth);
        filter(f_cron_msgs);
        destination(df_auth);
};
```




HTH

---

### Post by iandol on 2009-08-11
Thanks for your answer. I had seen that page on my searches but couldn't apply the information usefully. For example, update-motd in /etc/cron.d has the following:

```
*/30 * * * *	root	[ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null
```

I don't know enough about linux to know why this command is repeated twice, once in brackets and once redirected to /dev/null/ -- but most of the commands in cron do not redirect output to logs by default, I assume the syslog deamon deals with this internally. Should I redirect output in both bits to /dev/null? What about other commands that don't redirect anywhere?

Also, I don't see a syslog-ng conf file (it is not part of the default ubuntu IINM), and I didn't see anything in "man syslog.conf" that immediately jumped out at me as useful.

---

### Post by dcstar on 2009-08-12
> **iandol said:**
> Hi, my auth.log has lots of messages triggered by authentication of cron (and dbus) each time cron runs one of its scheduled actions:

Aug  7 08:09:01 ianu CRON[29203]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug  7 08:09:01 ianu dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.57" (uid=1000 pid=4418 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.348" (uid=0 pid=29203 comm="/USR/SBIN/CRON "))

This repetitive information obscures useful entries and I wondered if there was an easy way to stop these messages in auth.log?

Thanks in advance for any help!

The auth.log file is to show **every** root level access to your system, **every** entry is supposed to be there otherwise the whole log file is basically useless.

---

### Post by iandol on 2009-08-12
Thanks, David. 

So instead of source-filtering then, does anyone know of a good GUI log viewer that allows filtering? The one that comes with Jaunty is pretty poor (no filtering, no auto-scrolling etc.).

Or, what would be the correct syslog.conf entry that would also log ssh daemon information contained in auth.log to a new ssh.log? I still want to log to auth.log, so don't want to change the logging options of the sshd.

Thanks again.

---

