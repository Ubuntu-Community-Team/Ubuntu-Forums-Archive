---
title: "pcscd generating loads of unwanted syslog messages"
date: 2010-05-04
forum: General Help
---

### Post by abitwise on 2010-05-04
If you have a problem pcscd generating loads of unwanted syslog messages, here is a solution for you. One example of messages you may find in syslog:

May  4 16:44:08 machine1 pcscd: ifdwrapper.c:638:IFDControl() Card not transacted: 612
May  4 16:44:08 machine1 pcscd: commands.c:954:CmdGetSlotStatus Card absent or mute
May  4 16:45:09 machine1 pcscd: last message repeated 149 times
May  4 16:46:10 machine1 pcscd: last message repeated 151 times
May  4 16:47:11 machine1 pcscd: last message repeated 152 times
May  4 16:48:12 machine1 pcscd: last message repeated 151 times

Solution:
1. Open a terminal, make a root session (sudo -i).
2. Go to "/etc/default/" and look for a file called pcscd.
3. If the file is not there, generate it like this: echo "" > pcscd
4. Edit /etc/default/pcscd file (use nano or something else you like) and add a line: DAEMON_ARGS="--critical"
   You may add empty line in the end just in case.
5. Save and exit editor
6. And restart service: sudo /etc/init.d/pcscd restart
   Or if this doesnt work use these two commands:
   sudo /etc/init.d/pcscd stop
   sudo /etc/init.d/pcscd start


I hope this helps someone :popcorn:

---

### Post by crazyboy on 2012-02-04
Hi abitwise, this help me.... Thanks

---

### Post by hceuterpe on 2013-05-04
Sorry to dig up a rather old forum.  You are using an SCM MIcro reader in all likelihood?  If this your only smart card reader.  If so, remove the ccid package, and use the custom bundle from SCM ( scmccid.bundle).
[http://support.identive-infrastructure.com/downloads.php?lang=en&open=driver](http://support.identive-infrastructure.com/downloads.php?lang=en&open=driver)
Look for Linux based, (scmccid).

---

### Post by wildmanne39 on 2013-05-04
Thanks for sharing! old thead closed!

---

