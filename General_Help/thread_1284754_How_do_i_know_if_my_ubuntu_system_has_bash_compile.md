---
title: "How do i know if my ubuntu system has bash compiler?"
date: 2009-10-07
forum: General Help
---

### Post by dandeliondream on 2009-10-07
Hi
 
I'm a newbie. How do i know if my ubuntu system has bash compiler?

---

### Post by bigboy_pdb on 2009-10-07
I don't think there is such a thing as a bash compiler.

If you want to check if bash is installed open a terminal (Applications -> Accessories -> Terminal) and type "which bash" and press enter. It should display where the bash program is located.

To see what shell you're using open the "Users and Groups" window (System -> Administrator -> Systems and Groups), select your account, and click the "Properties" button. In the window that appears, click the "Advanced" tab. There will be a field that displays which shell you are using (and it should be the same as what the command "which bash" returned).

---

### Post by kavon89 on 2009-10-07
BASH stands for the Bourne Again SHell. It's an interpreted language, there is no compiling done.

Also, it is the default shell in Ubuntu, so you have it unless you changed something.

---

### Post by barthel on 2009-10-07
> **kavon89 said:**
> BASH stands for the Bourne Again SHell. It's an interpreted language, there is no compiling done.

Also, it is the default shell in Ubuntu, so you have it unless you changed something.

Not quite. Bash is the default user shell (specified in /etc/passwd), but /bin/sh is symlinked to dash. As a result, dash is the actual default shell.

(When dash was introduced as the sh replacement, I had to go through my scripts and specify bash explicitly when I needed its features.)

---

