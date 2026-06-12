---
title: "'su' rejects password. How to set one?"
date: 2010-02-28
forum: General Help
---

### Post by ffrr on 2010-02-28
Hi all,

I recently installed Ubuntu 9.10 from a UBS stick on a Dell Latitude E6500. I was required (or asked?) to choose a password. What kind of password that would be wasn't explained. I chose one and so I now have one password. I need it to start the machine. It also serves in conjunction with the command modifier 'sudo'. The command 'su', however, rejects it. So, it looks like nobody can login as root, which is a major deficiency that should be corrected. I have no clue how I would do that other than reinstalling the whole system (and possibly ending up again where I am now.) Suggestions highly welcome.

Frederic

---

### Post by rcayea on 2010-02-28
Give me a second to type this up. I might be able to help.

---

### Post by rcayea on 2010-02-28
Instead of trying to give you just the commands, I thought I would post this whole link because if you do read it, it is very educational. I hope it helps. If not, let us know and someone here, me too, will try to give you exact info. 

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo)

Good Luck.

---

### Post by asmoore82 on 2010-02-28
Hello "ffrr" and **WELCOME**!

You are obviously *not* new to GNU/Linux but obviously *are* new to Ubuntu.

Ubuntu strictly adheres to the `sudo` philosophy and as such
always ships with the root account locked with no password.

It is the policy of the Ubuntu Forums Community *not* to post the
commands to enable the root account as it can cause new users
looking for help much much more trouble than it's worth.

See: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Paperlantern on 2010-02-28
This is good information as i am familiar with Debian and a couple other distros and was baffled at first by the authentication as well. If I am logged in as me, why does it want to reauthenticate... me? I figured out it needed my password and not some unset root password only because i noticed the setup didnt ask me for one.

Bizarre, but good tip. Thanks.

---

### Post by nerdy_kid on 2010-02-28
i think sudo -i serves the same purpose?

---

### Post by ffrr on 2010-03-01
I am totally overwhelmed by so much good advice. Thank you all! I am now studying the excellent reference "http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo" which rcayea suggested. It is an immense comfort to set a system up with a complete understanding of every detail. 

Frederic

---

