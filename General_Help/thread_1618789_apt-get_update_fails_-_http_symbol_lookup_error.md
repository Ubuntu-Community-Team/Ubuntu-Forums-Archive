---
title: "apt-get update fails - http: symbol lookup error"
date: 2010-11-11
forum: General Help
---

### Post by aohanian on 2010-11-11
Hi all,

I am in the process of switching to Ubuntu from FC and am having some odd issues.
Please bare with me because I am somewhat confused...

First, I installed 10.04.1, then I was prompted to upgrade to 10.04 LTS which I did.
I messed around and got the darn nVidia thing installed (I don't know if this is related, but I thought I should mention it)

After the upgrade, I had some corrupted packages I couldn't re-install.  I edited 'available' and 'status' to remove these (in /var/lib/dpkg), then removed all the related files from the  /var/lib/dpkg/info area.  I then re-installed them with apt-get and everything seemed fine...

So much said, now I can no longer use 'apt-get update' or 'apt-get install ...'.
Basically, can't install anything anymore.

I get the following add error:

# apt-get update
0% [Working]/usr/lib/apt/methods/http: symbol lookup error: /usr/lib/apt/methods/http: undefined symbol: _Z14maybe_add_authR3URISs
E: Method http has died unexpectedly!
E: Sub-process http returned an error code (127)

Please help!  I have been at this for 2 night...

Thanks,
-Arman.

---

### Post by aohanian on 2010-11-11
I thought this might also be relevant...
I 'fixed' the broken packages using the instruction in this post:
[http://ubuntuforums.org/showthread.php?t=540286](http://ubuntuforums.org/showthread.php?t=540286)

Quoting:
1) cd /var/lib/dpkg
2) sudo cp available available.bad
3) sudo cp status status.bad
4a) open available with a text editor.
4b) remove all references to offending package.  Save/close.
5a) open status with a text editor.
5b) remove all references to offending package.  Save/close.
6) cd info
7) delete all files relating to package.  

PLEASE HELP!

---

### Post by psavva on 2010-11-11
> **aohanian said:**
> I thought this might also be relevant...
I 'fixed' the broken packages using the instruction in this post:
[http://ubuntuforums.org/showthread.php?t=540286](http://ubuntuforums.org/showthread.php?t=540286)

Quoting:
1) cd /var/lib/dpkg
2) sudo cp available available.bad
3) sudo cp status status.bad
4a) open available with a text editor.
4b) remove all references to offending package.  Save/close.
5a) open status with a text editor.
5b) remove all references to offending package.  Save/close.
6) cd info
7) delete all files relating to package.  

PLEASE HELP!

Try This:
```
sudo apt-get install --reinstall apt
```

---

### Post by aohanian on 2010-11-11
Thanks Psavva.

I tried that.  I can't install anything since it can't really download anything (apt's http breaks).

However, I was able to download apt from the Lucid repo and installed it with dpkg.  That failed too.  It kept crashing with the same error.

Then, I made a brave move and downloaded the next version of apt from Maverick's repo.  I installed it using dpkg.  This version works.

Thanks for the reply.

I can say this issue is now resolved for me.  Keep an eye out for the 100 other posts about 100 other issues from me.  ;o)

---

### Post by psavva on 2010-11-13
> **aohanian said:**
> Thanks Psavva.

I tried that.  I can't install anything since it can't really download anything (apt's http breaks).

However, I was able to download apt from the Lucid repo and installed it with dpkg.  That failed too.  It kept crashing with the same error.

Then, I made a brave move and downloaded the next version of apt from Maverick's repo.  I installed it using dpkg.  This version works.

Thanks for the reply.

I can say this issue is now resolved for me.  Keep an eye out for the 100 other posts about 100 other issues from me.  ;o)

Hi Aohanian, 

Can you Give exact instruction on what you did, and post it up here so that if anyone else comes into this error, they can fix it :)

Can you also mark this thread as solved...

---

### Post by aohanian on 2010-11-24
Hi,

Sorry for the late reply.  I was away on business for sometime.
I don't recall the exact commands I ran, but here are the steps I took in a nutshell:
1. Initially, I had 10.04LTS installed and was trying to get NVIDIA dirvers working.
2. After trying a few things from the threads, apt-get started crashing (httpd script)
3. I downloaded the new version of apt from 10.10 here:
                [http://packages.ubuntu.com/maverick/apt](http://packages.ubuntu.com/maverick/apt)
4. I used dpkg to install it: dpkg -i apt_0.8.3ubuntu7_i386.deb
5. Restarted the computer and 'apt' was back!
6. I followed the instructions on the forums to upgrade to 10.10.
7. Re-installed the NVIDIA drivers and all worked well!
7-a.  Even though everything was working fine, I chickened out and re-installed 10.10 from scratch.  ;o)

Thanks to all who replied.
Your help and advice is much appreciated!

Thanks,
-Arman.

---

