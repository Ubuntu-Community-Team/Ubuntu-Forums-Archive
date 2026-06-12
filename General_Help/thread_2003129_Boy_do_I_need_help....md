---
title: "Boy do I need help...???"
date: 2012-06-13
forum: General Help
---

### Post by robertcoulson on 2012-06-13
Hi guys

Some how I can't input my old password, don't know what happened. Some one said to use a live cd and go to the terminal and type in "passwd" and change the password, BUT it asked me for my "current" password which I don't know...

Can anyone help....?

I am using Ubuntu 12.04

---

### Post by matt_symes on 2012-06-13
Hi

Take a look at this blog post.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Kind regards

---

### Post by robertcoulson on 2012-06-13
Thanks for trying to help Matt-symes, but it comes up as an error.

Does anyone else have any ideas so I don't have to re-install 12.04 all over again...???

Or can I re-install 12.04 again and keep my files and gnome...???

---

### Post by robertcoulson on 2012-06-13
Or can I re-install 12.04 over my existing 12.04 and still have my files and gnome...???

---

### Post by SeijiSensei on 2012-06-13
Reboot and select the "recovery mode" kernel from the grub menu. (If you don't see that menu, hold down the Shift key while booting.) Choose "root shell" from the list of options when offered.

At the root prompt ("#"), type "passwd yourusername" and enter the password.  Reboot once more and log in with your username and the password.

---

### Post by matt_symes on 2012-06-14
Hi

Sorry for the delay. Timezones and sleep i suspect...

Did SeijiSensei's suggestion help ?

> Thanks for trying to help Matt-symes, but it comes up as an error.

You have no hope of getting any useful support if you do not post back error messages.

Kind regards

---

### Post by robertcoulson on 2012-06-14
Hi SeijiSensei

Tried what you said and got the error below...

[B]retype new unix password:
passwd : authentication token manipulation error
passwd : password unchanged[/B]

---

### Post by SeijiSensei on 2012-06-14
I suspect there's a deeper problem.  Perhaps the root filesystem is corrupt.  Linux will mount the root filesystem as read-only if it has errors, meaning you cannot alter the shadow password file /etc/shadow.  Try following the steps [here](http://ubuntuforums.org/showpost.php?p=11838980&postcount=21), then after rebooting, try the passwd command again.

---

### Post by steeldriver on 2012-06-14
iirc that's usually because the root partition is mounted ro in the recovery console - so it can't update the password file

try doing this first

```
mount -o remount,rw /
```

or exit from the root shell and select the "Remount / read-write and mount other filesystems" option from the recovery menu

---

### Post by speel on 2012-06-14
If there is nothing of value on the drive the just reformat and install and just try to use some type of backup service wether its ubuntu one or even a usb key. If you want you can experiment with this [http://www.sysresccd.org/](http://www.sysresccd.org/) but I have no personal experience with it.

---

### Post by matt_symes on 2012-06-14
Hi

> passwd : authentication token manipulation error

The problem with this error is there is no one cause of it. From the root console...

Have you checked auth.log for PAM errors ?

```
tail -f /var/log/auth.log
```

and then try to change the password. Any PAM errors displayed ?

You can also try

```
pwck
```

to check the integrity of the passwd and shadow file.

Also have you checked the permissions.

```
ls -l /etc/{passwd,shadow}
```

Post back any errors from the above commands.

You have space on your root partition ?

```
df -h
```

Kind regards

---

### Post by robertcoulson on 2012-06-14
Hey guys

Tried all your ideas, but every time it asks for my OLD password....That is what I am trying to fix.

Appreciate all your help guys, maybe the best way like **speel** said is just to re-install 12.04, BUT one question, if I re-install it will I be able to keep my folders and my gnome...???

---

### Post by matt_symes on 2012-06-14
Hi

I though you were having authentication errors in the root console  when you tried to change the password ?

You can try deleting your current password from the root console after mounting it read/write.

```
mount -n -o remount,rw /
```

```
passwd --delete <user_name>
```

and then adding a new one.

```
passwd <user_name>
```

As i said though, I thought this was giving you authentication errors.

If you reinstall there should be an option to keep your home directory in 12.04.

I would back up your data, though, if you reinstall. Just in case.

Kind regards

---

### Post by robertcoulson on 2012-06-14
**matt_symes**...Do I do this right in m terminal...???

---

### Post by matt_symes on 2012-06-14
Hi

> **robertcoulson said:**
> **matt_symes**...Do I do this right in m terminal...???

In the root console from the recovery mode.

Kind regards

---

### Post by robertcoulson on 2012-06-14
Hi **matt_symes** and **everyone else** who tried to help...Got frustrated and re-installed 12.04 and are back to 98% where I was before...Thanks guys.

---

