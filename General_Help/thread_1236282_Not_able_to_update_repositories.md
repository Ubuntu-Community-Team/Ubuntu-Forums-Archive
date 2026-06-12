---
title: "Not able to update repositories"
date: 2009-08-10
forum: General Help
---

### Post by Devakishor on 2009-08-10
Hi all,

I have been facing problems with updating repositories for sometime now. I'm pasting the error messages as it is.

It would be great if you guys can help me out here.

Thanks 
Dev

_Error Message:_

[COLOR="Red"]

[I]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_IN.bz2](http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_IN.bz2)  Unable to connect to wine.budgetdedicated.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/I][/COLOR]

---

### Post by mthalis on 2009-08-10
Problem is your link **Authentication keys** those are invalid... 
This will give some idea of how to manage repository
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by arky on 2009-08-10
man apt-get

or 

System > Administration > Software Sources

Problems:
You can get GPG keys of the ppa repositories.

You can remove unreachable repsoitories.

Then 
sudo apt-get update 
sudo apt-get upgrade

---

### Post by Devakishor on 2009-08-10
thanks @mthalis & @arky for the super fast reply 

I know there's a problem with the keys.. Will do what you guys suggested.

Another query?

I had valid keys until a few days back. How did they become invalid? Do repository kers become obsolete after a certain period?

---

### Post by credobyte on 2009-08-10
Most of these things are already explained - [https://help.ubuntu.com/community/SecureApt#How%20to%20find%20a%20key](https://help.ubuntu.com/community/SecureApt#How%20to%20find%20a%20key) ;)

---

### Post by arky on 2009-08-10
The package maintainer might have changed them or your keyring must have lost 'em. Either way you can retrive and add them with apt-key

---

### Post by jherskow on 2009-08-27
hi im a total newbie, and im getting some problems when i try to update:
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://medibuntu.sos-sts.com jaunty Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release  

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/jaunty/free/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

any help?

---

### Post by arky on 2009-08-27
Try a different repository. And update your computer.

[https://help.ubuntu.com/9.04/add-applications/C/adding-repos.html](https://help.ubuntu.com/9.04/add-applications/C/adding-repos.html)

---

### Post by jherskow on 2009-09-01
what d you mean, a different repository?

---

### Post by arky on 2009-09-01
Sorry, You learn more of Ubuntu Repositories over here

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by hubertofliege on 2009-09-09
I have the same problem as the original poster, however I did not understand the solution.  My authentication keys have gone bad.  Do I want to reauthenticate them or delete them?  

Also, even if my third party applications are no longer good, I should still be getting all the Main updates, right?

---

### Post by arky on 2009-09-12
See if running the following command would correct the problems.

sudo apt-get update
sudo apt-get upgrade

---

### Post by hubertofliege on 2009-09-13
I managed to replace almost all of my keys, however I still have these three error messages remaining:

GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>

Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages)  Unable to fetch file, server said 'Failed to open file.  '

Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '

so I've authenticated all the missing keys, but what do I do about the one BAD key and the other to files which can't be opened?

---

### Post by arky on 2009-09-13
Follow the steps mentioned in this page.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -

---

