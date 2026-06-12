---
title: "/etc/sudoers Has No Effect"
date: 2010-06-12
forum: General Help
---

### Post by Penguin Guy on 2010-06-12
**In a nutshell:** sudoers is not designed to use 127.0.0.1

Old, [COLOR="red"]broken[/COLOR] sudoers:
```

# Defaults
Defaults	editor=/usr/bin/nano
Defaults	env_reset
#Defaults	timestamp_timeout=0

# Aliases
Cmnd_Alias	SHUTDOWN = /usr/sbin/shutdown, /usr/sbin/poweroff,\
		/usr/sbin/halt, /usr/sbin/fasthalt, /usr/sbin/reboot,\
		/usr/sbin/fastboot

# Rules
root	ALL=(ALL)	ALL
%admin	ALL=(ALL)	ALL
%admin	[COLOR="Red"]localhost[/COLOR]=(ALL)	NOPASSWD: ALL
ALL	[COLOR="red"]localhost[/COLOR]=(ALL)	NOPASSWD: SHUTDOWN
%admin	All=(ALL)	NOPASSWD: /usr/local/bin/set-xsplash-background

```

New, [COLOR="Green"]fixed[/COLOR] sudoers:
```
Defaults	env_reset,pwfeedback,editor=/usr/bin/nano,timestamp_timeout=0

# Rules
root	ALL=(ALL)	ALL
%admin	ALL=(ALL)	NOPASSWD: ALL
```

Thanks, all, for your time.

---

### Post by Penguin Guy on 2010-07-22
I've messed around a bit, but I still can't get it to work.

---

### Post by bodhi.zazen on 2010-07-22
You are having conflicts as you are listing your user more then once.

You have two lines of %admin and once for ALL

Usually last match in sudoers wins.

Solution : Create a new group, shutdown, see man sudoers and alises

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

---

### Post by AlphaLexman on 2010-07-22
What is the output of:
```
sudo visudo -c
```

---

### Post by Penguin Guy on 2010-07-23
> **bodhi.zazen said:**
> Usually last match in sudoers wins.
```
NOPASSWD: /usr/local/bin/set-xsplash-background
```
Surely, by that logic, I should be able to run [FONT="Courier New"]set-xsplash-background[/FONT] with no password?


The syntax is fine:
```
# visudo -c
/etc/sudoers: parsed OK
```

---

### Post by bodhi.zazen on 2010-07-23
> **Penguin Guy said:**
> ```
NOPASSWD: /usr/local/bin/set-xsplash-background
```Surely, by that logic, I should be able to run [FONT=Courier New]set-xsplash-background[/FONT] with no password?

I am not sure what you are asking. My point is that you have conflicts in your configuration and the result of such conflicts is often unpredictable behavior.

If a user is listed by name and group membership(s) and %admin is listed twice you are going to have issues.

Clean up your syntax , eliminate duplicates, use aliases as shown in the man page and try again.

---

### Post by Penguin Guy on 2010-07-23
> **bodhi.zazen said:**
> I am not sure what you are asking. My point is that you have conflicts in your configuration and the result of such conflicts is often unpredictable behavior.

If a user is listed by name and group membership(s) and %admin is listed twice you are going to have issues.

Clean up your syntax , eliminate duplicates, use aliases as shown in the man page and try again.
I've read the man page, guides, examples, but am still completely clueless how to fix the problem. I just can't see how an alias is going to work. And anyway, I didn't think duplicates mattered?

I tried:
```
%admin	ALL=(ALL)	ALL, NOPASSWD: /usr/local/bin/set-xsplash-background
```
But that blocked everyone from [FONT="Courier New"]sudo[/FONT].

---

### Post by Penguin Guy on 2010-07-30
Ah, from a recent answer on [superuser]("http://superuser.com/questions/169278/localhost-in-sudoers#answer-169563") it looks like sudoers is **not** designed to give privelages to specific Hosts/IPs. I've had to dramatically simplify my sudoers file because of that. It's quite insecure, but hey.

---

