---
title: "annoying messages in /var/log/messages"
date: 2006-05-07
forum: General Help
---

### Post by aparsons on 2006-05-07
I keep getting these messages in /var/log/messages and they are filling my log rather quickly.  I have NO IDEA what they are:

> 
May  7 06:47:02 localhost syslogd 1.4.1#17ubuntu3: restart.
May  7 07:07:02 localhost -- MARK --
May  7 07:27:02 localhost -- MARK --
May  7 07:47:02 localhost -- MARK --
May  7 08:07:02 localhost -- MARK --
May  7 08:27:03 localhost -- MARK --
May  7 08:47:03 localhost -- MARK --
May  7 09:07:03 localhost -- MARK --
May  7 09:27:03 localhost -- MARK --
May  7 09:47:03 localhost -- MARK --
May  7 10:07:03 localhost -- MARK --
May  7 10:27:03 localhost -- MARK --
May  7 10:47:03 localhost -- MARK --
May  7 11:07:03 localhost -- MARK --
May  7 11:27:03 localhost -- MARK --
May  7 11:47:03 localhost -- MARK --
May  7 12:07:03 localhost -- MARK --
May  7 12:27:03 localhost -- MARK --


---

### Post by towsonu2003 on 2006-05-07
just ignore them. I forgot their function, but nothing to worry about. Here is what it says in man syslogd > -m interval
              The syslogd logs a mark timestamp regularly.  The default inter&#8208;
              val  between  two  --  MARK -- lines is 20 minutes.  This can be
              changed with this option.  Setting the interval to zero turns it
              off entirely.

---

