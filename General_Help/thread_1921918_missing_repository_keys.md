---
title: "missing repository keys"
date: 2012-02-07
forum: General Help
---

### Post by steve.a on 2012-02-07
Hi i always see these errors whenever i try to install a new package or whenever update manager is run


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68A3CE6B38BD81CA

i tried adding the key using the following 
```
gpg --keyserver subkeys.pgp.net --recv 68A3CE6B38BD81CA
```

and
```
gpg --keyserver keyserver.ubuntu.org --recv 68A3CE6B38BD81CA
```

but i kept getting
[I]gpg: requesting key 38BD81CA from hkp server
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.[/I]

how can this be solved?
thanks

---

### Post by Krytarik on 2012-02-07
> **steve.a said:**
> ```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68A3CE6B38BD81CA
```
Given its way too short address, that source is a faulty entry in your "Software Sources" in the first place; just remove it from there.

Regards.

---

### Post by wojox on 2012-02-07
Should be:
```
gpg --keyserver keyserver.ubuntu.com --recv 38BD81CA
gpg --export --armor 38BD81CA | sudo apt-key add -
```

---

### Post by bluexrider on 2012-02-07
import keys
```

gpg --keyserver keyserver.ubuntu.com --recv XXXXXXXXXXXXXXXX
gpg --export --armor XXXXXXXXXXXXXXXX | sudo apt-key add -

``` replace the X with the key

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys XXXXXXXX
```
replace X with the last 8 digits of the key


using Ubuntu.ORG will not work

---

### Post by steve.a on 2012-02-08
> **Krytarik said:**
> Given its way too short address, that source is a faulty entry in your "Software Sources" in the first place; just remove it from there.

Regards.

Hi,

what is the correct address to replace this entry with?

thanks

---

### Post by Krytarik on 2012-02-08
> **steve.a said:**
> what is the correct address to replace this entry with?
My fault; I've just tested if the complete Launchpad address of a PPA is output when the respective GPG key is missing (by deliberately deleting one of mine, obviously), and it is not. So follow the suggestions of the other guys. :D

---

### Post by steve.a on 2012-02-09
> **bluexrider said:**
> import keys
```

gpg --keyserver keyserver.ubuntu.com --recv XXXXXXXXXXXXXXXX
gpg --export --armor XXXXXXXXXXXXXXXX | sudo apt-key add -

``` replace the X with the key

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys XXXXXXXX
```
replace X with the last 8 digits of the key


using Ubuntu.ORG will not work

hmmm even that does not work i keep getting

gpg: requesting key 38BD81CA from hkp server
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.

however i navigated to kerserver.ubuntu.com and entered ppa.launchpad.net in the search box, it returned a list of entries. which one of them should i use. are they safe to use?

---

### Post by Krytarik on 2012-02-09
> **steve.a said:**
> hmmm even that does not work i keep getting

gpg: requesting key 38BD81CA from hkp server
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.

however i navigated to kerserver.ubuntu.com and entered ppa.launchpad.net in the search box, it returned a list of entries. which one of them should i use. are they safe to use?
Your search there simply returned a small part of *all* keys stored up there for Launchpad PPAs, and even though you can also find the details of the key you are actually having issues with ([here]("http://keyserver.ubuntu.com:11371/pks/lookup?search=dockbar&op=vindex")), I don't know whether it would help in importing it.

To get to know of what specific PPA the GPG key is missing, I've simply googled for "38BD81CA", and it turned out that it's the "[Dockbar Main PPA]("https://launchpad.net/%7Edockbar-main/+archive/ppa")", which, coincidentally, I have added too; so I've simply tested if I can re-import its GPG key, and had no issues with that at all.

It seems like you are behind a proxy blocking access to the port used by default for importing GPG keys; try using port 80 instead, this should work:
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 38BD81CA
```

---

