---
title: "Can't delete or modify .bashrc"
date: 2010-04-18
forum: General Help
---

### Post by Morfi777 on 2010-04-18
rm: cannot remove `.bashrc': Operation not permitted

* ALL other files in /home/admin directory are able, only this one.
* can't even change own, grp, just nothing
* no matter if i'm doing it from root or admin

inside this file there is:
> export PATH=$PATH:/home/administrator/Downloads/ns-allinone-2.34/bin:/home/administrator/Downloads/ns-allinone-2.34/tcl8.4.18/unix:/home/administrator/Downloads/ns-allinone-2.34/tk8.4.18/unix


REGARDS

---

### Post by Morfi777 on 2010-04-18
at least one time help me with some sollution

---

### Post by wojox on 2010-04-18
Can't you just open the file and delete that line in your quote?

---

### Post by klemes on 2010-04-18
Did you try:

sudo chown your:username:your_group(same) ~/.bashrc  ???

also :

sudo chmod 770 ~/.bashrc

---

### Post by Morfi777 on 2010-04-18
@wojox:
Nope cause I will not be able to save it :/

@klemes:

admin@server4:~$ sudo chown admin:admin /home/admin/.bashrc
chown: changing ownership of `/home/admin/.bashrc': Operation not permitted


admin@server4:~$ sudo chown 770 /home/admin/.bashrc
chown: changing ownership of `/home/admin/.bashrc': Operation not permitted

---

### Post by KaiJordanDay on 2010-04-18
You need to sign in with root account.

> su

---

### Post by Morfi777 on 2010-04-18
Same, even if I log in as root. Operation not permitted :/

---

### Post by Drenriza on 2010-04-18
Why do you want to delete that file?

Can you do an ```
 ls -lah
``` on the file and tell us the permissions?

---

### Post by KaiJordanDay on 2010-04-18
Very very odd.

Goto Users + Groups -> Unlock (enter normal user pass) -> Click or Root + then Edit -> set the password, and re-type password -> Click ok etc etc. -> restart

Then try logging in as root from the terminal again afterwards.

> su

Sorry in advance if you have already done this.

---

### Post by Morfi777 on 2010-04-18
I installed fresh version without any user, just root.

I added admin manually and I wanted to add custom .bashrc to have coloured ssh console. But I put wrong line, copied from some topic on this forum and it doesn't work properly. I wanted to copy .bashrc (same as in /root/ here) but I see that operation not permitted.

> **KaiJordanDay said:**
> Very very odd.

Goto Users + Groups -> Unlock (enter normal user pass) -> Click or Root + then Edit -> set the password, and re-type password -> Click ok etc etc. -> restart

Then try logging in as root from the terminal again afterwards.



Sorry in advance if you have already done this.

I don't have graphical NX Server installed. this is remote server I connect via putty. Is there any option to do this via putty?

---

### Post by Serpher on 2010-04-18
The root account in Ubuntu by default it locked. Before you do that use the command:

```
$sudo passwd
```

If you're still not permitted perhaps something in /etc/sudoers is messed up.

---

### Post by KaiJordanDay on 2010-04-18
Tried using nautilus folders to copy and remove?

---

### Post by Morfi777 on 2010-04-18
@Serpher
But I CAN log in on root. I used "passwd" as root before.

@KaiJordanDay
What is that? :(

---

### Post by Serpher on 2010-04-18
@KaiJordanDay
What is that? :(

```
$gksu nautilus
```

---

### Post by Morfi777 on 2010-04-18
I can't open GUI apps in putty :(

I heard that there is some option with this X11 but I never acomplished it :/

---

### Post by Serpher on 2010-04-18
> **Morfi777 said:**
> I can't open GUI apps in putty :(

I heard that there is some option with this X11 but I never acomplished it :/

Well this changes everything. If you're not an admin of that server, you are probably not permitted to do things the root account would do. What is the server even running?

---

### Post by Morfi777 on 2010-04-18
:o ?

I do. I have option to fully reinstall my system which I have done.
I chosen clean instalation.

I got email with root password. After that I created admin account.

Actually I can take risk and work on root account ommiting admin. I'll not run any application except 2 which I was running always and I will keep extreme caution when executing commands.

Maybe instead of making this admin work, I will just switch to root.

**QUESTION:**
Tell me please, people say that working on root is like playing with knife. Maybe you will not harm yourself but there is big chance you will.

What I can do accidentally on root (except running rm -R *.* or running some app in wine for example) ?

---

### Post by Morfi777 on 2010-04-18
up, question in #17 :P

---

