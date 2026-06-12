---
title: "Unable to access ubuntu jaunty using nomachinenx"
date: 2009-07-10
forum: General Help
---

### Post by naklinaam on 2009-07-10
Hi,
I recently installed ubuntu 9.04 64 bit on a new machine and was in the process of setting up all the servers etc that I have on the old machine this will replace.

I installed the nomachine nx (not freenx) and set up the keys as described on their site ([http://www.nomachine.com/ar/view.php?ar_id=AR01C00126](http://www.nomachine.com/ar/view.php?ar_id=AR01C00126))

When I try to connect from my XP laptop, I get an "Authentication failed for user .....". 

I know this is not an ssh issue. If I change the key used for ssh, the system does not even connect to my server.In this case, it does connect, but it is the user authentication that I am missing something on.

I have in the past got this to work successfully (I think that was using freenx and not nomachine's version).

Can someone please help me in figuring out how to enable this user to access my ubuntu box with NX.

I need to be able to access my desktop (ubuntu) from my laptop (xp). I do not need to have multiple users connected.. I will be the only one connecting over he net.

---

### Post by Peter09 on 2009-07-10
Just to check,
can you login using ssh

ssh -X <yourid>@<your ip> xterm

What do you see in the system logs?

---

### Post by naklinaam on 2009-07-10
Thanks Peter
I am able to log in using ssh and also using putty from my windows xp laptop.

The uploaded file has the output of the above command as well as screen shots of the putty screen.

---

### Post by Peter09 on 2009-07-10
The reason the Ubuntu command failed is that its a capital X

```
ssh  -X ..........
```

You need to check your NX configuration files. Also, I'm not sure but do you need to be the Group NX.

---

### Post by naklinaam on 2009-07-10
Hey peter.. thanks for helping...


Community I apologise for raising a non issue here and wasting everyone's time and effort.

The login is now working for me. 
I just did 2 things...

a) executed the code ```
sudo /usr/NX/bin/nxserver --usercheck <username>
```.
This code was giving me some error yesterday, 

b) restarted the machine today and executed the same code above. This time it worked and I got the following message```
jdoe@john-doe:/$ sudo /usr/NX/bin/nxserver --usercheck jdoe
NX> 900 Verifying public key authentication for NX user: jdoe.
NX> 900 Adding public key for user: jdoe to the authorized keys file.
NX> 716 Public key added to: /home/jdoe/.ssh/authorized_keys2.
NX> 900 Verifying public key authentication for NX user: jdoe.
NX> 900 Public key authentication succeeded.
NX> 999 Bye.

```

so my guess is that the public key was not in my authorized_keys (though I can promise I did copy the public key to my autorized_keys2 file yesterday.

Somehow I think the restart made it work fine this time round...

---

