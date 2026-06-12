---
title: "unattended-upgrades not being executed regularly"
date: 2011-08-18
forum: General Help
---

### Post by NautilusIII on 2011-08-18
Hi!


I am using Ubuntu 10.04.

I have recently installed unattended-upgrades:


```
apt-get install unattended-upgrades
```





I have made the following entries in /etc/apt/apt.conf.d/50unattended-upgrades:


```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
    "Ubuntu lucid-security";
//    "Ubuntu lucid-updates";
};

// List of packages to not update
Unattended-Upgrade::Package-Blacklist {
//    "vim";
//    "libc6";
//    "libc6-dev";
//    "libc6-i686";
};

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. The package 'mailx'
// must be installed or anything that provides /usr/bin/mail.
Unattended-Upgrade::Mail "me@me.de";

// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";

// Automatically reboot *WITHOUT CONFIRMATION* if a 
// the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";


// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";

```


Since the file /etc/apt/apt.conf.d/10periodic did not exist, I just created it and added the following entries:

```
APT::Periodic::Enable "1";
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
APT::Periodic::RandomSleep "1800";
APT::Periodic::Verbose "1";

```


Besides that I am using apticron which is afaik not executing unattended-upgrades, but simply telling me what needs to be upggraded. Aptricron regularly informs me about that via mail, but it does not trigger any update.

So, why is unattended-upgrades not being executed on a regular basis, or, even more interesting, how can I ensure unattended-upgrades is being executed daily?

Thanks!

---

### Post by NautilusIII on 2011-08-19
Nobody an idea? :-(

---

