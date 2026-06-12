---
title: "Forgot My admin Password"
date: 2009-12-12
forum: General Help
---

### Post by PastorOk3 on 2009-12-12
I keep reading unbutu website for the answer on how to reset the admin password but on my dell mini 9 when I hit esc only the boot menu comes up no grub menu comes up it only gives me options of the drives I want to boot from or if I want to boot from a Cd please help I am dieing I am new to linux and I am about read to throw this dell mini and it's operating system out the window. oh i think it is the 8.04 version again help please!

---

### Post by ubhi on 2009-12-12
cant get your question, which admin password u talking bout, its root password or user from you login.. 
& where ubuntu stuck exactly...

---

### Post by sahabcse on 2009-12-12
Select the recovery mode in option in grub, It load to the single user mode.

There type

#passwd 

For changing the root user password

---

### Post by lisati on 2009-12-12
> **sahabcse said:**
> Select the recovery mode in option in grub, It load to the single user mode.

There type

#passwd 

For changing the root user password

Careful! "login as root" tutorials are discouraged here.

---

### Post by ubhi on 2009-12-12
if you remember your username then type

passwd username

then it prompt you for new unix password

---

### Post by Primefalcon on 2009-12-12
try what ubhi said first, enabling the root account is becoming more and more the big no no in Linux land, thats why sudo and gksudo were made, to relegate having to use it

---

### Post by sisco311 on 2009-12-12
> **PastorOk3 said:**
> I keep reading unbutu website for the answer on how to reset the admin password but on my dell mini 9 when I hit esc only the boot menu comes up no grub menu comes up it only gives me options of the drives I want to boot from or if I want to boot from a Cd please help I am dieing I am new to linux and I am about read to throw this dell mini and it's operating system out the window. oh i think it is the 8.04 version again help please!

Hi and welcome to the forums!

If you are using Ubuntu 9.10 (Karmic Koala), then you have to hold down the Shift key during the bootup. 

If you are using an earlier release, then select and boot the default drive from the boot menu, immediately after that press Esc (repetitively) until the grub menu shows up.

Then follow this instructions: [http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by Physical Hook on 2009-12-12
> **Primefalcon said:**
> try what ubhi said first, enabling the **root account is becoming more and more the big no no in [COLOR=Red]Ubuntu[/COLOR] land**, thats why sudo and gksudo were made, to relegate having to use it

[COLOR=Silver][-- edited --][/COLOR]

Fedora, OpenSUSE, Arch, FreeBSD, Mandriva, .. vs. Ubuntu. You must be joking.

---

### Post by Primefalcon on 2009-12-12
> **Physical Hook said:**
> [COLOR=Silver][-- edited --][/COLOR]

Fedora, OpenSUSE, Arch, FreeBSD, Mandriva, .. vs. Ubuntu. You must be joking.
Actually a lot of the others even red hat (the system I work with) had sudo setup rather than using root, sudo really is becoming more of the norm

---

### Post by Leppie on 2009-12-12
Debian, the base for Ubuntu systems, uses the root account normally. I understand it if Ubuntu wants to keep of policy of not enabling the root account (maybe to avoid many unrecoverable newby mess ups?), but I don't understand why they try to "forbid" using it.

---

### Post by sisco311 on 2009-12-12
> **Leppie said:**
> Debian, the base for Ubuntu systems, uses the root account normally. I understand it if Ubuntu wants to keep of policy of not enabling the root account (maybe to avoid many unrecoverable newby mess ups?), but I don't understand why they try to "forbid" using it.

It's well explained in the [thread=716201]Forum policy on log-in-as-root tutorials[/thread].

---

### Post by snowpine on 2009-12-12
Hi PasterOK3, this thread has turned into an interesting debate, but nobody is really helping you. :)

The Dell Mini 9 does not use "regular" Ubuntu; it comes pre-installed with a special "Dell Remix." You can follow these directions to boot into recovery mode:

[https://help.ubuntu.com/community/DellMini9#Booting%20into%20Recovery%20mode](https://help.ubuntu.com/community/DellMini9#Booting%20into%20Recovery%20mode)

Then, you can reset your password following this tutorial (skip the part about getting into recovery mode, obviously):

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Good luck! (and I agree with the posters above; forget about a root password; just use 'sudo' because it's the way Ubuntu was designed.)

---

### Post by PastorOk3 on 2009-12-21
hello, thankyou everyone after many unsucessful attempts I did it thanks to you all you where quite helpful:guitar:

---

### Post by prateek.konojya on 2011-01-24
> **ubhi said:**
> if you remember your username then type

passwd username

then it prompt you for new unix password



this workd:p

---

