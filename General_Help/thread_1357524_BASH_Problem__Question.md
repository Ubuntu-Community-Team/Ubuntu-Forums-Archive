---
title: "BASH Problem / Question"
date: 2009-12-17
forum: General Help
---

### Post by haraldmilz on 2009-12-17
Hi all,

Maybe someone is able to help:

Need to redirect the output of a command to a second command. Command-A executes a remote shell to another host, and outputs its results. Command-B displays a "dialog" with the outputs of Command-A.

Command-A Output:

Updating FileA
Updating FileB
Updating FileC
etc

It takes about a minute for the whole output to finish.

I've tried:

for p in `ssh [email]user@ip.ip.ip.ip[/email] /etc/cron.hourly/command`; do dialog --infobox "$p" 3 40;done

This actually prints out the dialog, but with all the output at once. I need something that will redirect the output in realtime. So I tried:

'ssh [email]user@ip.ip.ip.ip[/email] /etc/cron.hourly/command' | dialog --infobox "$?" 3 40

with no luck until now.

Can anyone give me a hint how to resolve this?

---

### Post by Tipo on 2009-12-17
Would you be able to print the output to a file with the `>` operator and then carry out your actions on the file?

---

### Post by haraldmilz on 2009-12-18
That wouldn't bring the realtime status. The whole process of the remote ssh procedure lasts about a minute, and I need to inform the user of the status of the process WHILE the process is running.

Is there any other option?

---

