---
title: "slapd won't reinstall"
date: 2010-10-24
forum: General Help
---

### Post by ComradeSlice on 2010-10-24
Hello!
This is my first post and I would appreciate all the help I can get.

I effectively broke slapd on my machine so I ran an apt-get purge slapd on it. That went well, but attempting to apt-get install slap results in:

```

root@OT-HQ-1149:~/public/ldapconf# apt-get install slapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  slapd
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Need to get 0B/1,589kB of archives.
After this operation, 4,162kB of additional disk space will be used.
Preconfiguring packages ...
Can't locate object method "new" via package "Debconf::Element::Noninteractive::Booleam" (perhaps you forgot to load "Debconf::Element::Noninteractive::Booleam"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN1> line 5.
(Reading database ... 46009 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.4.23-0ubuntu3.2_amd64.deb) ...
Can't locate object method "new" via package "Debconf::Element::Noninteractive::Booleam" (perhaps you forgot to load "Debconf::Element::Noninteractive::Booleam"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN1> line 5.
dpkg: error processing /var/cache/apt/archives/slapd_2.4.23-0ubuntu3.2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/slapd_2.4.23-0ubuntu3.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I noticed several references to "Debconf::Element::Noninteractive::Booleam". Is that a typo of Boolean? Is this a package problem?

All help is appreciated.

Thanks.

---

### Post by ComradeSlice on 2010-10-24
I would just like to mention this is a very urgent and recurring problem. I've already completely reinstalled the system.

---

### Post by luvshines on 2010-10-24
May you can try to clean the cache
```
sudo apt-get clean
```

---

### Post by ComradeSlice on 2010-10-24
Same thing unfortunately. I would think it's a typo in the package but it installed the first time.

```
root@OT-HQ-1149:~# apt-get install slapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  slapd
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
6 not fully installed or removed.
Need to get 0B/1,589kB of archives.
After this operation, 4,162kB of additional disk space will be used.
Preconfiguring packages ...
Can't locate object method "new" via package "Debconf::Element::Noninteractive::Booleam" (perhaps you forgot to load "Debconf::Element::Noninteractive::Booleam"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN1> line 5.
(Reading database ... 46009 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.4.23-0ubuntu3.2_amd64.deb) ...
Can't locate object method "new" via package "Debconf::Element::Noninteractive::Booleam" (perhaps you forgot to load "Debconf::Element::Noninteractive::Booleam"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN1> line 5.
dpkg: error processing /var/cache/apt/archives/slapd_2.4.23-0ubuntu3.2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/slapd_2.4.23-0ubuntu3.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by luvshines on 2010-10-24
Well, I guess Booleam is infact a typo.

Just check if you actually have Booleam.pm at this location:
```

/usr/share/perl5/Debconf/Element/Noninteractive

```

I have Boolean.pm file there

---

### Post by ComradeSlice on 2010-10-24
> **luvshines said:**
> Well, I guess Booleam is infact a typo.

Just check if you actually have Booleam.pm at this location:
```

/usr/share/perl5/Debconf/Element/Noninteractive

```

I have Boolean.pm file there

I do too but the eror is for "Boolea**m**". I think it might be a package typo. But I have no idea where to begin to fix that.

---

### Post by luvshines on 2010-10-24
**Well this can be insane**, replace Boolean.pm to Booleam.pm and also package statement to "package Debconf::Element::Noninteractive::Booleam" in that file, so that apt-get can find the module when it searches for one

```

/usr/share/perl5$ grep Boolean * -r | grep Deb | grep package | grep Noninte
Debconf/Element/Noninteractive/Boolean.pm:package Debconf::Element::Noninteractive::Boolean;

```

This will be a bit of hack I guess, and I am not sure if it will work.
**Or, better wait for any expert on DEB packages to comment**

---

### Post by ComradeSlice on 2010-10-24
In /usr/share/perl5/Debconf/Element/Noninteractive I copied Boolean.pm to Booleam.pm and changed the package in Booleam.pm to reflect this. Everything works perfectly fine now :confused:. Should I contact the package vendor about this?

---

### Post by luvshines on 2010-10-24
VOILA!! It worked, superb !!
Yeah, you shud contact the concerned person to bring this thing to notice. Others may not be as bright as you at solving this ;)

PS: **I am also editing my earlier post to reflect this. I totally forgot that only Noninteractive Boolean.pm was giving the error and that alone needed to be mended, you were clever to catch that** :D

---

### Post by ComradeSlice on 2010-10-24
I'll contact the author about this. Thank you very much for your help. :)

---

### Post by heggink on 2010-10-27
followed your thread and did teh same thing which caused slapd to install. now i run sudo dpkg-reconfigure slapd and get the same error:

debconf: Unable to load Debconf::Element::Dialog::Booleam. Failed because: Can't locate Debconf/Element/Dialog/Booleam.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 .) at (eval 28) line 2, <GEN6> line 5.
BEGIN failed--compilation aborted at (eval 28) line 2, <GEN6> line 5.

Can't locate object method "new" via package "Debconf::Element::Dialog::Booleam" (perhaps you forgot to load "Debconf::Element::Dialog::Booleam"?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN6> line 5.

Applied the same to Debconf/Element/Dialog/Booleam.pm and now that works too.

---

### Post by drink1297 on 2010-11-01
2 days of messing with this, great solution!!!
I kept telling the wife, if I was able to configure and get DNS to work, I should be able to install slapd.

Thanks! Thanks! Thanks!:)

---

### Post by luvshines on 2010-11-01
> **drink1297 said:**
> 2 days of messing with this, great solution!!!
I kept telling the wife, if I was able to configure and get DNS to work, I should be able to install slapd.

Thanks! Thanks! Thanks!:)

Well my friend, that is what **'The Great Indian Jugaad Technology'** is all about ;)

It is nice to see people using this hack to install slapd, insane solution :D

---

### Post by ComradeSlice on 2010-11-02
I'm now convinced that this is a pure package script issue. I'll be sure to mention the scope of this when I finally write that bug report :)

---

