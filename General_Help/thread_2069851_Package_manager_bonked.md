---
title: "Package manager bonked"
date: 2012-10-11
forum: General Help
---

### Post by tdlam on 2012-10-11
Hi all...
Just starting recieving this error message this morning. It came out of nowhere. Installation was fine yesterday before  I ran normal suggested updates that popped up last night, so something has bonked.
```
Reading package lists... Error!
W: GPG error: http://dl.google.com stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: http://download.bitdefender.com bitdefender Release: The following signatures were invalid: BADSIG A373FB480EC4FE05 BitDefender Packages <packages@bitdefender.com>
W: GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG FC6FA5EB4357B38A Launchpad PPA for Arx Libertatis
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.canonical.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 3BDAAC08614C4B38 Launchpad otto06217
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 0D91713165530E6C Launchpad PPA for Screenlets Dev Team
W: GPG error: http://archive.canonical.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 94E58C34A8670E8C Launchpad PPA for Screenlets
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG EB563F93142986CE Launchpad PPA for Xubuntu Developers
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```
as I said all was fine yesterday before running updates that popped up in the normal notifier.

Any help would be appreciated!
Thanks in advance

---

### Post by wildmanne39 on 2012-10-11
*Thread moved to **General Help**.*

---

### Post by TheFu on 2012-10-11
Could be anything from a back network connection to a failing HDD.  What do the system log files say?

/var/log/
and dmesg would help.

---

### Post by jrog on 2012-10-11
OP, the last few sentences of your output suggest that there is a problem with your files in /var/lib/apt/lists ("E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages E: The package lists or status file could not be parsed or opened."). The following commands should (hopefully!) take care of that. At a terminal (CTRL + ALT + T), type:

