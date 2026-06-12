---
title: "undo my stupidity !"
date: 2010-03-15
forum: General Help
---

### Post by kernelnewbie1 on 2010-03-15
Dear friends , 
please suggest some solution for my problem ..

System was fine with :
Ubuntu 9.04 (had also installed kde )

then....
I wanted to try some change to gdm  so i downloaded gdm 
while building it , it asked "PAM" libraries to be installed
so i installed PAM ... but ignored the instruction to reinstall 
SHADOW (library i guess..) , 

Now :
on booting system i get login menu  but i am not able to login , it says some critical error occured


so please help me to :
1) install new copy of UBUNTU and remove old 
 or 
2) suggest a way to fix the problem


ps :
1) i can log into system through live cd
2) i can use recovery mode boot and log into terminal as root
 (startx is not working from this terminal..)


Please ... help me .

---

### Post by mechro on 2010-03-15
When you get to the login page can you choose a KDE session?

---

### Post by kernelnewbie1 on 2010-03-15
i tried dat too...
but no luck... i get an err mgs saying

"Critical error , check kde log(s) or contact you system administrator (thats me , lol)"

---

### Post by mechro on 2010-03-15
I don't know enough to show you how to find which packages you installed so my first suggestion is...

In recovery mode terminal do...

```
sudo apt-get remove gdm
```

You might also need to do the same with the libraries you installed but try that first.

Edit... wait a minute... how did you login before? Was it not gdm?

---

### Post by ronnielsen1 on 2010-03-15
>  or contact you system administrator (thats me , lol)"

doesn't that suck when that happens

I would think you already had gdm installed since you had a working ubuntu before you installed kde. Just because you added a wm doesn't mean you lose the others.

---

### Post by kernelnewbie1 on 2010-03-16
Well , i reinstalled Ubuntu , 
Bye to PAM !

>how did u log in
on grub menu u have two options for same kernel , one is normal other one for recovery
boot through recovery option,
you can log in only as root from there , but you dont get a gui :)

---

### Post by mechro on 2010-03-16
> **kernelnewbie1 said:**
> Well , i reinstalled Ubuntu , 
Bye to PAM !

>how did u log in
on grub menu u have two options for same kernel , one is normal other one for recovery
boot through recovery option,
you can log in only as root from there , but you dont get a gui :)

What I meant was that your original Login system was gdm (unless you changed it to kdm for the KDE desktop). If you had gdm installed and working why did you "try some change to gdm so i downloaded gdm"?

Example... this is gdm...

[IMG]http://resa.linux-hardcore.com/wp-content/uploads/2009/10/KarmicKoala-NewLoginScreen-Part2-SunVirtualBox.png[/IMG]

---

### Post by kernelnewbie1 on 2010-03-16
> What I meant was that your original Login system was gdm (unless you changed it to kdm for the KDE desktop). If you had gdm installed and working why did you "try some change to gdm so i downloaded gdm"?

Well, i thought i could fix some bugs in gdm , but never dreamt that i would end up formatting my system !

any ways, thank you all for replying to my post :)

---

### Post by mechro on 2010-03-16
No problem. Happy Ubunting!

---

### Post by soltanis on 2010-03-16
In the future, when you screw up your system so that it can't boot (i.e. I moved the sudoers file, I messed up the shadow file, etc) you can use a LiveCD to boot. From there, mounting your partition is simple, then you can make the necessary repairs to your system.

The only case in which this wont work is if you encrypt your system, then render it unbootable by messing up the encryption or forgetting your passphrase. So don't do either. If you do remember your passphrase though you can still boot.

---

