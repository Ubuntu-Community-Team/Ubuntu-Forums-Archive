---
title: "texlive 2009 + evince = no love"
date: 2010-01-05
forum: General Help
---

### Post by tacutu on 2010-01-05
Hi all,
I have texlive 2009 installed in /usr/local, instead of the older 2007 version which is in the repos.

In my .bashrc I also have ```
export TEXMFCNF=/usr/local/texlive/2009/texmf/web2c/
```

Everything works fine, except for evince. When I try to open a dvi file with it, I get:
```
evince: /usr/local/texlive/2009/texmf/web2c/texmf.cnf: Permission denied

```

Has anyone had this problem and found a solution for it? texmf.cnf is readable by everyone and xdvi doesn't seem to have any trouble opening dvi files. 

Any suggestions are welcome.
Thanks.

---

### Post by tacutu on 2010-01-06
bump!

---

### Post by tacutu on 2010-01-07
Nobody?

---

### Post by lmarmisa on 2010-01-07
Could you post the result of this command:

```

ls -l /usr/local/texlive/2009/texmf/web2c/texmf.cnf

```

---

### Post by meho_r on 2010-01-07
This is my entry in ~/.bashrc:
```
export PATH=/home/mehor/TeXLive/texlive/2009/bin/i386-linux:$PATH
```
As you can see, I installed TeXLive inside my home folder, set path to binaries and everything's working fine. I also have installed base files of TL2007 from Ubuntu repos (required for installation of Kile and Texmaker editors).

---

### Post by tacutu on 2010-01-08
Thanks for the replies

lmarmisa: 
texmf.cnf has these attributes (so it should be ok): -rw-rw-r-- 1 root root 

meho_r: I have symlinks for the binaries in /usr/local/bin, instead of exporting the PATH. It has worked in the past, this cannot be the problem. What base files have you installed from the repos and how can you be sure they don't interfere with the texlive2009 instalation?

---

### Post by tacutu on 2010-01-19
I managed to get it to work. I post the solution here, in case someone elese might stumble onto the same problem:

The culprit was the apparmor profile of evince. After disabling it (look in /etc/apparmor.d), evince works as expected

---

### Post by febrile on 2010-01-19
Sure enough, just stumbled into it today trying to view dvi's with evince. I'd installed texlive 2009 as regular user, but outside my home directory. Initially got the misleading "incorrect format" error as per [https://bugs.launchpad.net/evince/+bug/42410]("https://bugs.launchpad.net/evince/+bug/42410"), resolved it by exporting a TEXMFCNF=/[path-to]/texlive/2009/texmf/web2c/ variable in .bashrc, only to hit this texmf.cnf "permission denied" problem, despite 644 permissions on the file (and 755 on the parent directory).

@tacutu: I'm not sure if you did this or something more targeted, but I used
```
$ sudo aa-complain /usr/bin/evince
```
and sure enough evince displays dvi's fine now. This workaround feels like a blunt instrument, but I looked at /etc/apparmor.d/usr.bin.evince and couldn't see what was causing problems.

Any of you more experienced hands got some thoughts?

---

### Post by tacutu on 2010-01-19
Ideally, the apparmor profile for evince should be modified in order to allow it to read and write where needed. I couldn't be bothered to learn the apparmor syntax, so I just disabled the evince profile:

```
sudo ln -s /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable/
```

---

### Post by sdaau on 2012-04-06
Thank you all for the solution here :) 

Just posted here: [Bug #42410 “evince reports “incorrect format” for DVI files when...” : Bugs : “evince” package : Ubuntu](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/42410) so to note a couple of things from there: 

> 
What I did was:

sudo mv /etc/apparmor.d/usr.bin.evince /etc/apparmor.d/disable/
sudo shutdown -r now

... and after restart, I could run:

TEXMFCNF=/path/to/texlive/2011/texmf/web2c evince mytemp.dvi

... and tex fonts are generated, and the document renders in evince..

Note that calling this path however:

TEXMFCNF=/path/to/texlive/2011 evince mytemp.dvi

... will actually *not* work, even if there is a texmf.cnf file there - it may fail with "page: Error: could not load font" in stdout, and "Unable to open document" in evince.


Thanks again for the solution - Cheers!

---

