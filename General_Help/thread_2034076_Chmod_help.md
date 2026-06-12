---
title: "Chmod help"
date: 2012-07-27
forum: General Help
---

### Post by waveOSBeta on 2012-07-27
My friend was playing around with chmod and he ran the following command:

sudo chmod 764 /*

And how he can't do ANYTHING. Not even sudo. Can anyone shed some light on what I can do to fix this? He can't even access his own home folder..

Thanks,

Wave

---

### Post by MSPdwalt on 2012-07-27
So....what that command means is set permissions 764 on everything underneath / (root).

If sudo isn't working you might be boned.  Some friend you have there.  Be very, very careful with when using sudo and *.

Try booting to a live CD, doing a

```
ls -l /
``` 

This will show you the default permissions for the contents of /

Mount your physical drive and use chmod to match the permissions appropriately.  

Correct me if I'm wrong guys, but just using * shouldn't descend into sub-directories right?

---

### Post by papibe on 2012-07-27
Hi waveOSBeta.

Your friend will have to boot into recovery mode and fix the permissions selecting a root shell prompt.

Here's a guide to fix a similar problem: [Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo"). Follow it until the section 'Do the actual repair'.

Then run this:
```
cd /
chmod 755 *
chmod 700 lost+found/ root/
chmod 555 proc/
chmod 777 vmlinuz*
chmod 1777 tmp/
```

I hope that helps. Let us know how it goes.
Regards.

---

### Post by waveOSBeta on 2012-07-27
> **papibe said:**
> Hi waveOSBeta.

Your friend will have to boot into recovery mode and fix the permissions selecting a root shell prompt.

Here's a guide to fix a similar problem: [Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo"). Follow it until the section 'Do the actual repair'.

Then run this:
```
cd /
chmod 755 *
chmod 700 lost+found/ root/
chmod 555 proc/
chmod 777 vmlinuz*
chmod 1777 tmp/
```I hope that helps. Let us know how it goes.
Regards.
When I type sudo in a normal session, I get a command not found. :/

---

### Post by papibe on 2012-07-27
> **waveOSBeta said:**
> When I type sudo in a normal session, I get a command not found. :/

You won't be able to fix it on a regular graphic session. That is why you need to boot into recovery mode.

Regards.

---

### Post by waveOSBeta on 2012-07-27
Oh. I figured the tutorial was for people getting a not in sudoers file error. I'll tell him to boot into recovery mode.

Thanks,

Wave

---

### Post by galvatron408 on 2012-07-28
You don't need recovery mode, just run...

su -

type the root password and then fix the problem. "su -" means switch user (to root).

---

### Post by lisati on 2012-07-28
> **galvatron408 said:**
> You don't need recovery mode, just run...

su -

type the root password and then fix the problem. "su -" means switch user (to root).

The preferred method with Ubuntu is [sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by galvatron408 on 2012-07-28
That's great. If only he could use sudo. He said he couldn't sudo. Scroll up.

So, everyone says to reboot in to recovery mode. Yes, you could reboot in to recovery mode so that you can be "root" but wouldn't it be WaaaaaY easier to just "su -" and fix the problem?

-Vetern Systems Administrator

> **lisati said:**
> The preferred method with Ubuntu is [sudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by papibe on 2012-07-28
Unfortunately 'su' won't work because:
[LIST=1]
[*]There's no execution permission to /bin (where 'su' is located), and
[*]root's password is disable by default in Ubuntu, so 'su' only work with, well, sudo.
[/LIST]
Regards.

---

### Post by galvatron408 on 2012-07-28
Maybe in version 10, which is what you're using. Works great in version 12, which I'm using.

> **papibe said:**
> Unfortunately 'su' won't work because:
[LIST=1]
[*]There's no execution permission to /bin (where 'su' is located), and
[*]root's password is disable by default in Ubuntu, so 'su' only work with, well, sudo.
[/LIST]
Regards.

---

### Post by HiImTye on 2012-07-28
> **galvatron408 said:**
> Maybe in version 10, which is what you're using. Works great in version 12, which I'm using.
really?

```
tye@T:~$ lsb_release -d -s
Ubuntu 12.04 LTS
tye@T:~$ su
Password: 
su: Authentication failure
tye@T:~$ sudo su
[sudo] password for tye: 
root@T:/home/tye# exit
exit
tye@T:~$ 
```

---

