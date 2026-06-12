---
title: "Can't get PPA Key!"
date: 2010-06-23
forum: General Help
---

### Post by torato on 2010-06-23
I know I know,lots of you will say that I need to search forums.But I did it,and normally I know how to get a key,but this time I tried more than 20 times,but couldn't get the bloody key.Is this happening just me or to everyone?
Here's the link for ppa:
[https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia](https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia)
And I tried this code
sudo add-apt-repository ppa:nvidia-vdpau/cutting-edge-multimedia
NO luck!
```
sudo add-apt-repository ppa:nvidia-vdpau/cutting-edge-multimedia
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 71609D4D2F1518FA9C5DC0FB1DABDBB4CEC06767
gpg: CEC06767 anahtar&#305; keyserver.ubuntu.com sunucusunun hkp adresinden isteniyor
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: geçerli OpenPGP verisi yok
gpg: &#304;&#351;lenmi&#351; toplam miktar: 0
```

---

### Post by torato on 2010-06-23
I think problem is in my connection.Just because it only allows port 80.What do you think,how can i get rid of this problem?
Thanks,

---

### Post by PC_load_letter on 2010-07-02
I had the same problem, it was the firewall. When I disabled the firewall, everything was fine. 

If someone here can tell us what rule could be added to the firewall to allow the ppa server keys verification, it'd be great.

---

### Post by artemyv on 2010-07-02
> **PC_load_letter said:**
> I had the same problem, it was the firewall. When I disabled the firewall, everything was fine. 

If someone here can tell us what rule could be added to the firewall to allow the ppa server keys verification, it'd be great.
if you go to the ppa page and click on the key link 

```

Signing key:               [                 1024R/CEC06767               ]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x71609D4D2F1518FA9C5DC0FB1DABDBB4CEC06767&op=index")               ([What is this?]("https://launchpad.net/+help/soyuz/ppa-sources-list.html"))             
```it will bring you to the following page

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x1DABDBB4CEC06767](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x1DABDBB4CEC06767)

as you can see in the url - the key is accessible on the port 11371 - this is the port you need to open on the firewall

---

### Post by reakin on 2010-07-07
> 
as you can see in the url - the key is accessible on the port 11371 - this is the port you need to open on the firewall

What do you do if you can't open this port?  Is there any way to manually certify the key?

Also, I am only pretty sure this port is blocked on my connection.  Does anyone know how to verify this?

Regards,
Rich

---

### Post by reakin on 2010-07-07
I have tried to manually import a few of the gpg's after finding them on the net and I always get the following error message:

Error importing selected file

The selected file may not be a GPG key file or it might be corrupt.

Why does it think these are corrupt?

Rich

---

### Post by snahrck on 2010-09-30
if you are behind a firewall that blocks port 11371 try 80 by doing this:

sudo gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver **hkp://keyserver.ubuntu.com:80** --recv [your_key]

add-apt-repository should be aware of that and try the port 80 if 11371 fails (or simply use 80 by default). Alternatively, it could add an option to switch the keyserverport in command line.

---

### Post by nilarimogard on 2010-12-09
I've created a script that imports all missing GPG keys using port 80 so it should work behind a firewall too. See here: [http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html](http://www.webupd8.org/2010/12/import-missing-gpg-keys-even-behind.html)

---

