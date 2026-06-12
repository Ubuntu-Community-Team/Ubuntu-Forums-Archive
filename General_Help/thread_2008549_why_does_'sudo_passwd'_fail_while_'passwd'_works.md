---
title: "why does 'sudo passwd' fail while 'passwd' works?"
date: 2012-06-22
forum: General Help
---

### Post by anon0 on 2012-06-22
I noticed that when I was adding sudo to 'passwd', the password change did not work (I could still log in using the old password), but if I just type 'passwd', then the update was effective. I saw another user with similar experience too. What is the point of this? It seems unintuitive, since one may assume that changing the password should require a higher authority.

---

### Post by haqking on 2012-06-22
> **anon0 said:**
> I noticed that when I was adding sudo to 'passwd', the password change did not work (I could still log in using the old password), but if I just type 'passwd', then the update was effective. I saw another user with similar experience too. What is the point of this? It seems unintuitive, since one may assume that changing the password should require a higher authority.

why is it counter intuitive ?

You are changing your own password, you authorise the change by providing your old one (which would be the same as typing sudo)

Unless you trying to change another accounts passwd

---

### Post by papibe on 2012-06-22
Hi anon0.

Changing the password does not require to be run as root. Note that 'passwd' is a command that is by itself secured: it asks for your current password (just like sudo).

Is important to note that 'sudo passwd' won't be setting your user's password, but root's password, which it is disable by default as a security measure.

I strongly recommend disabling again the root password by running:
```
sudo passwd -l root
```

I hope that clarifies things a bit.
Regards.

---

### Post by anon0 on 2012-06-23
> **haqking said:**
> why is it counter intuitive ?

I expected that adding sudo to an operation would not cause the operation to fail, but in this case it did, that's why it was confusing. I'm sure some of you who are used to the command know what to do and what not to do, but some users have made the same mistake.

> **papibe said:**
> Is important to note that 'sudo passwd' won't be setting your user's password, but root's password, which it is disable by default as a security measure.

I strongly recommend disabling again the root password by running:
```
sudo passwd -l root
```

Yes, thanks so much! By the way, how would one check if the root password is currently disabled?

---

### Post by HiImTye on 2012-06-23
```
tye@T:~$ sudo cat /etc/shadow | grep root
root:!:15499:0:99999:7:::
```
if root has a password it will be much longer (as it contains a checksum, such as when you run that command and grep your username)

---

### Post by anon0 on 2012-06-23
> **HiImTye said:**
> ```
tye@T:~$ sudo cat /etc/shadow | grep root
root:!:15499:0:99999:7:::
```
if root has a password it will be much longer (as it contains a checksum, such as when you run that command and grep your username)

So it appears that locking a password does not delete it. I deleted the root password with "sudo passwd -d root", and now it seems to be empty. Thanks again.

---

### Post by sisco311 on 2012-06-23
> **anon0 said:**
> So it appears that locking a password does not delete it. I deleted the root password with "sudo passwd -d root", and now it seems to be empty. Thanks again.

You also have to lock the password "sudo passwd -l root". If the password field is empty, then no password is required to authenticate as the specified login name, which is a big security risk. Of course, some applications which read the /etc/passwd file may decide not to permit access if the field is empty, but this behavior is not mandatory.

"passwd -l" adds a `!' at the beginning of the password. In this way, the password is changed to a value which matches no possible encrypted value.

So, you don't have to delete the password in order to lock it. If you see a `!' or `*' at the beginning of the encrypted password field in /etc/shadow, then the password is locked.

---

