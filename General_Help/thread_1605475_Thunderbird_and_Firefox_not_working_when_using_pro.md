---
title: "Thunderbird and Firefox not working when using profiles on an NFS share"
date: 2010-10-25
forum: General Help
---

### Post by go4linux on 2010-10-25
Instead of upgrading to 10.10, I decided to install everything from scratch. Since the installation I can't make Firefox and Thunderbird work with the profiles I have always used on an NFS share. Locally Everything seems to work fine, but when I use the profiles on my NFS server I get in trouble.
With Thunderbird I can read the email that is already there, but I can't get new one. It seems to hang during the connection. I can also write Drafts, and save them. RSS seems to work too.
With Firefox I get the error "the bookmark and history system will not be functional because one of Firefox's files is in use by another application". When I try to open a url it doesn't work.
Both applications start very slowly, but only when I open the profiles on the NFS share. I can happily read and write files on that share, so it can't be an access problem. I have a 64 bit machine, and I am using the Firefox 3.6.11 32 bit that I downloaded separately. Thunderbird is the one coming with the distribution.

Any help really appreciated. Many thanks

---

### Post by go4linux on 2010-10-26
seems that i found a solution: my nfs client stopped regularly for a while because it couldn't get a lock. I could see that from a message in /var/log/messages:

*lockd: cannot monitor 10.10.1.2*

so I mounted the share with the option nolock, and now it seems to work. In fact, I am posting from my wonderful firefox running with the profile on my NFS share :cool:

It took me several hours and 2 computers, but I finally did it. Guess it could have been much faster if I had looked at the messages as a first thing.

I would still like to know while this behavior changed though

---

