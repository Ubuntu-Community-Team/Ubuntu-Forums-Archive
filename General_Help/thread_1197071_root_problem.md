---
title: "root problem"
date: 2009-06-25
forum: General Help
---

### Post by RastaManPower on 2009-06-25
hello guys each time i go to terminal and type   su  to go in root mode it asks me for a password that i never setup...  i tryed using blank password and my ubuntu 9.04 password but it is not workin...how come?

---

### Post by lisati on 2009-06-25
Use your normal Ubuntu admin account's password.

BTW, don't worry if it doesn't show when you type it, that's a normal Ubuntu security feature.

---

### Post by sisco311 on 2009-06-25
the root account password is locked by default.
use sudo: [uhelp]community/RootSudo[/uhelp]

---

### Post by RastaManPower on 2009-06-25
if i go to termianl and type su  it asks me for a password.. i type my password and i get this
su: Authentication failure

---

### Post by ibutho on 2009-06-25
Ubuntu works a bit differently to other distros. Read the RootSudo link posted above for more info. You need to execute any commands you wish to run as root, using sudo e.g.
```
sudo somecommand
```

---

### Post by bodhi.zazen on 2009-06-25
See the link [sisco311]("http://ubuntuforums.org/member.php?u=244665") gave you and in the meantime try :

```
sudo -i
```Use your log in password.

---

### Post by RastaManPower on 2009-06-26
ok thanx.. i got this to work but now i got a problerm.. i have only 2300 mb of free space on my ubuntu....how do i resize my widnows partition with ubuntu?? do i have to use partition magic from windows or there is a easyer way?

---

### Post by lisati on 2009-06-26
The "Try Ubuntu" option on the Ubuntu LiveCD comes with a copy of gparted (partition editor) that might be of some help.

---

### Post by RobOrr on 2009-06-26
Using the Live CD is the best way of doing a repartition in my opinion. GPartEd is very easy to use.

Whilst your Ubuntu installation does have gparted available, it cannot perform operations on the same disk that it's running on, so if your windows partition is on the same physical drive as your ubuntu partition you need the Live CD. If it's not, just load up GPartEd in your normal installation (system > administration > GPartEd)

---

