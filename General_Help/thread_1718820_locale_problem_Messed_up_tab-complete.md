---
title: "locale problem? Messed up tab-complete"
date: 2011-03-31
forum: General Help
---

### Post by lethalfang on 2011-03-31
This problem started today. 
When I started my Ubuntu 10.04.02, a message appeared that "my locale has changed," whether or not to change a couple of directory names. I selected "no" and ignored it.
Now everytime I try tab complete on the terminal, I get this:

cd Do (tab) is supposed to get me to cd Document, but it gets me this:

```
cd Do**bash: warning: setlocale: LC_CTYPE: cannot change locale (en_US)**
cuments/
```

It happens in all tab completions. What is this? 


```
cat /var/lib/locales/supported.d/local
ss_ZA UTF-8
tn_ZA UTF-8
gv_GB.UTF-8 UTF-8
se_NO UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
```



```
cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="en_US:en"
LANG="en_US.UTF-8"
```


```
cat /etc/default/locale
LANG=en_GB.UTF-8
LANGUAGE="en_US:en"
```


Is there any problems?







[B]FIX:
```
sudo locale-gen en_US
sudo update-locale LANG=en_US
sudo dpkg-reconfigure locales

```[/B]

---

### Post by daqron on 2011-04-14
Thanks for the fix, lethalfang. Note to other Googlers: I also had to close my terminal window and open a new one for the fix to take effect.

---

### Post by JohanWJoubert on 2011-09-04
> **daqron said:**
>  Note to other Googlers: I also had to close my terminal window and open a new one for the fix to take effect.

Thanks!! I'm ssh'ing into my server, and applied the fix above, but I still have the same issue. Even after closing the terminal. Should one first restart the server? I hope not.

---

### Post by teedubb on 2011-10-23
lethalfang's solution worked for me.

---

### Post by gornack on 2011-11-08
Worked great here also, thanks.

---

### Post by little_penguin on 2011-11-20
Worked for me too, thanks.

---

