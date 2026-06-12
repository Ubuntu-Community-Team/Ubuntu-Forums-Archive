---
title: "GPG invalid packet errors in apt"
date: 2009-12-27
forum: General Help
---

### Post by tilapia on 2009-12-27
My apologies if this has been posted already - I've had a read around but haven't been able to find a solution that works for me. 

I'm running Karmic Koala and when I run sudo apt-get update I get several error messages telling me that public keys are not present. 

[PHP]W: GPG error: http://archive.canonical.com karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://gb.archive.ubuntu.com karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://gb.archive.ubuntu.com karmic-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://gb.archive.ubuntu.com karmic-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
[/PHP]

For each key, I tried running the following command: gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5 (where 40976EAF437D05B5 was the offending key). However, when I re-ran sudo apt-get update, I still got the same errors. 

And then ran this: [PHP]gpg --keyserver keyserver.ubuntu.com --recv 437D05B5; gpg --export --armor 437D05B5 | sudo apt-key add -; gpg --keyserver keyserver.ubuntu.com --recv 437D05B5; gpg --export --armor 437D05B5 | sudo apt-key add -; sudo apt-get update[/PHP]

Unfortunately, that didn't seem to do anything either...

[PHP]

Trying the following commands also gives me a nasty looking error: 

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5

matt@q9550:/etc/apt$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys
matt@q9550:/etc/apt$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: [don't know]: invalid packet (ctb=23)
gpg: keydb_get_keyblock failed: eof
gpg: [don't know]: invalid packet (ctb=23)
gpg: /etc/apt/trusted.gpg: copy to `/etc/apt/trusted.gpg.tmp' failed: invalid packet
gpg: error writing keyring `/etc/apt/trusted.gpg': invalid packet
gpg: [don't know]: invalid packet (ctb=23)
gpg: keydb_search failed: invalid packet
gpg: key 437D05B5: public key "[User ID not found]" imported
gpg: error reading `[stream]': invalid packet
gpg: Total number processed: 0
gpg:               imported: 1
matt@q9550:/etc/apt$ [/PHP]

Does anyone have any pointers on how I might be able to resolve this, please? I've tried removing these items from my sources.list, but that doesn't appear to work either. 

Many thanks!

---

### Post by zvacet on 2009-12-27
I don´t know if that will be helpful but try to switch to another server under **system>admin>software sources**.

---

