---
title: "Cannot Install ANY programs; erroring out all over the place"
date: 2012-09-15
forum: General Help
---

### Post by Shie6meepo on 2012-09-15
I just did a fresh install of 12.04 today because my old one was buggy, and the new install won't let me download ANY software, add any repositories, or update my system without erroring out. Here's what I get when I try to update:

[LEFT]```
W: GPG error: http://security.ubuntu.com precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```This has done this twice today on two fresh installs, and I'd rather find a way around it here than to re-download and format the ISO on my flash drive to try again in vain.
[/LEFT]

---

### Post by squaregoldfish on 2012-09-15
It looks as though something's gone wrong at your chosen repository source (us.archive.ubuntu.com). You can switch to a different server using Synaptic:

Go to Settings -> Repositories. On the Ubuntu Software tab, select the Download From... dropdown and then Other... - you'll be given an enormous list of servers to choose from. Select a different one and see if it makes a difference.

Steve.

---

### Post by Shie6meepo on 2012-09-15
> **squaregoldfish said:**
> It looks as though something's gone wrong at your chosen repository source (us.archive.ubuntu.com). You can switch to a different server using Synaptic:

Go to Settings -> Repositories. On the Ubuntu Software tab, select the Download From... dropdown and then Other... - you'll be given an enormous list of servers to choose from. Select a different one and see if it makes a difference.

Steve.
Problem: Synaptic is not installed. Is there another way to change it?

---

### Post by squaregoldfish on 2012-09-15
Ha! Chicken and egg....

OK, it can be done, but with great care. **PLEASE TAKE BACKUPS FIRST!**

**Backup**, then edit the file /etc/apt/sources.list - replace every instance of us.archive.ubuntu.com with the name of an alternative mirror. I'm in the UK, so I'm using gb.archive.ubuntu.com and it seems to be working at present.

After changing the file, run sudo apt-get update and hopefully it will work! Then you can install Synaptic and use that to find a more local repository that works - much safer!

Steve.

---

### Post by Shie6meepo on 2012-09-15
> **squaregoldfish said:**
> Ha! Chicken and egg....

OK, it can be done, but with great care. **PLEASE TAKE BACKUPS FIRST!**

**Backup**, then edit the file /etc/apt/sources.list - replace every instance of us.archive.ubuntu.com with the name of an alternative mirror. I'm in the UK, so I'm using gb.archive.ubuntu.com and it seems to be working at present.

After changing the file, run sudo apt-get update and hopefully it will work! Then you can install Synaptic and use that to find a more local repository that works - much safer!

Steve.
Is there anywhere online I can find a mirror that's relatively close to me, or should I just select a well-known one that may not be close and just wait awhile for things before I can change it to a more localized one?

---

### Post by squaregoldfish on 2012-09-15
I should just use one anywhere that works to get Synaptic installed. Once you've done that, you can use it to pick a more local mirror from the list. It'll be much easier to switch mirrors that way.

Steve.

---

### Post by Shie6meepo on 2012-09-15
Here's what I got after running the update. My issues are with the remaining two URLs, which I didn't change. What do you recommend for the security and extras URLs if I used GB for the ones that said us before?

```
W: GPG error: http://security.ubuntu.com precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Edit: I guess that doesn't really matter now that I have Synaptic.

Thanks for the help, and barring any further issues this thread should be declared solved!

---

### Post by oldos2er on 2012-09-15
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

You can graphically edit your sources.list with ```
gksudo software-properties-gtk
```

---

### Post by squaregoldfish on 2012-09-15
A bit of Googling has found a probable answer for those. Try Method 1 on this link:

[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

Steve.

oldos2er beat me to it! Also it seems that Synaptic simply runs software-properties-gtk for the repository setup. *Squirrels away information for the future*

---

