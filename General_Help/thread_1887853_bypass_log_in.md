---
title: "bypass log in?"
date: 2011-11-28
forum: General Help
---

### Post by Matrix01 on 2011-11-28
how to go to home screen without logging in?

---

### Post by Elfy on 2011-11-28
Edit lightdm.conf. Backup the file first.

```
sudo cp /etc/lightdm.conf /etc/lightdm.conf.bak

gksudo leafpad /etc/lightdm.conf
```

```
[SeatDefaults]
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
autologin-user=hobgoblin
autologin-user-timeout=2

allow-guest=false
```

This is mine - edit the username to suit you and the timeout, I've also disabled the guest account so if you want that leave the line out.

---

### Post by Matrix01 on 2011-11-28
[ATTACH]208123[/ATTACH]
typed command,
unable to type my passward on terminal?

> **forestpiskie said:**
> Edit lightdm.conf. Backup the file first.

```
sudo cp /etc/lightdm.conf /etc/lightdm.conf.bak

gksudo leafpad /etc/lightdm.conf
``````
[SeatDefaults]
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
autologin-user=hobgoblin
autologin-user-timeout=2

allow-guest=false
```This is mine - edit the username to suit you and the timeout, I've also disabled the guest account so if you want that leave the line out.

---

### Post by Elfy on 2011-11-28
password doesn't show in terminal - type it and enter

you need to run the commands seperately as well

---

### Post by Matrix01 on 2011-11-28
here's output,
[ATTACH]208126[/ATTACH]


> **forestpiskie said:**
> password doesn't show in terminal - type it and enter

you need to run the commands seperately as well

---

### Post by Elfy on 2011-11-28
As you have been told in another thread - run command seperately or join them with &&

---

### Post by Matrix01 on 2011-11-28
[ATTACH]208132[/ATTACH]
that did not work.

> **forestpiskie said:**
> As you have been told in another thread - run command seperately or join them with &&

---

### Post by Elfy on 2011-11-28
Can you run this and paste the result.

```
ls /etc/lightdm
```

If you get no result then 

are you running a 11.10 version?
did you upgrade it from 11.04?

Not sure if you get no result what is going on - you should be using lightdm instead of gdm I thought.

---

### Post by Matrix01 on 2011-11-29
erased

---

### Post by Matrix01 on 2011-11-29
here's how output looks like,

k@ubuntu:~$ ls /etc/lightdm
lightdm.conf              lightdm-gtk-greeter-ubuntu.conf
lightdm-gtk-greeter.conf  users.conf
k@ubuntu:~$ 



> **forestpiskie said:**
> Can you run this and paste the result.

```
ls /etc/lightdm
```If you get no result then 

are you running a 11.10 version?
did you upgrade it from 11.04?

Not sure if you get no result what is going on - you should be using lightdm instead of gdm I thought.

---

### Post by Elfy on 2011-11-29
Then the commands given should all work - try again - copy and paste them if necessary.

---

### Post by Matrix01 on 2011-12-02
i tried your code again,
and got same output.

this Xubuntu 11.10 is installed straight from Wubi. 

> **forestpiskie said:**
> Then the commands given should all work - try again - copy and paste them if necessary.

---

### Post by critin on 2011-12-02
I don't use Xubuntu 11.10 or Wubi, so don't know, but can't a user choose 'no password login' from the user/group program as they can from the other buntu's?  Or is this another issue altogether?

---

