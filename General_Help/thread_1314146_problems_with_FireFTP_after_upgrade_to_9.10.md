---
title: "problems with FireFTP after upgrade to 9.10"
date: 2009-11-04
forum: General Help
---

### Post by fantastic on 2009-11-04
I'm unable to connect to a site using FireFTP since upgrading to 9.10. I'm running Firefox (Shiretoko) 3.5.5pre and FireFTP 1.0.6.

The server I'm connecting to accepts port 22 requests. FireFTP was configured to use SFTP. Before the upgrade the connections work; now after the upgrade, "Unable to make a connection. Please try again." is returned.

I've tried the usual: reinstalling FireFTP, restarting firefox, deleting the entry for that server in FireFTP and re-adding it, etc...

I have blown away all keys in my /home/[user]/.shh/known_hosts. I've even removed the known_hosts file altogether. 

I am still able to connect to the server using the command line:
```
ssh [username]@[servername].[dom]
```

---

### Post by fantastic on 2009-11-05
Still having this issue.

Any suggestion for troubleshooting?

---

### Post by fantastic on 2009-11-09
Has anyone else had this problem? I'm still trying to resolve it.

thanks

---

### Post by finalwebsites on 2010-01-15
Just noticed that I have the same problem :(

FireFTP works fine for normal ftp connections but not for SFTP.

It seems that putty is needed to run the connection, maybe FireFTP doesn't have the rights to start Putty? )just guessing

---

### Post by Nisitiiapi on 2010-01-17
This seems to be an issue with 64-bit Firefox which is bundled with Karmic 64-bit.  I have this problem on one computer running 64-bit FF and FireFTP (running Karmic 64-bit).  On my netbook, which has 32-bit Karmic, no problems at all.

It doesn't seem to be unique to Ubuntu either.  In the reviews for FireFTP, someone noted the problem occurs with 64-bit FF on Arch as well: [https://addons.mozilla.org/en-US/firefox/reviews/display/684?page=7&show=20](https://addons.mozilla.org/en-US/firefox/reviews/display/684?page=7&show=20).  Sadly, that was in May 2009 and doesn't seem fixed.

For now, looks like the best solution would be to install 32-bit FF if that seems to be the issue.  Otherwise, hope for a fix in FF/FireFTP?

I, too, would love a solution.  I was hoping to finally settle on FireFTP for uploading and maintaining web sites, but this kills that since I connect by SSH/SCP.  But, I am considering separately install 32-bit FF just for FireFTP use.

---

### Post by finalwebsites on 2010-01-18
I never used the 64bit version of firefox, so it seems using the 32bit version it's not a fix in my situation. :(

I think that fireftp can't start the putty tools anymore

---

### Post by Nisitiiapi on 2010-01-20
I haven't had any problem with 32-bit.  In fact, I've been using it to ssh to a couple of spots like crazy the last couple days on my netbook.  But, it was initially a clean install of Karmic, not an upgrade from Jaunty.  I only have an issue on my desktop, which is 64-bit Karmic.

Have you tried putty by itself in CLI?  You may have to install it.  FireFTP requires putty-tools, but not putty.

If putty will connect, then it might be a FF/FireFTP issue rather than a putty one.

---

### Post by finalwebsites on 2010-01-20
Maybe it's not related to the 32/64 bit version and instead it's releated to the ubuntu system (updated or clean install).

I used fireftp on the same machine for ~6 month and actually I'm not sure that this problem exists since my update to 9.10.

I'm not sure, but I think I used fireftp for ssh after the update to 9.10 and maybe it's stopped working after the upgrade of fireftp?

Can't say this, I use fireftp for ssh only on my home network, at work I use nautilus.

Maybe it's time to post the problem to the mozilla forum...

---

### Post by Nisitiiapi on 2010-01-25
My FireFTP is 1.0.7 and is o.k.  Firefox is 3.5.7.  I believe both of those are the latest stable releases.  Are those your versions?

Maybe you should try Nautilus to narrow it down to whether it's a FF/FireFTP issue or something else.

I just tried to SSH with FireFTP on my home network and it was fine (using either internal or external address).  I've had trouble with FTP over SSL on my home network in the past (usually just directory listing problem), but SSH seems fine.

---

### Post by finalwebsites on 2010-01-25
Hi,

I'm using the same versions for Firefox and FireFTP.

Using nautilus for SSH connections is not a problem, the same for Putty or the console.

I installed FireFTP because on my home network the is some strange timeout for idle connections (another problem related to my ISP).

Actually I was very surprised that FireFTP has stopped working on SSH connections. After searching the web I found this thread about the ubuntu update and seems to me the only explanation why fireFTP has stopped working for SSH connections.

---

### Post by heyyoyo on 2011-01-24
Same error on ubuntu 10.10 64bit in virtualbox with firefox 3.6.13 and fireftp 1.0.10.
It's the first time I install this ubtuntu, so I didn't make any upgrade. I installed only putty-tools 0.60+2010-02-20-1 with synaptic package manager. my private key is in .ppk format.

---

