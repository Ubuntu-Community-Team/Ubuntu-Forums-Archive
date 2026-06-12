---
title: "Questions about installing packages"
date: 2009-07-26
forum: General Help
---

### Post by csh on 2009-07-26
I would like to ask some questions regarding installing packages through Synaptic Package Manager or "apt-get" command.

If I install some packages through Synaptic Package Manager or "apt-get" command, I have the following questions:

1. Where will the package setup files (.deb or others) being stored?

2. Will the downloaded package setup files being deleted after installation?

3. If the package setup files are not deleted, can I delete it? And, if I delete, will it cause any problem?

I ask the above questions because if the package setup files are not being deleted after package installation, it will waste my hard disk space.

Please answer my above questions. Any reply will be appreciated.

---

### Post by credobyte on 2009-07-26
> 1. Where will the package setup files (.deb or others) being stored?
/var/cache/apt/archives

> 2. Will the downloaded package setup files being deleted after installation?
No!

> 3. If the package setup files are not deleted, can I delete it? And, if I delete, will it cause any problem?
Yes, you can & it'll not cause any problems.

---

### Post by lisati on 2009-07-26
apt-get comes with a couple of "clean" options, e.g. ```
sudo apt-get autoclean
```

---

### Post by DeMus on 2009-07-26
> **lisati said:**
> apt-get comes with a couple of "clean" options, e.g. ```
sudo apt-get autoclean
```

I tried that and yes it did clean some packages but most of them are still there.
Are there any other methods of getting rid of all the .deb files in /var/cache/apt/archives or is it just rm *.deb ?

---

### Post by credobyte on 2009-07-26
> **DeMus said:**
> I tried that and yes it did clean some packages but most of them are still there.
Are there any other methods of getting rid of all the .deb files in /var/cache/apt/archives or is it just rm *.deb ?

```
sudo apt-get clean
```

---

### Post by DeMus on 2009-07-26
> **credobyte said:**
> ```
sudo apt-get clean
```

Clean works while autoclean does not. Is it me or is that strange?

---

### Post by credobyte on 2009-07-26
> **DeMus said:**
> Clean works while autoclean does not. Is it me or is that strange?

Quote ( autoclean ) from apt-get man page:
> Like clean, autoclean clears out the local repository of retrievedpackage files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless.

Quote ( clean ) from apt-get man page:
> clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/.

It's not weird - it's supposed to be so :)

---

### Post by oldos2er on 2009-07-26
> **csh said:**
>  2. Will the downloaded package setup files being deleted after installation?


 You can configure Synaptic this way, via menus Settings, Preferences, Files; under Temporary files tick the box next to 'Delete downloaded packages after installation'.

---

### Post by csh on 2009-08-04
Sorry for the late reply because of busy. Well, I would like to say thank you to all people who replied to this thread. Your suggestion helped me very much.

> **oldos2er said:**
> You can configure Synaptic this way, via menus Settings, Preferences, Files; under Temporary files tick the box next to 'Delete downloaded packages after installation'.

Thanks, oldos2er.

---

