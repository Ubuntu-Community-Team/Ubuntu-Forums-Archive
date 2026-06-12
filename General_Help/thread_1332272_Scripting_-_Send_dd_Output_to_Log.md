---
title: "Scripting - Send dd Output to Log"
date: 2009-11-20
forum: General Help
---

### Post by SuperDodge on 2009-11-20
I have a homebuilt NAS that is running Ubuntu from a Compact Flash card.  On a weekly basis I have cron execute a script to use dd to back up the MBR and the system partition of the Compact Flash card in case of a crash later.

I am trying to update my script so that it will log all the work done during it's execute and e-mail it to me.  Everything is being logged except the output from the dd command itself.

Here is what I am doing, why is this not working?

dd if=xx of=xx >> logfile.log

This methodology works for every other command run in the script, but not for either of the dd lines.

Any ideas?

---

### Post by Locutus_of_Borg on 2009-11-20
change dd command to end in 2> log

e.g.

dd if=xx of=xx 2> logfile.log

---

### Post by John Bean on 2009-11-20
I haven't tried but perhaps the output is on stderr rather than stdout. You could try redirecting stderr to stdout ([FONT=monospace][/FONT]2>&1) before redirecting stdout to the logfile as you've already done and see what happens.

---

### Post by lmarmisa on 2009-11-20
You are redirecting the standard output of the command to logfile.log.

But the problem is the standard output is empty.

Try to modify your command in this way

**dd if=xx 2>> logfile.log | tee yy.dd | xxd >> logfile.log**

I suggest you to use xxd because it is not a good idea to add binary information to your log file.

I hope that this information will be usefull for you.

Best regards,

Luis

---

### Post by SuperDodge on 2009-11-20
This worked great guys.  Thanks for the help.

I guess I need to read up on the difference between STDOUT AND STDERR since I have no idea what you guys are talking about.

---

