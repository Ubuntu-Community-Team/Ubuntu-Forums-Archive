---
title: "Move file in terminal"
date: 2012-08-06
forum: General Help
---

### Post by P4770N on 2012-08-06
Hello,
 
I just wonder how i can move a file in terminal. I've tried to use the "mv" command and the file in the directory i'm currently are in. And then i don't understand what more text i've have to write on the line.
 
This is how my terminal looks like:
 
"root@test-vm:/home/test/Documents# mv common.txt ~/example"
 
But how do i move this to a folder called "example" in the root area, because that line doesn't work. It gives me an error:
 
"mv: cannot stat 'common.txt' : no such file or directory" - Which it is!?
 
I'm very grateful for any answers about this.

---

### Post by cortman on 2012-08-06
You do know that the terminal is case-sensitive?
Also, when you're logged in as root you are working in root's /home directory, not your own.
If you're trying to move files in your own home directory, there is no reason to be root to do that.
As for the command, have you tried typing "mv com" + tab to tab-complete?

---

### Post by P4770N on 2012-08-06
> **cortman said:**
> You do know that the terminal is case-sensitive?
Also, when you're logged in as root you are working in root's /home directory, not your own.
If you're trying to move files in your own home directory, there is no reason to be root to do that.
As for the command, have you tried typing "mv com" + tab to tab-complete?
 
Yes i know that the terminal is case-sensitive. I'm now the "test" user instead of the sudo root. Why i choose to use the sudo root was because i can't access my folders in root in the "graphic-mode" but i can in the terminal (i know why, but not how i can access these). Or should i install the files with "apt-get" in a area that can be accessed by the test accounts instead to prevent risks of the system? 
 
Yes i have tried typing that and with the tab. So if i want to get that file into the folder "/example" what is the full command for this operation?

---

### Post by drmrgd on 2012-08-06
It may help if you give a quick explanation (beyond just moving files) as to what you're trying to do.  Apart from moving files, it looks like you're also trying to install something.  It's a little confusing.

In order to use the file browser as root, you'd have to run:

```
gksudo nautilus
```

That will allow you to use the file browser as root.

The error you're getting "...cannot stat common.txt..." is either a naming or permissions problem.  To help clear it up, please run:

```
ls -l /home/test/Documents/
```

This will tell us if the file is really there and what permissions are set.

Finally, you don't need to switch user to root to do things.  You can (and should) just use elevated privileges to run individual commands.  So, let's assume that common.txt is in /home/test/Documents and you want to move it to /example (which by the way is different than ~/example...be careful!).  Since / is owned by root (and depending on how you make /example, that directory may be as well), you'd run:

```
test@test-vm:/home/test/Documents# sudo mv common.txt /example/
```

---

### Post by P4770N on 2012-08-06
> **drmrgd said:**
> It may help if you give a quick explanation (beyond just moving files) as to what you're trying to do. Apart from moving files, it looks like you're also trying to install something. It's a little confusing.
 
In order to use the file browser as root, you'd have to run:
 
```
gksudo nautilus
```
 
That will allow you to use the file browser as root.
 
The error you're getting "...cannot stat common.txt..." is either a naming or permissions problem. To help clear it up, please run:
 
```
ls -l /home/test/Documents/
```
 
This will tell us if the file is really there and what permissions are set.
 
Finally, you don't need to switch user to root to do things. You can (and should) just use elevated privileges to run individual commands. So, let's assume that common.txt is in /home/test/Documents and you want to move it to /example (which by the way is different than ~/example...be careful!). Since / is owned by root (and depending on how you make /example, that directory may be as well), you'd run:
 
```
test@test-vm:/home/test/Documents# sudo mv common.txt /example/
```
 
Thank you for your great answer and i'm sorry for not being clear what i asked about. This helped me a lot.

---

