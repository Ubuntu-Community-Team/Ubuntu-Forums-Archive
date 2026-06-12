---
title: "PSAD errors"
date: 2011-06-04
forum: General Help
---

### Post by Dalek Draco ON LINUX on 2011-06-04
Hi. 

I've recently installed PSAD and after updating it and running > sudo psad --fw-analyze I get 

> [+] Parsing iptables INPUT chain rules.
sh: /usr/bin/mail: Permission denied
[-] Errors found in firewall config.
    emailed to [email]dalekdraco@yahoo.com[/email]
[+] Results in /var/log/psad/fw_check
[+] Exiting.


When I read the fw_check log it says:
> You may just need to add a default logging rule to the INPUT chain on
    draco-laptop.  For more information, see the file "FW_HELP" in
    the psad sources directory or visit:

    [http://www.cipherdyne.org/psad/docs/fwconfig.html](http://www.cipherdyne.org/psad/docs/fwconfig.html)

Now I've googled the problem and to fix the error you apparently need to run:
>  [SIZE=1][COLOR=Black]sudo iptables -A FORWARD -j LOG[/COLOR][/SIZE]
  [SIZE=1][COLOR=Black]
[/COLOR][/SIZE]
[SIZE=1][COLOR=Black]sudo iptables -A INPUT -j LOG[/COLOR][/SIZE]


When I run --fw-analyze again it shows no errors. However when I reboot I get the original error on running the command. 

I'm slightly nooby still, all I've done is install psad and update it, and I assume I don't need to configure anything to make it work :P. 

Any help would be appreciated, cheers. p { margin-bottom: 0.21cm; }

---

### Post by Rubi1200 on 2011-06-05
Hi,
I don't use this application, but I hope this link will prove useful:
[http://bodhizazen.net/Tutorials/psad](http://bodhizazen.net/Tutorials/psad)

You might also be better asking this in the Security Discussions thread.

---

### Post by Dalek Draco ON LINUX on 2011-06-05
I uninstalled psad and reinstalled using that guide, I still have the same problem. Probably something basic that i'm doing wrong. I'll move it to the security thread. Thanks for your help.

---

