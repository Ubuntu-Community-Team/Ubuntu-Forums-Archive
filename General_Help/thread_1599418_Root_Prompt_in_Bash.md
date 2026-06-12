---
title: "Root Prompt in Bash"
date: 2010-10-17
forum: General Help
---

### Post by hewjr1000 on 2010-10-17
I changed Bash Prompt to the following

Hewjr1000~$

This is the prompt when I sudo su

root@hewjr1000:/home/hewjr1000#

How do I change root prompt to the following

Root@Hewjr1000~$

Henry

---

### Post by kerry_s on 2010-10-17
then you won't know where your at.

anyways just cd & it should put you to the root directory.

edit: i think i might be misunderstanding.
it looks more like you want to shorten /home/hewjr1000 to just ~/ i think you can do that in ~/.bashrc

check "man bash"

---

### Post by sisco311 on 2010-10-17
The preferred method for starting a root shell in Ubuntu is **sudo -i**. See: [uhelp]community/RootSudo[/uhelp] and [unutbu's post](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4).  

You can change the root user's bash prompt the same way you changed your user's prompt.

---

### Post by hewjr1000 on 2010-10-17
Thank you very much, I believe I've got it now.

---

### Post by Agent ME on 2010-10-17
When you're logged in as (or sudo'd into) root, ~ refers to /root, not your user's directory. Running "HOME=/home/myuser" will change that but if you do that, programs you run as root may write files to your user's directory that your user won't have ownership of. Not a good idea really.

---

### Post by hewjr1000 on 2010-10-17
I see what your saying I guess I will leave it alone.

Henry

---