```
sudo apt-get clean
sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
```
**If that works** (I'm guessing it will), you can delete the backup directory with the old lists (be careful to type this command exactly, as mistakes with 'rm -rf' can result in serious data loss):

```
sudo rm -rf /var/lib/apt/lists.old
```
**If it didn't work**, you can try manually adding the keys. Look at the BADSIG errors, note the key hash for each one (e.g., BADSIG **40976EAF437D05B5**), and then type:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
```

Do that for each. But again, given the last few sentences of your output, I'm suspecting that re-creating the lists (in the first step) will clear things up.

---

### Post by oldos2er on 2012-10-11
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by wildmanne39 on 2012-10-11
Hi, please be careful using and posting commands like this.
```
rm -rf
```they need to include a warning that if the path is not typed correctly you can break your system.
Thanks

---

### Post by jrog on 2012-10-11
> **Wild Man said:**
> Hi, please be careful using and posting commands like this.
```
rm -rf
```they need to include a warning that if the path is not typed correctly you can break your system.
Thanks
Sorry. That^ is correct. Edited the earlier post.

---

### Post by tdlam on 2012-10-11
Var has so many files in it that I wouldn't even know where to begin to look

sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
When I type the above command it tells me it can't be moved because the directory is not empty
```
mv: cannot move `/var/lib/apt/lists' to `/var/lib/apt/lists.old/lists': Directory not empty

```
one thing I did notice is that on boot up Xubuntu did a "routine disk check" and its not the first time it has done this...could I be having a hard drive failure?

---

### Post by TheFu on 2012-10-11
> **tdlam said:**
> Var has so many files in it that I wouldn't even know where to begin to look

That's what **grep** is for.

**$ sudo grep -i error /var/log/*log**

The disk check happens from time to time based on file system settings or if the machine was shutdown without giving the file system time to cleaning unmount it.

I'm inclined to think the other answers are more helpful for this issue, but a HDD failure could come at any time and they are seldom convenient.  **Every HDD will fail. Every one of them.** The trick is to have already replace the HDD before that happens. Having a great backup solution can be the best solution.

Again, the other answers are probably better.

---

### Post by tdlam on 2012-10-11
@ oldos2er:
that link doesn't work for me. The first method I get the error saying I can't move again because the directory is not empty
second method doesnt work because the word aptitude is not recognised

---

### Post by oldos2er on 2012-10-11
> **tdlam said:**
> @ oldos2er:
that link doesn't work for me. The first method I get the error saying I can't move again because the directory is not empty
second method doesnt work because the word aptitude is not recognised

Here are the commands: 

sudo -i

apt-get clean

cd /var/lib/apt

mv lists lists.old

mkdir -p lists/partial

apt-get clean

apt-get update

---

### Post by jrog on 2012-10-11
> **tdlam said:**
> Var has so many files in it that I wouldn't even know where to begin to look

sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
When I type the above command it tells me it can't be moved because the directory is not empty
```
mv: cannot move `/var/lib/apt/lists' to `/var/lib/apt/lists.old/lists': Directory not empty

```
Okay, then instead of the original commands I gave you, edit them slightly to do this:

```
sudo apt-get clean
mkdir ~/backup
sudo mv /var/lib/apt/lists ~/backup/ 
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
```> **tdlam said:**
> one thing I did notice is that on boot up Xubuntu did a "routine disk check" and its not the first time it has done this...could I be having a hard drive failure?
That's very unlikely right now. Routine disk checks are typically just routine disk checks.

EDIT: The commands that oldos2er is giving you do essentially the same thing as the ones I'm giving you, BTW.

---

### Post by tdlam on 2012-10-11
wow this is getting complicated I tried running ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
```inserting one of the keys  and I get this error:```
 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.Vi2IVQEfMX --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
gpg: requesting key 7FAC5991 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection refused
gpgkeys: HTTP fetch error 7: couldn't connect: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```
Edit: yes I see the commands are essentially the same thanks...just that the mv command in both instances doesnt work

---

### Post by oldos2er on 2012-10-11
Trying to add or update a key isn't going to solve a BADSIG error.

---

### Post by jrog on 2012-10-11
> **tdlam said:**
> wow this is getting complicated I tried running ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
```inserting one of the keys  and I get this error:```
 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.Vi2IVQEfMX --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
gpg: requesting key 7FAC5991 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection refused
gpgkeys: HTTP fetch error 7: couldn't connect: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```
You shouldn't move to this step until you try all of the earlier commands and determine that they do not work. See above posts ([http://ubuntuforums.org/showpost.php?p=12290388&postcount=12](http://ubuntuforums.org/showpost.php?p=12290388&postcount=12)). Do what they say first. They should fix the problem.

Anyway, the error you're getting here is likely caused by a firewall. Are you behind a firewall?

EDIT: And oldos2er is right; what you did in the quoted part here (which I suggested you do if the other instructions don't work) won't resolve a BADSIG error, but rather a NO_PUBKEY error. The two must've got crossed up in my brain, so ignore that part of what I suggested.

---

### Post by tdlam on 2012-10-11
ok I have tried the other commands and I am stopped at this :
```
root@tdlam-Inspiron-6000:/var/lib/apt# mv lists lists.old
mv: cannot move `lists' to `lists.old/lists': Directory not empty

```

so that doesn’t seem to work.
I am on a restricted server here at work but if its interfering with this its the first time it has done so as I have updated numerous times here at work with no issues. 
I could wait until I get home tonight and try again I suppose. Dunno at this point.

BTW I DO appreciate all your help and suggestions folks. I failed to say that at first. Thanks

---

### Post by jrog on 2012-10-11
> **tdlam said:**
> ok I have tried the other commands and I am stopped at this :
```
root@tdlam-Inspiron-6000:/var/lib/apt# mv lists lists.old
mv: cannot move `lists' to `lists.old/lists': Directory not empty

```so that doesn&#8217;t seem to work.
I am on a restricted server here at work but if its interfering with this its the first time it has done so as I have updated numerous times here at work with no issues. 
I could wait until I get home tonight and try again I suppose. Dunno at this point.

BTW I DO appreciate all your help and suggestions folks. I failed to say that at first. Thanks
Use the version of the commands that I suggested, where you move the lists to a different spot: [http://ubuntuforums.org/showpost.php?p=12290388&postcount=12](http://ubuntuforums.org/showpost.php?p=12290388&postcount=12). It appears you have a lists.old directory in /var/lib/apt already.

And no problem. :)

---

### Post by tdlam on 2012-10-11
ok Jrog...your edited commands did the trick. Dunno why it all suddenly  went south after a normal update but it did. Thanks for all your help  folks. And just an FYI I am a back up fool...I have all my files backed  up every one or two days and I clonezilla this laptop for a full drive  image once a week. 

Thanks again folks. You are all a testament to why the linux community is  the very best in the world.

Just wish I knew why this might have happened in the first place...LOL!

hmmmmmm I dont see where I can mark this thread as solved...it used to be upper right somewhere...or am I missing something?

edit: never mind found it!

---

### Post by jrog on 2012-10-11
> **tdlam said:**
> ok Jrog...your edited commands did the trick.
Great!

> **tdlam said:**
> Dunno why it all suddenly  went south after a normal update but it did.
One possible cause is a broken network connection while updating; don't know if you experienced that at any point recently. This can also happen if you are going through a proxy while updating and something is/was wonky with the proxy. Either way, it seems that what happened here is that the list files in /var/lib/apt/lists got corrupted.

> **tdlam said:**
> Thanks for all your help  folks. And just an FYI I am a back up fool...I have all my files backed  up every one or two days and I clonezilla this laptop for a full drive  image once a week.
You're welcome! And speaking of backups, if you followed my instructions exactly, you created a folder with the name 'backup' in your home directory, and you put your old (corrupted) list files there; you can delete all of that if your system is now in a working state, as it appears to be.

> **tdlam said:**
> hmmmmmm I dont see where I can mark this thread as solved...it used to be upper right somewhere...or am I missing something?
It appears that you succeeded (or that someone did it for you)!

---

