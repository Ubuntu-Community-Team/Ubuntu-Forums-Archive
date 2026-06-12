---
title: "Root password needed for fsck"
date: 2009-08-18
forum: General Help
---

### Post by toofast.mv on 2009-08-18
Hi,
have ubuntu 9.04 installed on my sd card for my laptop. Today i was using it, and put it to standby, but when i tried to wake it, it froze. So i hard reset (held power button), and now it gives me the error that fsck needs to be done manually. So it wants me to login to a maintenance shell, and says "Give root password for maintenance", but i have no idea what root pass is. What is the easiest way to find out. I never set up a root pass, instead using sudo when needed, with my user password. 
Thanks

---

### Post by dmizer on 2009-08-18
Use the live CD to do your scan instead. It's safer that anyway.

---

### Post by lisati on 2009-08-18
The preferred method of temporarily giving yourself root privileges in Ubuntu is with the sudo command. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by toofast.mv on 2009-08-18
Cheers for the quick replies.

I am on live cd now. Need to know who do i know what is my sd card value. eg sda1 etc. 

Also do i just type sudo fsck sdwhatever, and it will fix it?

EDIT: :D

Seems to be back up now. It told me i had some inodes, and i just yes'd everything, which got it going. Cheers for this, as my university software project was on that, so would of been hard to lose. Now i see why people say your home and root should be different partitions. 

Just out of interest, how do you find out the root password? I know you can sudo su, and passwd to reset it, but is there anyway to find it out, since you never are asked to set it.

---

### Post by HiImTye on 2009-08-18
the root password is disabled as a security measure. the reason being any hacker worth their grits knows that on a linux system 'root' is always the best account to hack so the root password is disabled, making it impossible for them to hack the password. they then need to know your account name (which is hopefully different than your machine name)

---

### Post by toofast.mv on 2009-08-18
Is there a reason than, that shells, like the maintenance one i encountered, still require a root password. I mean since you say it was disabled, do you mean there was no word i could type into that prompt, to login.

---

### Post by HiImTye on 2009-08-18
yes, that's what the live CD is for :)

you *could* enable the root password if you wanted to but it goes against the Ubuntu security policy

---

### Post by lisati on 2009-08-18
> **toofast.mv said:**
> Is there a reason than, that shells, like the maintenance one i encountered, still require a root password. I mean since you say it was disabled, do you mean there was no word i could type into that prompt, to login.

Already answered here in this very thread: [http://ubuntuforums.org/showpost.php?p=7804930&postcount=3](http://ubuntuforums.org/showpost.php?p=7804930&postcount=3)

---

### Post by mcduck on 2009-08-18
> **toofast.mv said:**
> Is there a reason than, that shells, like the maintenance one i encountered, still require a root password. I mean since you say it was disabled, do you mean there was no word i could type into that prompt, to login.

Are you *absolutely sure* you haven't at some point, enabled the root password? Since the recovery shell shouldn't ask for any passwords unless you have yourself set the root password..

The default setup definitely should not ask for any passwords to enter the recovery mode.

---

### Post by mcduck on 2009-08-18
> **lisati said:**
> Already answered here in this very thread: [http://ubuntuforums.org/showpost.php?p=7804930&postcount=3](http://ubuntuforums.org/showpost.php?p=7804930&postcount=3)
The OP is trying to access the recovery mode, so "sudo" is useless. (since recovery mode logs you in as root). And you definitely can't throw "sudo" into a login prompt..

---

### Post by HiImTye on 2009-08-18
I also get prompted for a root password when I enter recovery mode, however, I still have the root password disabled. figured this was just normal behavior

---

### Post by mcduck on 2009-08-18
> **HiImTye said:**
> I also get prompted for a root password when I enter recovery mode, however, I still have the root password disabled. figured this was just normal behavior

Have you then, perhaps, set a grub password protection for the recovery mode?

The normal behavior is that password isn't asked for recovery mode since there is no password. If the recovery mode required a root password the whole existence of the recovery mode would be rather pointless.. :D

---

### Post by HiImTye on 2009-08-18
I used a root password when I first installed to make moving files around easier but have since disabled the root password

haven't set a grub password

---

### Post by mcduck on 2009-08-18
> **HiImTye said:**
> I used a root password when I first installed to make moving files around easier but have since disabled the root password

haven't set a grub password

That could have caused the recovery mode's behavior to change. I'm not sure how to get the default behavior back, though, I've never seen any reason to enable root in Ubuntu.

---

### Post by sisco311 on 2009-08-18
> **HiImTye said:**
> I used a root password when I first installed to make moving files around easier but have since disabled the root password

haven't set a grub password

How did you disabled the password?

```
sudo passwd -dl root
```

> **mcduck said:**
> That could have caused the recovery mode's behavior to change. I'm not sure how to get the default behavior back, though, I've never seen any reason to enable root in Ubuntu.

Yep, it was a bug in Hardy, but I think it's fixed now.

Anyway, one could manually edit the shadow file:
```
sudo VISUAL=nano vipw -s
```

and lock the account by replacing the encrypted password with a !:
> root:**[B]$6$Vnf21Dn6$bx39xChZ.AJcHrxRE0a4sRXIAPhIB1MVSSk7RIq/EEZCxhYdnx2pOZPL26zszCzlAPsGObwjlWHx0vggx7sPo/**[/B]:14474:0:99999:7:::

> root:**!**:14474:0:99999:7:::

---

### Post by toofast.mv on 2009-08-18
I actually did have a play with root password before. Using sudo to access su, then changing the password. But i know what i changed the password to, and that didn't let me access maintenance shell. 

But since you have brought up the security concerns, would sudo passwd -dl root disabled it correctly?

---

### Post by HiImTye on 2009-08-18
I used
```
sudo passwd -dl root
```and /etc/shadow has an astrerix for encryption type field for root

edit: correction it has an exclamation mark, I was looking at the second line

---

