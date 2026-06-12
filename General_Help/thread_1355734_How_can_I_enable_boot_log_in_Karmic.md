---
title: "How can I enable boot log in Karmic?"
date: 2009-12-15
forum: General Help
---

### Post by Lukas666 on 2009-12-15
I get error messages just before the login screen, can not pause the process so I don't know what the errors are about.

I read about the changes to the bootloader, but come on, there must be a way to save those messages. I have **BOOTLOGD_ENABLE=Yes **set and even enabled the boot message deamon.

Nothing works, boot log is still empty. Any tips?

I used to use other distros and boot.log was one of the files I checked regularly. Why can't I do it in Ubuntu?

---

### Post by ww2 on 2009-12-15
Bump.

---

### Post by Lukas666 on 2009-12-18
> **Lukas666 said:**
> I get error messages just before the login screen, can not pause the process so I don't know what the errors are about.

I read about the changes to the bootloader, but come on, there must be a way to save those messages. I have **BOOTLOGD_ENABLE=Yes **set and even enabled the boot message deamon.

Nothing works, boot log is still empty. Any tips?

I used to use other distros and boot.log was one of the files I checked regularly. Why can't I do it in Ubuntu?


Nobody????

Why can't I have in Ubuntu what all other distros have?

And my boot errors are still unresolved...

---

### Post by StuartN on 2009-12-18
> **Lukas666 said:**
> Why can't I have in Ubuntu what all other distros have?

Take a look at syslog in System->Administration->System Log. You can also execute **dmesg | less** in a terminal just after booting up.

---

### Post by oldfred on 2009-12-18
Are you sure its not kerel log that you want to look at. Mine looks like the boot process.

---

### Post by Lukas666 on 2009-12-18
> **oldfred said:**
> Are you sure its not kerel log that you want to look at. Mine looks like the boot process.

nope, I checked kernel logs and [B]dmesg | less

[/B]When the screen is blinking I can see words "error" and "corrupt"[B].

[/B]I could not find it in any available logs.

---

### Post by oldfred on 2009-12-18
I would use the command line to edit to boot to remove quiet & splash so you can see the boot process.

[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot)

---

### Post by Lukas666 on 2009-12-19
> **oldfred said:**
> I would use the command line to edit to boot to remove quiet & splash so you can see the boot process.

[https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot](https://help.ubuntu.com/community/Grub2#Editing%20Menus%20During%20Boot)

This sounds like  a horrible workaround. 
I don't get a single error message at booting, it's the full screen of them. I would like to investingate each single issue.

And they are on the screen just for a fraction of a second.

I still can't believe there is not way to save the boot log.

---

### Post by StuartN on 2009-12-19
> **Lukas666 said:**
> I still can't believe there is not way to save the boot log.

From [http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

> You need to enable boot logging by opening a terminal and typing the following:

```
$ sudo gedit /etc/default/bootlogd
```

The text editor will open, and the following will be show:

```
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No
```

Change BOOTLOGD_ENABLE to yes


---

### Post by Lukas666 on 2009-12-19
> **StuartN said:**
> From [http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

I've tried that, no luck. This instruction is no longer valid for versions 9.04 and 9.10

---

### Post by StuartN on 2009-12-19
> **Lukas666 said:**
> I've tried that, no luck. This instruction is no longer valid for versions 9.04 and 9.10

Well, it looks like boot logging was very comprehensively and deliberately sabotaged because it had a bug in it [https://bugs.launchpad.net/upstart/+bug/98955](https://bugs.launchpad.net/upstart/+bug/98955) and caused more crashes than it solved. It is a two-year-old bug report which is still open and active.

The previous recommendation to remove quiet and splash seem very sensible, but you will still need quick responses.

---

### Post by Azyx on 2009-12-20
> **Lukas666 said:**
> This sounds like  a horrible workaround. 
I don't get a single error message at booting, it's the full screen of them. I would like to investingate each single issue.

And they are on the screen just for a fraction of a second.

I still can't believe there is not way to save the boot log.

Have the same problem. I will now try to video-record the boot screen.

---

### Post by cityguy on 2010-03-31
This has been a problem since 2005.  It's now April of 2010 and yet there is still no resolution to this problem.  I think it's time to escalate it from low to high.  If one isn't able to boot their system because they cannot capture logging information that certainly isn't going to be a system that will be worthy of any serious usage.

So let's get this resolved.

---

