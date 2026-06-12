---
title: "Prelude-lml post installation script error"
date: 2010-11-04
forum: General Help
---

### Post by Robbyx on 2010-11-04
I reinstalled prelude-lml but I still get error messages when software updates are run. On the reinstall in synaptic I had this error message:

> E: prelude-lml: subprocess installed post-installation script returned error exit status 1


Any one know what it means?

---

### Post by Robbyx on 2010-11-06
Does anyone know what I should do about this error message. It means that every-time there is a software update there is an error message about prelude-lml.

---

### Post by Zhukov on 2010-11-10
Guys, here is the fix:

sudo prelude-admin register "prelude-lml" "idmef:w" 127.0.0.1 --uid 0 --gid 0

I used the localhost as the manager address. This should be added to post-install script.

=) Enjoy!

Posted bugfix here as well:
[https://bugs.launchpad.net/ubuntu/+source/prelude-lml/+bug/628692](https://bugs.launchpad.net/ubuntu/+source/prelude-lml/+bug/628692)

---

### Post by Robbyx on 2010-11-10
> **Zhukov said:**
> Guys, here is the fix:

sudo prelude-admin register "prelude-lml" "idmef:w" 127.0.0.1 --uid 0 --gid 0

I used the localhost as the manager address. This should be added to post-install script.

=) Enjoy!

Posted bugfix here as well:
[https://bugs.launchpad.net/ubuntu/+source/prelude-lml/+bug/628692](https://bugs.launchpad.net/ubuntu/+source/prelude-lml/+bug/628692)


The solution is not easy to apply. 

First I did this as proposed by you:

> rob@rob-desktop:~$ sudo prelude-admin register "prelude-lml" "idmef:w" 127.0.0.1 --uid 0 --gid 0
[sudo] password for rob: 
Generating 2048 bits RSA private key... This might take a very long time.
[Increasing system activity will speed-up the process].
Generation in progress... X+++++O+++++O


You now need to start "prelude-admin" registration-server on 127.0.0.1:
example: "prelude-admin registration-server prelude-manager"

Enter the one-shot password provided on 127.0.0.1: 
Confirm the one-shot password provided on 127.0.0.1: 
Enter the one-shot password provided on 127.0.0.1: 




I did not know anything about a one shot password and so did this next:

> 
rob@rob-desktop:~$ sudo prelude-admin registration-server prelude-manager
[sudo] password for rob: 
* WARNING: no --uid or --gid command line options were provided.
*
* The profile will be created under the current UID (0) and GID (0). The
* created profile should be available for writing to the program that will
* be using it.
*
* Your sensor WILL NOT START without sufficient permission to load the profile.
* [Please press enter if this is what you intend to do]

Generating 2048 bits RSA private key... This might take a very long time.
[Increasing system activity will speed-up the process].
Generation in progress... X.+++++O........+++++O

The "gtn5t4fa" password will be requested by "prelude-admin register"
in order to connect. Please remove the quotes before using it.

Generating 1024 bits Diffie-Hellman key for anonymous authentication...+++++.++++++++++++++++++++++++++++++..+++++.+++++.+++++.++++++++++++++++++++..++++++++++.+++++.++++++++++++++++++++++++++++++.+++++++++++++++++++++++++++++++++++++++++++++.....>+++++.................<+++++......>.+++++...................................................................................+++++O++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++^^^
Waiting for peers install request on 0.0.0.0:5553...



the second terminal result  "Waiting for peers install request on 0.0.0.0:5553..." is hanging.

I do not know what to do next.

Robin

---

### Post by Zhukov on 2010-11-11
Ok, sorry, my explanation was not so good :)

Let's see if I can explain it now.

In my configuration of prelude I set it to run on 127.0.0.1:5553, thus meaning that I defined the port to use.

Don't know if it is relevant, but in the conf file they stated to introduce the address as well as the port, so I just ended picking this one.

I caught the "solution" by doing "tail /var/log/syslog", and there was an error about some missing profile for "prelude-lml", thus the command I referred on my previous post.

In order to add the profile you need this two-stage process, the prelude-admin register command and the actual prelude-admin server, in my case running on 127.0.0.1:5553.

I ended up running these commands with actual root, not sudo (had some problems with some files, was the quick and easy solution, not sure if it had something to do).

I also ran across some problems due to the fact that the port 5553 was already being used by a previous instance (gave me an address already in use error), so a nmap list showed me what was up and I killed the process (just in case you end up with the same problem).

So anyway, run the "prelude-admin register …" on shell 1, and on shell 2 run "prelude-admin registration-server …".

Shell 1 will ask for a password that is given by shell2, copy paste it and hit enter. Confirm the password, and the go back to shell2, and there is a prompt asking if you want to accept this new registration.

This should do the trick.

Any problems that may arise:

-> Maybe the port is actually necessary
-> Check with nmap if something is creating conflicts
-> Run it as root
-> tail /var/log/syslog is your friend

Hope it works for you, let us know how it goes.

---

