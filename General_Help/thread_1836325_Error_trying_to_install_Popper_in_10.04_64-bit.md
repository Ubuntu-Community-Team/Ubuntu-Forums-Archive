---
title: "Error trying to install Popper in 10.04 64-bit"
date: 2011-08-30
forum: General Help
---

### Post by magic8ball on 2011-08-30
Hi,

I'm using 10.04 LTS 64-bit and I'm trying to install Popper.

I run this command:

```
sudo add-apt-repository ppa:ralf.hersel/rhersel-ppa
```And get this output (I blanked 3 things below because I didn't know if they were unique to me):

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
gpg: requesting key xxxxxxxx from hkp server keyserver.ubuntu.com
gpg: key xxxxxxxx: public key "Launchpad PPA for Ralf Hersel" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```When I look in Software Sources, I see the PPA for ralf.hersel and there is an associated Authentication key listed.

However, when I look in Ubuntu Software Center, Popper isn't listed.  In addition, when I run Update Manager, I get the following error:

```
Failed to fetch [http://ppa.launchpad.net/ralf.hersel/rhersel-ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/ralf.hersel/rhersel-ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```This looks like a problem on the PPA end to me (Lucid 64-bit package not found), but I'm not sure.  I'd appreciate if someone could answer this for sure and give me an idea of how to proceed.

Thanks,
Chuck

---

### Post by magic8ball on 2011-09-14
Ouch, didn't think that I'd ask one of those leper questions that gets no response.

Since people don't use Popper, let me try this...

I'm using the latest Thunderbird, but FireTray isn't compatible with it.  I'm basically just looking for a Thunderbird add-on or a program (like Popper) that will display the number of new emails in the notification area and is compatible with the latest Thunderbird. Any suggestions for a solution would be appreciated.

Thanks,
Chuck

---

### Post by timgood on 2011-09-14
There does seem to be a problem with the ppa as I am using 10.10 and still can't get the latest version (0.29) using the ppa so I had to install manually. But having done that, it works.

Hope this helps.

---

### Post by magic8ball on 2011-09-14
Ah ha!  That's exactly what I needed to know.  I used a couple of your earlier posts and figured out how to install the GetDeb PPA and then install Popper (i.e. your aforementioned "install manually").  Popper is now installed and I'll work on configuring it in the next few days.

Thank you very much for your help,
Chuck

---

