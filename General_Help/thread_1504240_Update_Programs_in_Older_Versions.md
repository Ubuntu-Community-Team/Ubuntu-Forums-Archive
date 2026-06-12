---
title: "Update Programs in Older Versions"
date: 2010-06-07
forum: General Help
---

### Post by multisystem on 2010-06-07
I'm sorry if this is recurring subject, but I have searched the forum for such a subject and can't find one.

I'm using Xubuntu 8.10,

I'd like to update my programs to the latest releases, but the available updates in 8.10 versions are not the newest ones. I can't upgrade to a newer version of Ubuntu due to some known issues with older Intel drivers.

Is it possible to have the latest updates of packages while I still using 8.10 version?

Thanks in advance :)

---

### Post by SlidingHorn on 2010-06-07
well, there's a couple ways you could probably do it...I don't know how good an idea it would be, but you could add a newer version's repos for the updated packages, or you could get them from the actual developer(s)' site and go from there.

I have a tendency to advise not to do anything I say until someone smarter comes along though..so hang tight

**Edit:**  It might also help to know which packages you're trying to update

---

### Post by multisystem on 2010-06-07
Thanks SlidingHorn for replying :)

I tried to add a newer repos, but I got this error message

```

following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: You may want to run apt-get update to correct these problems

```

I tried to download the source code of the newer version and compile it, but it's too difficult and had a lot of dependency problems, also compiling and building takes too much time. I failed to compile any program from source code till now.

I'm trying to update Pidgin, aMSN, MonoDevelop and some other stuff.

---

### Post by multisystem on 2010-06-07
Please, any help :(

---

### Post by SlidingHorn on 2010-06-07
did you run the command?  What happened?

```
sudo apt-get update
```

---

### Post by multisystem on 2010-06-08
Still the same :(

---

### Post by snowpine on 2010-06-08
8.10 has reached its "end of life" and is no longer supported with application updates, bug fixes, and security patches. I would suggest troubleshooting the Intel problem with 10.04 (the current release) or rolling back to 8.04 (which uses the older Intel drivers and will be supported through April 2011).

You might also consider an alternate distro; there are lightweight options such as Puppy that are designed specifically for older hardware.

---

### Post by multisystem on 2010-06-08
Are you sure that 8.04 version provides the latest updates while 8.10 doesn't?

Thanks very much :)

---

### Post by snowpine on 2010-06-08
> **multisystem said:**
> Are you sure that 8.04 version provides the latest updates while 8.10 doesn't?

Thanks very much :)

8.04 uses software from April 2008. It is, however, still supported (8.10 is not). You need 10.04 if you want up-to-date applications (as of April 2010).

---

### Post by Soul-Sing on 2010-06-08
> **multisystem said:**
> Are you sure that 8.04 version provides the latest updates while 8.10 doesn't?

Thanks very much :)

yes, desktop versions of 8.04 will be updated up to april 2011
But the most logical step is to upgrade to 9.04, and maybe via 9.10 to 10.4, or backup your ./home direct. and try via a live cd a clean install of the newest 10.4 version of ubuntu.

---

