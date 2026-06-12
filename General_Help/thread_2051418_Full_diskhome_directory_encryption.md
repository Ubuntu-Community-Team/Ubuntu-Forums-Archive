---
title: "Full disk/home directory encryption"
date: 2012-09-01
forum: General Help
---

### Post by aef54 on 2012-09-01
I'm installing Ubuntu using the alternate installation CD.

I would like to do full disk encryption, and I have two questions:

1. Is the following option the correct one for Full Disk Encryption with pre-boot authentication?

```
Partitioning method: Guided - use entire disk and set up encrypted LVM
```2. If you select that  option, it still gives you the option to encrypt the home directory later on. But if you already have have an encrypted LVM, does that add anything  security wise, right? Can I just skip that?

---

### Post by jerome1232 on 2012-09-01
> **aef54 said:**
> 

1. Is the following option the correct one for Full Disk Encryption with pre-boot authentication?yes
> **aef54 said:**
> 
```
Partitioning method: Guided - use entire disk and set up encrypted LVM
```2. If you select that  option, it still gives you the option to encrypt the home directory later on. But if you already have have an encrypted LVM, does that add anything  security wise, right? Can I just skip that? yes, you can skip that

---

### Post by aef54 on 2012-09-01
Thanks. I did that (I chose to not encrypt home directory, just the entire drive).

however, now it still prompts two passwords when booting. First the pre-boot authentication, and then my root password to get into my account.

---

### Post by jerome1232 on 2012-09-01
> **aef54 said:**
> Thanks. I did that (I chose to not encrypt home directory, just the entire drive).

however, now it still prompts two passwords when booting. First the pre-boot authentication, and then my root password to get into my account.

I assume you mean your users password, Ubuntu doesn't have a root account enabled by default.

Yes that's normal, if you desire you can disable your users password so that you aren't prompted for a password under System Settings - User Accounts.

---

### Post by aef54 on 2012-09-01
Thanks. I'll do that (if the entire disk is encrypted, I don't see how it adds to security).

I'm kinda noob with the terminology. User password it is. It's the same password that's required to install software or do sudo commands.

It's all working so far. Marvelous piece of software this is.

Marking this one as solved.

---

### Post by jerome1232 on 2012-09-01
> **aef54 said:**
> Thanks. I'll do that (if the entire disk is encrypted, I don't see how it adds to security).

Well for one, your user is an admin user, you can use that users password to escalate it's privileges to that of root using sudo and make system wide changes that can impact every user. Despite disabling the login password, you are still going to be prompted for a password when making changes via sudo (I think, I've never actually disabled the password on an admin account, let me know about that)

Remember once the computer is on and the encryption is unlocked, It's no different than an unencrypted hard drive.

Here's a little info about sudo, root, and such things [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Tobeus on 2012-09-01
The user password improves security from remote hacks/attacks.  If something tried to connect to your machine while your drive was decrypted they would have to have your user account password (in this case also your root password).  It is not a very likely scenario, but if the user / root password were not set, it is similar to leaving your car unlocked all the time in a busy city.  The thieves wouldn't necessarily have the ability to drive you car away because of your awesome encryption, but they could take everything they wanted from your car without any real resistance to speak of.  It's just not a good practice to get into.

-Tobeus

---

### Post by aef54 on 2012-09-02
> **jerome1232 said:**
> Despite disabling the login password, you are still going to be prompted for a password when making changes via sudo []("https://help.ubuntu.com/community/RootSudo")
Yes, that is exactly what I wanted.

The only thing I wanted is not having to type the user password when booting, since I already have the pre-boot authentication to prevent unwanted access.

I do want to Ubuntu to prompt the user password when doing sudo operations, because from what I learned, that protects you against unwanted malware being secretly installed.

---

### Post by aef54 on 2012-09-02
Unsolved the thread.

I got another issue. When using the encrypted OS, now and then I get a hangup and the screen freezes. The only way to get out of it is to reset the computer. However at rebooting, it gives an error: system uncleanly demounted (or something like that), it won't boot and I'm in a world of errors.

The only possibility I've found in that situation is to reinstall the complete OS. Is that a problem that is familiar to other people who have their complete disk encrypted using Ubuntu?

---

