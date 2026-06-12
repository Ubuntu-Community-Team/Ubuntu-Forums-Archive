---
title: "specify sender name using exim4 from script?"
date: 2009-12-04
forum: General Help
---

### Post by negativ on 2009-12-04
I am running a cron job that needs to send email to my ISP account.  I have exim4 set up to use gmail as a mail relay.

When the cron job sends email, the sender field says "root" and shows the name of the gmail account as the email address.

I would like to change it so that it doesn't say "root" but instead says something more meaningful like "automated alert" or some such.

How can I do this?

---

### Post by negativ on 2009-12-04
boink

---

### Post by StuartN on 2009-12-04
> **negativ said:**
> I would like to change it so that it doesn't say "root" but instead says something more meaningful like "automated alert" or some such.

```
-F <string>

Set the sender's full name for use when a locally-generated message is being accepted. In the absence of this option, the user's gecos entry from the password file is used. As users are generally permitted to alter their gecos entries, no security considerations are involved. White space between -F and the <string> is optional.
```

---

### Post by negativ on 2009-12-04
> **StuartN said:**
> ```
-F <string>

Set the sender's full name for use when a locally-generated message is being accepted. In the absence of this option, the user's gecos entry from the password file is used. As users are generally permitted to alter their gecos entries, no security considerations are involved. White space between -F and the <string> is optional.
```

I'm using mail (from the GNU mailutils) to send the emails, and -F is a parameter for exim, which complains if you invoke it directly.  I am at a loss to understand how to pass that parameter to exim.

---

### Post by StuartN on 2009-12-04
> **negativ said:**
> I'm using mail (from the GNU mailutils) to send the emails, and -F is a parameter for exim, which complains if you invoke it directly.  I am at a loss to understand how to pass that parameter to exim.

I know you can **exim -F "Friendly name" -i <recipient>** from the command line, but I do not know how your user agent would pass the parameter on. Man exim isn't clear on that point, but it might be buried in [http://wiki.debian.org/PkgExim4](http://wiki.debian.org/PkgExim4)

Edit: Actually, man mail says to use -- sendmail-options

---

### Post by StuartN on 2009-12-05
This works.

Cron sends the command output by mail, but only if there is output. If you redirect your command output and error messages into a mail command, then that is the only mail message sent.

In crontab -e you can change the mail commandline like this (2>&1 appends stderr to stdout):

```
* 4 * * * mycmd | mail -s "Sent by Stuart in cron" stuart@somewhere.else -- "-F Friendly\ Sender\ Name" 2>&1
```

---

