---
title: "Sudo timeout driving me crazy. How can I extend the timeout?"
date: 2012-05-23
forum: General Help
---

### Post by charleswb on 2012-05-23
I have read that after entering sudo followed by a command, and entering my password, the terminal should remember my password for 15 min so that I don't have to reenter my password for each command.

However, my sudo timeout seems to be zero. It makes me reenter the word sudo in front of every command line and reenter my password each time too.
[B]
How can I edit the sudoers file to set the time out to 15 minutes?[/B]

---

### Post by kanikilu on 2012-05-23
I haven't changed it myself, but it's in the wiki:

[https://help.ubuntu.com/community/RootSudoTimeout](https://help.ubuntu.com/community/RootSudoTimeout)

---

### Post by matt_symes on 2012-05-23
Hi

> **charleswb said:**
> I have read that after entering sudo followed by a command, and entering my password, the terminal should remember my password for 15 min so that I don't have to reenter my password for each command.
From ```
man sudoers
```.
> Once a user has been authenticated, a time stamp is updated and the user may then use sudo without a
       password for a short period of time (15 minutes unless overridden by the timeout option.

As you state, the default timeout is 15 mins. 
> 
However, my sudo timeout seems to be zero. It makes me reenter the word sudo in front of every command line and reenter my password each time too.

You will always have to enter sudo before a command if you want to run that command with elevated privileges. 

You should not have to enter your password each time though.

> 
[B]
How can I edit the sudoers file to set the time out to 15 minutes?[/B]

First thing i would check would be your sudoers file.

Open a terminal and type

```
sudo visudo
```

Look for a line containing the word ```
Defaults
``` and see if it has the text

```
timestamp_timeout
```. If it does then remove it.

IE. If you see a line that looks something like this

```
Defaults        env_reset, timestamp_timeout=0
```

Change it to this.

```
Defaults        env_reset
```

i.e remove the reference to timestamp_timeout=X from the file.

Be very careful when editing the file (although using visudo should perform checks for you). If in doubt post the contents of the file here so we can look before modify it.

After that i would check the timestamps directories below the directory

```
/var/lib/sudo/
```

EDIT: Beaten to it. That will teach me for writing a novel :)

Kind regards

---

### Post by charleswb on 2012-05-29
Thanks, I haven't yet tried the above, but that should cover it. 

P.S. - I'm not sure if a tech who worked on my computer in the past changed my timeout, or if I just didn't understand. I will work through the above advice step-by-step and figure it out.

Thanks again.

---

### Post by garvinrick4 on 2012-05-29
Be careful charleswb everyone has messed up this file at one time or another. Follow your directions closely. I use nano as a editor each has there preference.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
sign before letters at bottom means ctrl.
click on screenshot below. Just in case      [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

