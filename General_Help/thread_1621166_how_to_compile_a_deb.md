---
title: "how to compile a deb"
date: 2010-11-13
forum: General Help
---

### Post by dante19992 on 2010-11-13
ok this may be the wrong forum but how do i compile a .DEB from a tarball? and give me full step by step instructions preferebly for checkinstall since im not gonna distribute anything. none of that
"./configure
make
sudo checkinstall" crap plz cuz i dont understand it i rly wanna switch from win 7 completely but ill need ur guyz help or im stuck with it T-T.

---

### Post by ubudog on 2010-11-13
Does this help?

[http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

---

### Post by dante19992 on 2010-11-13
i dont even kno how to do the basic compile

---

### Post by ubudog on 2010-11-13
> **dante19992 said:**
> plz i RLY need the help

Umm...did you try that link?

---

### Post by dante19992 on 2010-11-13
sorry i hadnt seen ur reply. no it rly doesnt. i tried it but its a little out of my league atm. i am a windows user with no development skills and a comp moron so i need a guide that can show me the easy way in baby steps.

EDIT: i have no intention of distributing anything so i intend to just use checkinstall i hear its the easy way however it still confuses me

---

### Post by yetiman64 on 2010-11-13
> **dante19992 said:**
> sorry i hadnt seen ur reply. no it rly doesnt. i tried it but its a little out of my league atm. i am a windows user with no development skills and a comp moron so i need a guide that can show me the easy way in baby steps.

EDIT: i have no intention of distributing anything so i intend to just use checkinstall i hear its the easy way however it still confuses me

What is the package you want?

Have you checked the repositories (with Synaptic) or the Ubuntu software centre for it first?

Compiling from source is not recommended for beginners if a version is already packaged.

---

### Post by ubudog on 2010-11-13
There are some graphical tools that may be of use, like...
```
sudo apt-get install debomatic

```

Type that into a terminal (Applications>Accessories>Terminal).

After you ran ./configure, make and make install, you can use the executable most likely located in the "src" directory of the directory of the extracted .tgz.

---

### Post by dante19992 on 2010-11-13
some versions yes but im going to have to learn eventually right?

EDIT: ok ill try that after i figure out the ./configure and make make install stuff.

---

### Post by dante19992 on 2010-11-13
thx for the help guyz.

---

### Post by yetiman64 on 2010-11-13
> **dante19992 said:**
> some versions yes but im going to have to learn eventually right?

The "Ubuntu way" (I will need to look a link for it) is not to recommend to new starters to compile if it is not necessary. 

With upwards of 20000+ apps in the software centre and even more repositories available for enabling (either Ubuntu or sourceforge PPA's) then the chances of you ever needing to compile from source are pretty much negligible.

Some people in Ubuntu can go without ever needing to compile from source as a result of the packaging already done.

If you could please tell us what you want to install someone will likely find it in the repos or find a downloadable .deb installer from a (hopefully) trustworthy site for you.

---

### Post by dante19992 on 2010-11-14
i wanted to install the firefox 4.0 beta actually. However any install packages and ppa directories i found wouldnt install cuz they were "untrusted"

---

### Post by dante19992 on 2010-11-14
would alien work? or is it a virus?

[http://ascarizdiscovery.blogspot.com/2010/07/convert-source-tarbz2-to-ubuntu-deb.html](http://ascarizdiscovery.blogspot.com/2010/07/convert-source-tarbz2-to-ubuntu-deb.html)

---

### Post by yetiman64 on 2010-11-14
Have you checked this link from Ubuntu geek,
[http://www.ubuntugeek.com/how-to-install-firefox-4-0-beta-using-ubuntu-ppa.html](http://www.ubuntugeek.com/how-to-install-firefox-4-0-beta-using-ubuntu-ppa.html).

Has the instructions to install the PPA then installs FF4 beta, all done from a terminal (Applications > Accessories > Terminal). 

Sure beats compiling if you are unsure.

---

### Post by dante19992 on 2010-11-14
tht will work. thx man

---

### Post by |{urse on 2010-11-14
if the package you need is in some other format (rpm for example) you can always try alien

Open a terminal..

> sudo apt-get install alien
alien -d /path/to/package.rpm

---

