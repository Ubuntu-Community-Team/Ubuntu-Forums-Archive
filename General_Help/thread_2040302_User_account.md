---
title: "User account"
date: 2012-08-10
forum: General Help
---

### Post by concerro on 2012-08-10
I tried to set up a new account. I was able to do so, but I was never prompted for a password. The account is not an admin account. Whenever I try to switch to the new account I am prompted for password.  

I would like to know how to add a password to the account of be able to switch to the account without entering a password.

---

### Post by unevenflow on 2012-08-10
from your admin account go to system settings--->user accounts

---

### Post by concerro on 2012-08-11
> **unevenflow said:**
> from your admin account go to system settings--->user accounts
That is what I did to create the new account, but I was never prompted to create a password. I am sure there is a way to do it through the terminal, but I was hoping for an easier method.

---

### Post by Supaikoo on 2012-08-11
it isl ikely that the account may be disabled as well, I just had this problem 20min ago. Goto terminal and run the following:

sudo passwd -u <username>
sudo passwd <username>

The first line unlocks the account or makes sure that its unlocked. The second line changes the password for that username. Try that and reply. You might get a usermod message when you run 'passwd -u' just ignore it.

---

### Post by concerro on 2012-08-12
I found the answer. 
"go to "user account" again select the newly created user and and under  login options next to password click on "account disabled" to setup a  password"

I did not know that "account disabled" could be clicked on.

---

