---
title: "I lost my right to sudo and start a root terminal by changing my username"
date: 2005-03-16
forum: General Help
---

### Post by troelssmit on 2005-03-16
Hi,

I installed ubuntu without ever being asked for a root password (afaik).

I created a user named t with password xxx.

I logged onto the system.

I was able to start a "root terminal" specifying t's password xxx.
I could never start a terminal and do a "su".

I used visudo to add t to the sudo users.

I changed the userid t to ts and the password from xxx to yyy.

- Now I can't start a root terminal - it says "child process failed -1".
- I can't sudo because the user t changed to ts and is no longer in the sudoers file.
- I can't "su root" from a terminal window - password fail with both password xxx and yyy.

I need root rights - and I am the only user of the machine, can anyone see a solution ?

The system is Ubuntu with Gnome.

---

### Post by troelssmit on 2005-03-16
Solved it using the "live" cd.
1. Called visudo on the /mnt/hda1/etc/sudoers file with a -f parameter

---

### Post by jkka on 2005-03-16
Or you could just boot to recovery mode (single)

---

### Post by Nis on 2005-03-16
You don't need to enable the root password at all.  sudo will handle all of this for you.  If you need a root terminal execute 'sudo -s' as a normal user and input your password.  I am the only user of this machine and the root user is still disabled because the above does everything I need it to.

---

