---
title: "Login as root?"
date: 2009-11-26
forum: General Help
---

### Post by unplugged23 on 2009-11-26
Hi there,

I just had a quick question. I was wondering if it was possible to login as root rather than as myself and confirming anything. Almost like a "root mode." I think I remember being able to do something like this before, but am not sure.

Thanks for any help! :D

---

### Post by LordSmight on 2009-11-26
> **unplugged23 said:**
> Hi there,

I just had a quick question. I was wondering if it was possible to login as root rather than as myself and confirming anything. Almost like a "root mode." I think I remember being able to do something like this before, but am not sure.

Thanks for any help! :D

Logging in as root isn't advised, this is why the people behind Ubuntu created the 'sudo' command.
You can also use 'sudo su' to enter a "full-root" mode while in terminal.

---

### Post by unplugged23 on 2009-11-26
I know it isn't advised. I'm just looking for a simple solution to a complex problem. So is it possible?

---

### Post by acoc on 2009-11-26
The root account is created, but given a random password.  The only way to use it is to create a known password for the user ie sudo passwd root.  There are some advantages to having this account, for example if you mess up your sudo privileges, it's easy to get them back.  However, logging into a root account is not advised for most problems.

> You can also use 'sudo su' to enter a "full-root" mode while in terminal.

I wouldn't do this, it sounds like a big security problem.  Use sudo -s

John

---

### Post by unplugged23 on 2009-11-26
> **acoc said:**
> The root account is created, but given a random password.  The only way to use it is to create a known password for the user ie sudo passwd root.  There are some advantages to having this account, for example if you mess up your sudo privileges, it's easy to get them back.  However, logging into a root account is not advised for most problems.



I wouldn't do this, it sounds like a big security problem.  Use sudo -s

John

So how would I go about creating a password for the root account?

I am aware of the security risks logging in as the root poses and I'm ok with them. I don't plan on using it regularly.

---

### Post by acoc on 2009-11-26
```
sudo passwd root
```

Edit: There already is a password for root, but you don't know it.  This changes it.

---

### Post by unplugged23 on 2009-11-26
Thanks so much for all of the help!

---

### Post by cariboo on 2009-11-26
It is against forum policy to show someone how to login as root. You really don't don't need to enable the root account, as anything you can do as root you can use sudo -i to accomplish the same thing. Have a look [here]("http://https://help.ubuntu.com/community/RootSudo") for more info.

---

### Post by lswb on 2009-11-26
> **LordSmight said:**
> Logging in as root isn't advised, this is why the people behind Ubuntu created the 'sudo' command.
You can also use 'sudo su' to enter a "full-root" mode while in terminal.

Just for the record "sudo" was around long before ubuntu or even linux existed.

---

### Post by DeMus on 2009-11-26
@OP:
There is nothing you can't do with the normal sudo command. It's just you are addicted to Windows probably and are used to be able to do things as administrator. Forget that here. Follow the normal Linux rules, Linux is NOT Windows.

@all others:
Why help him? Why tell him how to log in as root while it is policy not to do that? As I wrote here he can do everything with the normal sudo command and thus keep his system safe. You taught him differently.
NOT GOOD.

---

### Post by acoc on 2009-11-27
> There is nothing you can't do with the normal sudo command.

With an exception of fixing messed up sudo permissions, I agree.

> It's just you are addicted to Windows probably and are used to be able to do things as administrator. Forget that here. Follow the normal Linux rules, Linux is NOT Windows.

He never mentioned windows.  I know I had the same question when I came from most other distros (maaybe 3 yrs ago).  You get used to having a root account and at the time sudo had major security problems (fixed now), so knowing how to get access to something that's already there anyway isn't the worst thing in the world.  Also, sudo is far from normal Linux rules, it's just ubuntu's way having people only have to remember one password.

> Why help him? Why tell him how to log in as root while it is policy not to do that?

Log in is a little ambiguous here, could be x-server or command prompt.  Either way it's not ubuntu standard procedure, but is it actually policy to deny people access to root?  The link presented above isn't opening for me.

> As I wrote here he can do everything with the normal sudo command and thus keep his system safe.

Kind of goes against the first quote here.  The only thing that would make his system less secure would be a poor password, but if your user password is poor too, then it really makes no difference.  You can break stuff either way.

I'm not trying to start any flame wars here.  We encouraged him not to log into root because you bypass the safe guards of acting as a normal user.  I use sudo everyday, but if the system I run it on carried extremely important data, I would follow what I suggested and be able to login as a root account (with strong password) as another option to fix my system.

---

### Post by aysiu on 2009-11-27
Everything you need to know is here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

By the way, do **not** use *sudo -s*

If you need a persistent root prompt, use ```
sudo -i
``` instead

---

