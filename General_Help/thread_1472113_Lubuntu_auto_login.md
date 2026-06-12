---
title: "Lubuntu auto login"
date: 2010-05-04
forum: General Help
---

### Post by JUSTINBEAIRD on 2010-05-04
hello I installed lubuntu-desktop on an old computer for my cousins kids
from the lucid mini.iso
can someone help me set up auto login for them?

---

### Post by kerry_s on 2010-05-04
/etc/lxdm/default.conf

just uncomment to activate it & put your name.

mine looks like this.

---

### Post by daniele80 on 2010-05-04
thanks, it works for me :P

---

### Post by w1zard on 2010-05-11
Worked great for me too - if anyone else wants to do this, it's just a few easy steps:

Open Accessories->LXTerminal

Type the text below and hit enter

```
sudo leafpad /etc/lxdm/default.conf
```

Type your password when prompted, and hit enter again.

Add this line to the text beneath the [base] section, substituting your username:

```
autologin=myusername
```

Save the file, and you're done!

Thanks for the advice :)

---

### Post by kerry_s on 2010-05-11
> **w1zard said:**
> Worked great for me too - if anyone else wants to do this, it's just a few easy steps:

Open Accessories->LXTerminal

Type the text below and hit enter

```
sudo leafpad /etc/lxdm/default.conf
```

Type your password when prompted, and hit enter again.

Add this line to the text beneath the [base] section, substituting your username:

```
autologin=myusername
```

Save the file, and you're done!

Thanks for the advice :)

your suppose to use "gksudo" for graphical programs, then you can just use your alt+f2 run command.

i actually use a script for mine in /usr/local/bin which overides the leafpad command, i have nopasswd set in sudoers for it:
```

#!/bin/bash

test=`stat -c %U "$@"`
if [ "$test" == "root" ]; then
	gksudo /usr/bin/leafpad "$@" &
else
	/usr/bin/leafpad "$@" &
fi
exit 0


```

makes life easy. :)

---

### Post by w1zard on 2010-05-11
Thanks for the tips! This certainly makes life easier :)

---

### Post by MacHaddock on 2012-02-21
I got some sort of an error message at reboot saying something about xsession missing and not finding fallback session so I had to remove it again. Someone know what went wrong?

---

### Post by ethanay on 2013-03-07
from [http://www.itworld.com/operating-systems/289434/how-put-lubuntu-automatic-login-mode]("http://www.itworld.com/operating-systems/289434/how-put-lubuntu-automatic-login-mode")

> In Ubuntu releases starting with 12.04, however, you need to edit a different file. With the new display manager, lightdm, a different file is used to manage this setting. So, you edit the /etc/lightdm/lightdm.conf file instead.

lightdm is an X display manager that is fast, extensible and provides the ability to use multiple desktops -- like lubuntu and OpenBox. The lightdm.conf file, after your changes, will look something like this. Note the lack of # signs on the autologin lines:

[SeatDefaults]
autologin-user=spongebob
autologin-user-timeout=0
user-session=Lubuntu
greeter-session=lightdm-gtk-greeter
You can switch back to the using a username and password to log in in by reversing the changes described above. Put the comment markers back in front of the autologin lines and reboot.

---

### Post by wildmanne39 on 2013-03-07
Old thread closed!

---

