---
title: "Dual boot and security"
date: 2010-07-15
forum: General Help
---

### Post by PhotonicGuy on 2010-07-15
I want too create a dual boot Windows 7 Ultimate (64 bit) and Ubuntu (64bit).

I know there are many tutorials how to do this but I want something special.


The boot loader appear. Will be only one password field, no OS names.

If I introduce a password will boot in Linux, if I introduce  another password will boot in Ubuntu.

Also in Ubuntu, you can see windows partitions only if you introduce a password (root or power user).

---

### Post by nitstorm on 2010-07-15
> Also in Ubuntu, you can see windows partitions only if you introduce a  password (root or power user).

look into these links for this, u need to edit fstab so that the paritions that get mounted need root ownership
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Mark Phelps on 2010-07-15
> **PhotonicGuy said:**
>  ...If I introduce a password will boot in Linux, if I introduce  another password will boot in Ubuntu...


The only way I think this will work is if you have a script that runs during boot and selects one of two boot options, depending on the password you enter.

Problem I see is that the script will have to compare the password you enter to two stored passwords -- and since I believe that the stored passwords have to be unencrypted (in order to do the compare) -- this, essentially, makes your system LESS secure.  Why? Because you're storing your passwords, unencrypted, on your system.

If you're so paranoid that you're afraid of anyone with physical access to your box then obtaining access to either of your OS's, once they have physical access to your box, any security you've added is essentially, a waste of time.

... Just my opinions ... others may differ.

---

### Post by PhotonicGuy on 2010-07-16
Thanks for your replies and nitstorm for the links.

Mark I'm not 'very paranoid' ;), I was just curios if this is possible.

I'm searching for boot loader that can do this.

---

