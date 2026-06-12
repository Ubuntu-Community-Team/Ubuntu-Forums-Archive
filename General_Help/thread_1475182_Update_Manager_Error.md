---
title: "Update Manager Error"
date: 2010-05-06
forum: General Help
---

### Post by Morganza on 2010-05-06
Hello,

When i run update manager an error occurred:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3AD52A40B98E84D3

---

### Post by WorMzy on 2010-05-06
Try going to: System -> Administration -> Software Sources, and changing the download server.

---

### Post by wojox on 2010-05-06
Here you need the keys imported:

```
for i in `sudo aptitude update 2>&1 | grep NO_PUBKEY | awk '{print $NF;}'`; do sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys $i; done
```

---

### Post by Morganza on 2010-05-06
Hi, 

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE
gpg: requesting key 881574DE from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 3AD52A40B98E84D3
gpg: requesting key B98E84D3 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by Morganza on 2010-05-06
> **wojox said:**
> Here you need the keys imported:

```
for i in `sudo aptitude update 2>&1 | grep NO_PUBKEY | awk '{print $NF;}'`; do sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys $i; done
```

I have this result:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE
gpg: requesting key 881574DE from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 3AD52A40B98E84D3
gpg: requesting key B98E84D3 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by Morganza on 2010-05-06
> **WorMzy said:**
> Try going to: System -> Administration -> Software Sources, and changing the download server.

Not work, ty anyway :)

---

### Post by wojox on 2010-05-06
Well I've never had to run that but I saw it in launchpad one time and it looked cool. :lolflag:

Copy and paste these two commands into the terminal:

```
gpg --keyserver subkeys.pgp.net --recv 6E871C4A881574DE
```

```
gpg --export --armor 6E871C4A881574DE | sudo apt-key add -
```


Then do it for the other one but substitute the numbers.

---

### Post by Morganza on 2010-05-06
> **wojox said:**
> Well I've never had to run that but I saw it in launchpad one time and it looked cool. :lolflag:

Copy and paste these two commands into the terminal:

```
gpg --keyserver subkeys.pgp.net --recv 6E871C4A881574DE
```


```
gpg --export --armor 6E871C4A881574DE | sudo apt-key add -
```


Then do it for the other one but substitute the numbers.

:( 

gpg --keyserver subkeys.pgp.net --recv 6E871C4A881574DE
gpg: requesting key 881574DE from hkp server subkeys.pgp.net
gpgkeys: key 6E871C4A881574DE not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


omg... :popcorn:

---

### Post by wojox on 2010-05-06
> **Morganza said:**
> :( 

gpg --keyserver subkeys.pgp.net --recv 6E871C4A881574DE
gpg: requesting key 881574DE from hkp server subkeys.pgp.net
gpgkeys: key 6E871C4A881574DE not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


omg... :popcorn:

Wow okay one more

```
gpg --keyserver subkeys.pgp.net --recv-keys 881574DE ; gpg --export 881574DE | apt-key add -
```

---

### Post by Morganza on 2010-05-06
> **wojox said:**
> Wow okay one more

```
gpg --keyserver subkeys.pgp.net --recv-keys 881574DE ; gpg --export 881574DE | apt-key add -
```

bhaaaaaaaaaaa

gpg --keyserver subkeys.pgp.net --recv-keys 881574DE ; gpg --export 881574DE | apt-key add -
gpg: requesting key 881574DE from hkp server subkeys.pgp.net
gpgkeys: key 881574DE not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.


:guitar: :lolflag:

---

### Post by Morganza on 2010-05-06
wojox can u tell me wath is your download server please?

Ty

---

### Post by Morganza on 2010-05-07
Done :)

I remove entries from other software in update manager settings, like chrome and ubuntu tweak.

Thks to all

---

### Post by Dr.grUDgE on 2011-01-29
this thread is too old...but for all its worth, could anyone explain what exactly one is supposed to do in this case? I am having this problem and can't really find a solution...:(

---

### Post by sikander3786 on 2011-01-29
> **Dr.grUDgE said:**
> this thread is too old...but for all its worth, could anyone explain what exactly one is supposed to do in this case? I am having this problem and can't really find a solution...:(
Please post the complete output of this command from Applications > Accessories > Terminal.

```
sudo apt-get update
```

When you type your password, you won't see any characters or asterisks appearing. Just type it blindly and hit Enter and post the output back here.

---

### Post by Dr.grUDgE on 2011-01-30
@sikander3786: Hey man, thanx for the help, but I upgraded my 10.04 to 10.10 with an alternate install iso yesterday night and the problem doesn't persist after the upgrade. 
Thanks a lot! :guitar:

---

