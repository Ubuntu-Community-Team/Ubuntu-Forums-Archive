---
title: "Upgrade failure"
date: 2012-04-24
forum: General Help
---

### Post by Lara_Baker on 2012-04-24
[SIZE=2]When I checked the box to do a lot of upgrades (~365MB), after entering my admin pw, I got the message in a dialog box.  My only option is to close the dialog box.[/SIZE]

[FONT=&quot] 
[/FONT]  
[FONT=&quot]Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.[/FONT][FONT=&quot]
 
 [/FONT]
  [SIZE=2]

How do I "fix" this?

Thanks,

Lara[/SIZE]

---

### Post by newbie-user on 2012-04-24
You would need to add the pgp keys from the untrusted source. See here for a howto:

[http://askubuntu.com/questions/5917/add-repository-to-ubuntu-from-terminal-with-pgp-key](http://askubuntu.com/questions/5917/add-repository-to-ubuntu-from-terminal-with-pgp-key)

---

### Post by techsupport on 2012-04-24
> **Lara_Baker said:**
> [SIZE=2]When I checked the box to do a lot of upgrades (~365MB), after entering my admin pw, I got the message in a dialog box.  My only option is to close the dialog box.[/SIZE]

[FONT=&quot] 
[/FONT]  
[FONT=&quot]Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.[/FONT][FONT=&quot]
 
 [/FONT]
  [SIZE=2]

How do I "fix" this?

Thanks,

Lara[/SIZE]

Just override it for now. It is only a warning about the PGP keys being missing. How did you install your repos?

---

### Post by grahammechanical on 2012-04-24
You will need to go to the Settings section of the Update Manager and uncheck those PPAs that you put in.

In the past we could just click OK to confirm that we accepted the risk but now the Update Manager just closes.

so, you need to remove those PPAs that are part of your software sources and then the Update will proceed.

Regards.

---

### Post by Lara_Baker on 2012-04-25
Thanks much -- that worked the first time and fixed the problem!

I really appreciate the clear, succinct, accurate answer.

Best Regards,

Lara

---

### Post by techsupport on 2012-04-25
> **Lara_Baker said:**
> Thanks much -- that worked the first time and fixed the problem!

I really appreciate the clear, succinct, accurate answer.

Best Regards,

Lara

Don't forget to mark this thread as solved, and you are welcome.

:popcorn:

---

