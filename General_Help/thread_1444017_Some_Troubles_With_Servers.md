---
title: "Some Troubles With Servers"
date: 2010-03-31
forum: General Help
---

### Post by Thund3rstruck on 2010-03-31
Hi all,

I built out a headless VMWare v2.0.2 Server. I managed to work all that out but now I'm having some trouble getting my virtual machines on the server. 

I installed both proftpd and vsftpd but neither server lets me log in. 'Login Failed' is always returned (using the only account on the machine - created during the install). 

So I decided to install samba, but samba chokes on large files. I tried over and over again to copy a 10GB VMDK file over samba and it gets to 5% or so and suddenly tells me there is a network problem and dies (which there is no network problem as these machines are all on the same subnet plugged into the same gigabit switch). 

So now I'm back to FTP. Unfortunately when I ran apt-get remove proftpd, it didn't remove any of the config files (/etc/proftpd/*) so I manually deleted them. 

Now when I try to reinstall the FTP servers they won't start because the config files are gone.

What's the apt-get syntax to completely uninstall these servers as if they had never been installed so I can start clean? I really don't want to have to do a complete system re-install just to fix 300KB FTP servers.

---

### Post by iponeverything on 2010-03-31
```

sudo apt-get install sshfs
mkdir localdir
sshfs user@address:/home/path localdir
cp file localdir

```

or just use 

```
scp file user@address:/home/path
```

to reconfigure packages use:

```
dpkg-reconfigure packagename
```

If your removing package to try to start fresh use the purge option to dpkg, so that the old config files get removed.

---

### Post by Thund3rstruck on 2010-03-31
> **iponeverything said:**
> ```

sudo apt-get install sshfs
mkdir localdir
sshfs user@address:/home/path localdir
cp file localdir

```

or just use 

```
scp file user@address:/home/path
```

to reconfigure packages use:

```
dpkg-reconfigure packagename
```

EDIT: thanks for the feedback, I went ahead and did a re-install and I think I determined what the problem was. When I installed samba, I added a samba user with the same name and password as the admin user and that somehow messed up that account's ability to FTP. After the reload, I skipped installing samba and FTP now works. 

Cheers!
  

Thanks

---

