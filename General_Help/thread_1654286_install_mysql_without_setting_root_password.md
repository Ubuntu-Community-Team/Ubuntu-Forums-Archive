---
title: "install mysql without setting root password"
date: 2010-12-28
forum: General Help
---

### Post by austinium on 2010-12-28
Hi,

Is there any way i could install mysql without setting the password for the root account during installation? preferably using the command line.

I am trying this on Ubuntu 10.04.

Thanks

---

### Post by indytim on 2010-12-28
yes

I just finished installing LAMP on my new Mint 10 ops.  

1.  Install tasksel
2.  At terminal:
> 
$sudo tasksel


3.  Check the LAMP (space bar), tab down to OK
4.  When you are prompted for the password during the install ( I think 3x), just tab to the  Ok button and <Enter>

IndyTim / DataMan

---

### Post by austinium on 2010-12-28
hi,

thanks for your reply. i made a mistake in the way i phrased the question. i already have Ubuntu 10.04 installed, iam trying to find a way by which i can install mysql-server & client without having to set the password for the root account at the time of package installation via command line.

thanks

---

### Post by burton247 on 2010-12-28
Why would you want to do this?

I don't know how to do it like you want but could you just set up that root password. Then create a new user without a password and grant it all privileges. I don't know why you would want an unprotected database though

---

### Post by austinium on 2010-12-28
thanks burton247, indytim. I'll probably do as burton247 said, stick with a root password.

I am working on customizing Ubuntu for app deployment, this just happened to be part of it.

thanks again :)

---

