---
title: "Recovery Mode..."
date: 2006-05-30
forum: General Help
---

### Post by mohoso on 2006-05-30
When i startup ubuntu in the 'Recovery Mode' i am met with

root@ubuntu:~#


this stumps me every time and i dont know what command to type to start up ubuntu.

---

### Post by Gustav on 2006-05-30
Why are you starting in recovery mode?

(it's supposed to be like that)

---

### Post by mohoso on 2006-05-30
Well Ubuntu doesn't start normally so i thought that i would need to try a different approach.

---

### Post by hw-tph on 2006-05-30
"Recovery mode" is just a fancy name for Linux in single user mode. You are root, you can do pretty much everything - filesystem maintenance, set up software, clean up some mess you have accidentally made. It is not meant for day-to-day use, just - like the name implies - as a recovery option.


Håkan

---

### Post by Gustav on 2006-05-30
What happens when you try to start in the "normal" mode?

---

### Post by nocturn on 2006-05-30
You're already in Ubuntu,  just in a command shell as root.

This mode is for recovery purposes so most services and the GUI are disabled as they are often what you'll be wanting to troubleshoot.

---

### Post by mohoso on 2006-05-30
i posted a thread only minutes ago titled

"Startup problem!!"

in there it explains why i cant startup ubuntu normally.

---

### Post by az on 2006-05-30
To go from recovery mode (runlevel  1) to desktop mode (runlevel 2), run

init 2

---

