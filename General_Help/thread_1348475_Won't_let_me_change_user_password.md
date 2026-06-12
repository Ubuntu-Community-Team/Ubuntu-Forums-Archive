---
title: "Won't let me change user password"
date: 2009-12-07
forum: General Help
---

### Post by cjwescott on 2009-12-07
Even funnier than that, it partially took the new password.

After trying to change the password which was authenticated, now the login password is still the old one but when I enter Evolution it only accepts the new one.

Any suggestions on how I can get it to accept a new password?

Chris

---

### Post by Seven_Six_Two on 2009-12-07
What process did you use to change your password? Is this for your computer login, or your email address? What version of Ubuntu are you using?

J.P.

---

### Post by abhilashm86 on 2009-12-07
did you try in terminal or in GUI?? 
use in terminal ```
passwd
``` to change password......

---

### Post by cjwescott on 2009-12-07
I utilized the GUI interface, using admin/user.....
 
So...if I use the Terminal and type in passwd I will receive prompts directly afterwords correct?  Also, if I do it this way, can I assume that the password that I will be changing will be for the user that I am currently logged into?  BTW: I set up two users, one for me and one for my wife.  It is my wife's that I am trying to change.

---

### Post by abhilashm86 on 2009-12-07
> **cjwescott said:**
> I utilized the GUI interface, using admin/user.....
 
So...if I use the Terminal and type in passwd I will receive prompts directly afterwords correct?  Also, if I do it this way, can I assume that the password that I will be changing will be for the user that I am currently logged into?  BTW: I set up two users, one for me and one for my wife.  It is my wife's that I am trying to change.

oh then, you log into ubuntu in your wife's password, then open terminal, type ```
passwd
``` , so the change will be for your wife password.....

see its more easy to change users in terminal, use su (switch user)
if your wife name is aaa
```
su aaa
```
so then you can change passwd, which will also changes your wife passwd.........

so home directory will change /home/aaa ,
but i don't know if you understand switch users concept!! su is great when it comes changing users!! read and get more info about it!!
so better reboot and change passwd:)

---

### Post by abhilashm86 on 2009-12-07
one question, are you comfortable with terminal? because you should know before you type, 
if you copy paste some thing on terminal, it'll not work, makes things worse!!
so google command, or use man [command name] for help and head on!!

---

### Post by cjwescott on 2009-12-07
I used the terminal/passwd and it worked.

I have used the terminal before (following directions on websites to load items, etc)  I'll understand more over time.

Thx for the suggestions.

Chris

---

### Post by Bradj47 on 2009-12-07
> **abhilashm86 said:**
> oh then, you log into ubuntu in your wife's password, then open terminal, type ```
passwd
``` , so the change will be for your wife password.....

see its more easy to change users in terminal, use su (switch user)
if your wife name is aaa
```
su aaa
```
so then you can change passwd, which will also changes your wife passwd.........

so home directory will change /home/aaa ,
but i don't know if you understand switch users concept!! su is great when it comes changing users!! read and get more info about it!!
so better reboot and change passwd:)

Wouldn't 
```
passwd aaa
```
also work?

---

### Post by abhilashm86 on 2009-12-07
> **Bradj47 said:**
> Wouldn't 
```
passwd aaa
```
also work?

hey you din't understand what i told!! i told him re-boot with her wife password and login, open a terminal, then ```
passwd
```!!
and
```
su aaa
``` changes user from him his login to wife login, did you get the point what i told?
see this example,
```
abhilash@abhilash:~$ su abhilash
Password: 
       _                 _                              _     _ 
 _   _| |__  _   _ _ __ | |_ _   _  __      _____  _ __| | __| |
| | | | '_ \| | | | '_ \| __| | | | \ \ /\ / / _ \| '__| |/ _` |
| |_| | |_) | |_| | | | | |_| |_| |  \ V  V / (_) | |  | | (_| |
 \__,_|_.__/ \__,_|_| |_|\__|\__,_|   \_/\_/ \___/|_|  |_|\__,_|
                                                                
Hello abhilash

This is BASH 4.0 
Tue Dec  8 10:06:38 IST 2009
Be cautious in your daily affairs.
abhilash@abhilash:~$ 


```

---

