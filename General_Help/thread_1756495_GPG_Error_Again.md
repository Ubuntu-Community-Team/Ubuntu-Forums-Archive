---
title: "GPG Error: Again?"
date: 2011-05-12
forum: General Help
---

### Post by zia.newversion on 2011-05-12
So back in Maverick, when I enabled the third-party sources in Synaptics, next time when I'd do ```
apt-get update
``` there'd be some GPG error saying one or more keys couldn't be retrieved... I could repair that (unfortunately I have forgot how).

I thought it'd be fixed with the new release. But all the same. Now I have:
```
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 048A1684108A879C

```

Can someone please show me how to fix that?

---

### Post by philinux on 2011-05-12
> **zia.newversion said:**
> So back in Maverick, when I enabled the third-party sources in Synaptics, next time when I'd do ```
apt-get update
``` there'd be some GPG error saying one or more keys couldn't be retrieved... I could repair that (unfortunately I have forgot how).

I thought it'd be fixed with the new release. But all the same. Now I have:
```
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 048A1684108A879C

```

Can someone please show me how to fix that?

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 048A1684108A879C
```

Should fix it.

---

### Post by zia.newversion on 2011-05-12
Now that I come to think of it. That is somewhat like what I did in Maverick. :p
But sadly enough, looks like the keyserver.ubunut.com doesn't exist anymore... Have they moved it to another address? (I'm just saying).

```
gpg: requesting key 108A879C from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: No such file or directory
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
```

---

### Post by zia.newversion on 2011-05-16
[color="red"]**b u m p**[/color]

---

### Post by wojox on 2011-05-16
Run these two commands in the terminal:

```
gpg --keyserver pgpkeys.mit.edu --recv-key  048A1684108A879C 
gpg -a --export 048A1684108A879C | sudo apt-key add -
```

---

### Post by zia.newversion on 2011-05-17
```
# gpg --keyserver pgpkeys.mit.edu --recv-key 048A1684108A879C
gpg: requesting key 108A879C from hkp server pgpkeys.mit.edu
gpgkeys: key 048A1684108A879C not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

---

### Post by zia.newversion on 2011-05-18
Why do I gotta **[COLOR="Red"]B U M P[/COLOR]** it after every other post! :(

---

### Post by zia.newversion on 2011-05-19
And **[COLOR="Red"]b u m p[/COLOR]** again... Does no one know the answer? Come on!

---

### Post by zia.newversion on 2011-05-21
I need to find a solution. This GPG Error is getting on my head... Every time I do apt-get update, it's there... It doesn't cause any nuisance, but still, it's very annoying,

---

### Post by zia.newversion on 2011-05-22
> **zia.newversion said:**
> I need to find a solution. This GPG Error is getting on my head... Every time I do apt-get update, it's there... It doesn't cause any nuisance, but still, it's very annoying,
.

---

### Post by zia.newversion on 2011-05-25
***_[color="red"]b u m p[/color]_***

---

### Post by Elfy on 2011-05-25
Might be whatever ppa it is that you're getting the error with - try going to whatever ppa page it is and running the 

sudo add-apt-repository ppa:*ppaname* command.

Should get you the right key and all the information needed. Might also be that there is no 11.04 repo for it.

---

### Post by CoolJohnB on 2011-06-01
> **philinux said:**
> ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 048A1684108A879C
```

Should fix it.

Thank you this fixed it for me!!:D

---

### Post by zia.newversion on 2011-06-01
Nah! Doesn't work for me... :(

---

### Post by linuxinstalledfromhdd on 2011-06-01
Remove the listing in Synaptic package manager that you installed. 

Find the PPA for the repositories you wish to install from the command line instead.

Here is a good example:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by zia.newversion on 2011-06-05
I just removed Blender and Cheleb repos from Synaptic... And the error no longer shows... :)


But I 'm still looking for the workaround that doesn't require removing Blender! I live on it. :p

---

