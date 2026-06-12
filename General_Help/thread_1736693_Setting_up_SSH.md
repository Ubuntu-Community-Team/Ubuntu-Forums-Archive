---
title: "Setting up SSH"
date: 2011-04-22
forum: General Help
---

### Post by dangfrick on 2011-04-22
Hello all,

I am trying to set up ssh on my computer for remote access. I followed this guide [http://www.jonathanmoeller.com/screed/?p=1585](http://www.jonathanmoeller.com/screed/?p=1585) to set it up. 

So after I did all that, I tried to ssh into my own computer, from my computer. 

ssh username@computername

It says

The authenticity of host 'hostname (::1)' can't be established.
RSA key fingerprint is 0c:84:91:83:43:97:1d:c4:89:f7:08:8b:85:fd:58:f3.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'computername' (RSA) to the list of known hosts.
username@computername's password: 
Permission denied, please try again.

I did not make a password (at least I don't think I did) for this username, so why is it asking me for one? And how can I get the ssh to work?

Thanks.

---

### Post by sanguinoso on 2011-04-22
ssh authenticates with either passwords or keys. If you haven't set up a public/private key pair you need to setup a password for the account you're trying to log in with.

---

### Post by dangfrick on 2011-04-22
If you don't mind, how do I do this? Or could you point me in the direction of a helpful source?

---

### Post by hwttdz on 2011-04-22
To set a password for a user:
sudo passwd username

To set up key exchange:
[http://www.csua.berkeley.edu/~ranga/notes/ssh_nopass.html](http://www.csua.berkeley.edu/~ranga/notes/ssh_nopass.html)
[http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html](http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html)

there's also a script here to do the key exchange for you (let me know if you have any issues with it):
[http://astoryworthtelling.wordpress.com/2010/02/26/easy-passwordless-ssh/](http://astoryworthtelling.wordpress.com/2010/02/26/easy-passwordless-ssh/)

I like to have both a password and key exchange.

---

### Post by Joe of loath on 2011-04-22
Your account will have a password, Linux doesn't allow you to set one without.

---

### Post by sanguinoso on 2011-04-22
> **Joe of loath said:**
> Your account will have a password, Linux doesn't allow you to set one without.

Linux in general certainly does, on one of my Red Hat machines the git user doesn't have a password. Does ubuntu prohibit having an account with no password?

---

### Post by Joe of loath on 2011-04-22
Arch doesn't let me create a new user without a password, but I don't have access to a non-critical Ubuntu box to test it on.

---

