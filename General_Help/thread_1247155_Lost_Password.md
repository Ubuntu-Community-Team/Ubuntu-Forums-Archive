---
title: "Lost Password"
date: 2009-08-22
forum: General Help
---

### Post by kibster on 2009-08-22
I changed one of my passwords on my linux ubuntu box . Or I should say it was copied down wrong.. And it won't work. Is there anyway Of getting it or making a new one   Yes its my root password.

---

### Post by ibutho on 2009-08-22
Do you have another account that has admin privileges? If you do, just login to that account and do Applications -> Accessories -> Terminal and enter
```
sudo passwd someuser
```
someuser would be the username of the person who's password you forgot.

---

### Post by cariboo on 2009-08-22
IF you can't get into your account, go into recovery mode and at the menu select drop to root prompt. Once at the prompt type:

```
passwd <username>
```

Once you have entered your paswword and confirmed it type exit, and from the menu select resume, this will take you back to your desktop.

---

### Post by Iowan on 2009-08-22
See if [this]("http://www.psychocats.net/ubuntu/resetpassword") one helps.

---

### Post by kibster on 2009-08-23
Well it didnt work... It said it did but didnt...

did the ls /home 
typed the passwd <user>
asked for a password 
typed it...
asked again to confirm did that.
retyped it

rebooted

still dead in the water... 

is its because its the root ?

---

### Post by michy99 on 2009-08-23
> **kibster said:**
> Well it didnt work... It said it did but didnt...

did the ls /home 
typed the passwd <user>
asked for a password 
typed it...
asked again to confirm did that.
retyped it

rebooted

still dead in the water... 

is its because its the root ?

If it's the root password you have to enter <snip>. It's not really recommended to set a root password in Ubuntu. You should just use sudo and gksudo instead. I have never set one and never needed it.

---

### Post by kibster on 2009-08-23
SNIP  meaning a portion of something ???? like perhaps part of the password.

Sorry  I'm lost

---

### Post by michy99 on 2009-08-23
> **kibster said:**
> SNIP  meaning a portion of something ???? like perhaps part of the password.

Sorry  I'm lost

Sorry, a moderator snipped something from my post because what I was telling you is against forum policy. Root passwords are a touchy subject around here.

You should probably disable the root password:```
sudo usermod -p '!' root
```Then read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wojox on 2009-08-23
Snip means there are certain things we are not allowed to discuss.

---

### Post by kibster on 2009-08-23
well that would be nice but I cant use synaptic package manager.

---

### Post by kibster on 2009-08-23
I'm really getting frustrated... I'll have to wait and go get some dvd's to burn a disk.

---

