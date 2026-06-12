---
title: "how do i use chown with plink"
date: 2010-06-01
forum: General Help
---

### Post by smay84 on 2010-06-01
Hi

I need to be able to run a set of commands using plink.  I've set it up using the public key authorization.

However when i try to set the ownership of newly created folders to the user logged in i get Operation not permitted.

I believe i know why this is.

I have created an ftp server with the main ftp user having the home location of /home/ftp.  Each user then has a folder within this folder so user1 would have the home directory of /home/ftp/user1.  

So when user1 adds files folders they have ownership as expected.  However i need this script to change ownership of the files these users upload to the server.  And the script needs to be run through plink.

Is this an impossible task?

Oh and i'm sure this is not the best way to be running an ftp server but it is required in order to make some of our legacy software work correctly.

Any help would be much appreciated.

Simon

---

### Post by dino99 on 2010-06-01
[http://manpages.ubuntu.com/manpages/lucid/man1/plink.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/plink.1.html)

---

### Post by smay84 on 2010-06-01
yes i have read the documentation.  This is less about plink and more about getting ownership of files uploaded by other users.

---

### Post by dino99 on 2010-06-01
sudo chown user:user /path

set your real data

[http://manpages.ubuntu.com/manpages/lucid/fr/man1/chown.1.html](http://manpages.ubuntu.com/manpages/lucid/fr/man1/chown.1.html)

---

### Post by smay84 on 2010-06-01
sorry i don't think i've made myself clear.  I know how to use chown and plink.  However i don't know how to get it to do the following:

sudo chown myuser myfolder

without asking for a password.  That is why i setup key authorization.  Plink will run an automated script which needs to set the ownership of the newly created folders.

---

