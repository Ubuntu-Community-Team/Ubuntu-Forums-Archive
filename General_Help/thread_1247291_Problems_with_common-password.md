---
title: "Problems with common-password"
date: 2009-08-22
forum: General Help
---

### Post by btaylor101 on 2009-08-22
I am having issues getting cracklib to be used in the common-password config.I am running Ubuntu 8.04. My current config is 
> 
password required	  pam_cracklib.so retry=3 minlen=8 difok=3
password required	  pam_unix.so use_authtok nullok md5


I have been creating and deleting a user called "test" to verify that everything is working as expected. I enter the password "test" expecting it to fail and what i get is 
> 
New UNIX password: 
BAD PASSWORD: it is too short
Retype new UNIX password: 
passwd: password updated successfully


It seems like there is something overiding cracklib checks, but I am at a loss of what is doing this.

Any help would be greatly appreciated.

---

### Post by btaylor101 on 2009-08-22
Just found a post that explained the root does not follow the cracklib password guidelines. Tried it as a sudo user and everything worked as expected.

---

