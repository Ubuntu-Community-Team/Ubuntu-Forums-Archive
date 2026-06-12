---
title: "corrupt user, will not boot"
date: 2012-05-03
forum: General Help
---

### Post by kelsonbaird on 2012-05-03
Using ubuntu 12.04, I somehow currupted my one and only user, now ubuntu will not boot. it will give me recovery terminal but cannot login, anyone know how to fix this?

---

### Post by effenberg0x0 on 2012-05-03
> **kelsonbaird said:**
> Using ubuntu 12.04, I somehow currupted my one and only user, now ubuntu will not boot. it will give me recovery terminal but cannot login, anyone know how to fix this?

By holding shift when the computer boots you can get to the recovery option and select a root shell. I believe you got there already. At this point, you could simply add a new user:

```
# useradd newusername -m -s /bin/bash
# passwd newusername
# usermod -aG newusername adm,cdrom,sudo,dip,plugdev,lpadmin,sambashare newusername

```
Reboot now.
```
sudo reboot now
```

Regards,
Effenberg

---

### Post by kelsonbaird on 2012-05-03
that sounds lke it would do the trick but, I keep getting 
 
"cannot lock /etc/passwd"
any ideas? I am kinda a Newb

---

### Post by kelsonbaird on 2012-05-03
also to note: I cannot use the sudo command because it doen't know who I am, and can't login because it is trying to use HOME=/ not the actual home folder at /home/mine (mine being the username)

---

### Post by effenberg0x0 on 2012-05-03
If you look at my previous answer, you will see I haven't suggested you use sudo. not even once. When you access the system using the Recovery Mode, you will be root (full permissions) without password or a need for sudo. Check the screenshots [here]("http://unixlab.blogspot.com.br/2009/08/exploring-ubuntu-recovery-mode.html") if you have a question on how t access recovery mode.

If you are receiving that "lock" error message even as root in a recovery mode session:

- You might have one or more of the following files: /etc/group.lock, /etc/passwd.lock /etc/shadow.lock, /etc/gshadow.lock. Simply run the following command. If they exist, they will be deleted. If not, there's no harm in trying.```

# rm -rf /etc/group.lock
# rm -rf /etc/passwd.lock
# rm -rf /etc/shadow.lock
# rm -rf /etc/gshadow.lock

```
- Although rare, it could be a faulty app armor profile. Try disabling apparmor temporarily:```

# service apparmor stop

```
When you create a new user, with the commands I posted previously, it should be able to login to a proper environment, with sane environment variables (such as $HOME, that you mentioned). 

Regards,
Effenberg

---

### Post by kelsonbaird on 2012-05-03
Well that is not working, still get that same message. 
I was using sudo earlier because it was mentioned in other post, but like I said that did not work, one thing that sort of worked was "mount -o remount,rw /" I then didn't get the "cannot lock /etc/passwd" message and it allowed me to useradd, but when I went to sent password with "passwd NAME" it said that it could not determine the user. Any other suggestions?

---

### Post by effenberg0x0 on 2012-05-03
> **kelsonbaird said:**
> Well that is not working, still get that same message. 
I was using sudo earlier because it was mentioned in other post, but like I said that did not work, one thing that sort of worked was "mount -o remount,rw /" I then didn't get the "cannot lock /etc/passwd" message and it allowed me to useradd, but when I went to sent password with "passwd NAME" it said that it could not determine the user. Any other suggestions?

It's weird that on recovery/netroot you had to manually remount / as read/write. Normally you wouldn't have to. And that explains why the "lock" messages. So, at any rate, it was a great find, I'd never have guessed.

I'm not sure if you have no environment variables set for root? Again, that would be totally unexpected. I don't think I have ever seen that. But, wild guessing, you could try:

```
USER=UserName && export USER
HOME=/home/UserName && export HOME
LOGNAME=UserName && export LOGNAME
# passwd UserName
(enter new password for UserName)
```

Let me know.

Regards,
Effenberg

---

### Post by kelsonbaird on 2012-05-03
Well still didn't work. I think that I will do a clean install, seems easier at this point. I don't really like 12.04 anyway, not a fan of unity and the gnome doesn't function correctly all the time.

---

