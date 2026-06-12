---
title: "Urgent Help required - root access"
date: 2010-02-17
forum: General Help
---

### Post by jsriz on 2010-02-17
Hi All,
While Luking around i found "Users And Groups" and jus 4 fun i selected my account and selected properties->user pevilages and unchecked everything.Thats It I Have Locked Myself Out 'NO' super user previlages cant mount anything.it asks for a root password(which i have not set until now).
PLEASE HELP...................

---

### Post by flippo on 2010-02-17
drop to tty1 (ctrl+alt+f1, also, use ctrl+alt+f7 to get back to your gui) and login as root (use username root, and root pw)  what is the output of:```
cat /etc/sudoers
```

also, what is the output of:```
groups
```when logged in as your default user (the one who lost sudo privledges)

---

### Post by jamesisin on 2010-02-17
flippo - If he has not set a root password, how will he login as root?

---

### Post by jfr1tz on 2010-02-17
> **jamesisin said:**
> flippo - If he has not set a root password, how will he login as root?

boot livecd and re-add user to sudoers group by hand or boot rescue mode and drop to root shell there?

edit, theres no sudoers group so adm,admin then?

---

### Post by jsriz on 2010-02-17
> login as root (use username root, and root pw))
I Have Not set any root pw and my user account password dosent let me login

---

### Post by jsriz on 2010-02-17
> re-add user to sudoers group
Please let me know how do i do that...

---

### Post by jsriz on 2010-02-17
> **flippo said:**
> drop to tty1 (ctrl+alt+f1, also, use ctrl+alt+f7 to get back to your gui) and login as root (use username root, and root pw)  what is the output of:```
cat /etc/sudoers
```also, what is the output of:```
groups
```when logged in as your default user (the one who lost sudo privledges)
well i logged on with my username(srinivas) and pass
herez the op without the cmmnts srinivas is my user name
vi /etc/group
```

Defaults env_reset
root ALL=(ALL) ALL
%sudo ALL=NOPASWD:ALL   (I Removed # before this line from recovery mode)
%admin ALL=(ALL) ALL

```
groups
```

srinivas root

```

---

### Post by nothingspecial on 2010-02-17
Reboot, as soon as you see "grub loading" press escape.

Choose recovery mode (or whatever they call it these days)

Then choose root shell (again, whatever they call it these days, it should be something similar)

Type

```
adduser *[COLOR="Red"]username[/COLOR]* admin
```

sustitute the red username for your actuall username

```
reboot
```

That should fix it.

---

### Post by jsriz on 2010-02-17
That worked Thanks a ton
Prblm solved in 1hr of posting U GUYZ ROCKK......

---

### Post by jamesisin on 2010-02-17
Great.  Be sure to mark your thread as SOLVED in Thread Tools above.

---

### Post by jsriz on 2010-02-17
done

---

### Post by jamesisin on 2010-02-18
I just discovered something of interest.  There is a command which will produce an endless string of the letter y:

```
yes
```

You can interrupt the command with ctrl-c and get your command prompt back.

If you add a string it will repeat that string until interrupted:

```
yes 'Repeat Me'
```

Perhaps this relates to the issue you experienced.

---

