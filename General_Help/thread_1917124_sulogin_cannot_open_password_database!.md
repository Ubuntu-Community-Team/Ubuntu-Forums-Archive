---
title: "sulogin: cannot open password database!"
date: 2012-01-29
forum: General Help
---

### Post by nkjha on 2012-01-29
[B]Error :---> sulogin: cannot open password database!
[/B]
I have this error when I use recovery mode and go to shell 

     I play with /etc/passwd  

can someone help me
  
note : if i boot normally the pc restart automatically




Thanks,
NK

---

### Post by skipi-gz on 2012-07-10
i have the same problem. i must have deleted all the passwords! i cannot boot in single user mode because it just restarts itself. i cannot use recovery mode because of the error message mentioned above. is there any other way around?

---

### Post by ldaher on 2012-09-03
Although this post was submitted a long time ago, and probably the post owner has already found a solution for this, I'd like to say that, as I've faced the same problem and I managed to fix it, I'd suggest:

- since you won't be able to access the system anyway, even the restore console through Grub menu list, boot up your system using Live CD. When questioned, choose Live, just to test it;
- once GNOME is started, open a Terminal, mount the partition where "/etc" reside into (in most cases "/" context);
- jump into etc (cd <*root mounted directory*>/etc) and search for the "passwd" file, which contains the password set for all users;
- if you find more than 1 file containing the same string, adding at the end of file name the "-" symbol, this is the file you should care about;
- for security reasons, make a copy o the original file before rename the "passwd-" into "passwd" (mv passwd- passwd);

Note: Would be wise to take advantage of using a working Terminal and perform a fsck.<*file system type*> on all partition available before restart.

I hope I could help.

---

