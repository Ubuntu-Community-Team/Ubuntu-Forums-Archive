---
title: "eye of gnome never opens"
date: 2011-11-03
forum: General Help
---

### Post by nekroskoma on 2011-11-03
when i try to open eog the process starts but the window itself never opens

in the terminal it just stalls after I enter the command and in the system monitor it has futex_wait_queue_me in the waiting channel and the the program is sleeping while using no ram or cpu i usually have to kill it because telling to end doesn't usually work

im using 11.10 64 bit

---

### Post by Rabreu on 2011-12-13
Fix released:

eog (3.2.2-2ubuntu3) precise; urgency=low

  * debian/patches/git_no_glib_lock.patch:
    - git patch to fix issues with the new glib serie
 -- Sebastien Bacher <email address hidden>   Mon, 05 Dec 2011 18:32:02 +0100


Download binary distribution in here:

[https://launchpad.net/ubuntu/precise/i386/eog/3.2.2-2ubuntu3](https://launchpad.net/ubuntu/precise/i386/eog/3.2.2-2ubuntu3)

---

