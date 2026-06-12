---
title: "Firestarter: Failed to open system log"
date: 2011-05-04
forum: General Help
---

### Post by Chethan S on 2011-05-04
I made a fresh installation of Natty and went ahead with firestarter  installation as I had it since earlier versions of Ubuntu. To  automatically start firestarter and to avoid entering password each  time, I edited sudoers file as instructed in the  firestarter site and now I get this error each time I start firestarter.  As said here no event logs like "hit from ... detected" is shown now.  How can I set it right?

---

### Post by Marric on 2011-05-05
Hi,

there might be a solution here:

[https://bugs.launchpad.net/ubuntu/+bug/776361](https://bugs.launchpad.net/ubuntu/+bug/776361)

> When installing (or upgrading) to 11.04 syslogd is upgraded to  rsyslog.  This uses the file /etc/rsyslog.conf 
which references the file  configuration /etc/rsyslog.d/50-default.conf.
 You can edit this file and change the lines commented out that create the relevant logfile
 
#*.=info;*.=notice;*.=warn;\
# auth,authpriv.none;\
# cron,daemon.none;\
# mail,news.none -/var/log/messages
 
to
 
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none -/var/log/messages
 
and then restart rsyslog or reboot
 
Note: As rsyslog is referencing the directory /etc/rsyslog.d/ you  could just put a new file in that location that would be included in the  configuration so as not to fall foul of an ubuntu upgrade at a later  date.  The choice is yours.


---

### Post by Maximiliano Gasparini on 2011-05-06
Works Great! Thanks!!!

---

### Post by denisk on 2011-06-03
Thank you! Worked for me as well (after rebooting)

---

### Post by 4h98fna on 2011-06-08
Thank you. 
It works for me too, after restart rsyslog.

---

### Post by terminataaar on 2011-06-15
> restart rsyslog:

```
$ sudo service rsyslog restart
```

---

### Post by buckeyered80 on 2011-07-02
Worked for me also. But I had to use a ```
sudo restart rsyslog
```

---

### Post by wildmanne39 on 2011-07-02
Hi, firestarter is outdated, it is recommended for people to use gufw.

---

### Post by mundoalinks on 2011-07-06
thanks [COLOR=Black][wildmanne]("http://ubuntuforums.org/member.php?u=508533")[/COLOR] ill try it out

---

### Post by OttifantSir on 2011-12-01
If Firestarter is so outdated, and GUFW is the new way, then why doesn't GUFW work AT ALL on ANY of my 8 computers, ranging from P3s to QuadCores and Phenoms? I've tried it first for the last 4 or 5 releases of Ubuntu, and it JUST DOESN'T WORK! I've tried so many different ways of making rules with it, mainly trying every combination I can think of in General and Advanced view to open ports for Deluge. No go, no how.

I don't like Unity, but at least it's working as it should, which gufw isn't. Only way I would tell anyone to use gufw was if I wanted them to move to another distro or to (shock!) Windows or (horror!) Mac.

As I said, I don't like Unity, but it's evident that a lot of thought has gone into making it. I wish just a miniscule fraction of that effort had gone into making gufw ACTUALLY WORK!

---

### Post by 3rdalbum on 2011-12-01
> **OttifantSir said:**
> If Firestarter is so outdated, and GUFW is the new way, then why doesn't GUFW work AT ALL on ANY of my 8 computers, ranging from P3s to QuadCores and Phenoms? I've tried it first for the last 4 or 5 releases of Ubuntu, and it JUST DOESN'T WORK! I've tried so many different ways of making rules with it, mainly trying every combination I can think of in General and Advanced view to open ports for Deluge.

You shouldn't have to "open ports" for Deluge on your computer. By default, Ubuntu comes with NO ports blocked. When you run Deluge, it should be able to accept incoming connections without you having to change any configuration.

However, I suspect you're behind another firewall (such as one built into your router/modem) that is blocking the incoming connections.

In other words, gUFW is working perfectly. It's your OTHER firewall that's blocking incoming connections.

---

### Post by dbyrd on 2012-09-19
Taking **Chethan**'s advice I created a separate file called firestarter.rsyslog.d.conf with the following contents.

# use one of the following to commands to restart rsyslog.d
# sudo service rsyslog restart
# or sudo restart rsyslog

*.=info;*.=notice;*.=warn;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages

I have also copied this new conf file to my Ubuntu One cloud drive to allow me to simply run a bash script to help me with subsequent Ubuntu setups and upgrades etc.

sudo cp firestarter.rsyslog.d.conf /etc/rsyslog.d
sudo service rsyslog restart

---

