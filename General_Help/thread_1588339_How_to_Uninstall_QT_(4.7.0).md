---
title: "How to Uninstall QT (4.7.0)"
date: 2010-10-04
forum: General Help
---

### Post by ChameleonQS on 2010-10-04
how do I uninstall QT4. i downloaded it because it said it was a requirement for skype. bu looking at it skype is really crappy on linux. they really need to release a better version.

i have QT version 4.7.0

i tried software centre, checked my isntalled software, got results but they were only lib files and they added only were like a few Mb, maybe under 50mb. so even if i unintall those i thought i would uninstall the whole program, because the .tar.gz file i downloaded was 199mb

this is probably a noob question for the gods of this forum but please help lol. i really like ubuntu with xfce and i plan to stick with it, just hit a little snag

Thanks.

---

### Post by anglican on 2010-10-05
> **ChameleonQS said:**
> how do I uninstall QT4. i downloaded it because it said it was a requirement for skype. bu looking at it skype is really crappy on linux. they really need to release a better version.

i have QT version 4.7.0

i tried software centre, checked my isntalled software, got results but they were only lib files and they added only were like a few Mb, maybe under 50mb. so even if i unintall those i thought i would uninstall the whole program, because the .tar.gz file i downloaded was 199mb

this is probably a noob question for the gods of this forum but please help lol. i really like ubuntu with xfce and i plan to stick with it, just hit a little snag

Thanks.If you install from a tar.gz file then you must uninstall in the same way. The package management wont know anything about software installed in this way so will not be able to uninstall it (this is why installing from a tar.gz should only be done if there is really no alternative). Presumably you did something like:
```
tar xvfz programfilename.tar.gz
cd programfilename
./configure
make
sudo make install
```so to undo this you need to do:
```
cd programfilename
sudo make uninstall
cd ..
rm -r programfilename programfilename.tar.gz
```If the package you need is available in the repos then you should usually choose to install that way (via synaptic, apt-get... whatever your favourite package management program is) and not from a .tar.gz.

H

---

### Post by ChameleonQS on 2010-10-05
i extracted the files from the .tar.gz file and went into the directory that was on my desktop. i did do what you did to install it, but then i deleted the folder

so cant cd into the same directory. unless your talking about the install directory

---

### Post by stoneage on 2010-10-05
rm -r programfilename programfilename.tar.gz is the command to remove the application directory and the .tar.gz. If you have already removed them you don't this one. 

:)

---

### Post by anglican on 2010-10-05
> **ChameleonQS said:**
> i extracted the files from the .tar.gz file and went into the directory that was on my desktop. i did do what you did to install it, but then i deleted the folder

so cant cd into the same directory. unless your talking about the install directoryThat's another good reason for not installing with a tarball! You need to get that directory back (i.e. download the tarball, extract it and configure it) then try "sudo make uninstall" again. Don't ever delete the directories from which you have run "sudo make install". You can delete much of the contents, but you need all of the Makefiles in order to be able to uninstall. Since QT 4 is in the repos, at a level (admittedly not 4.7) necessary for skype, it should be installed from there. There's probably a PPA of later QT4 if you really needed it.

H

---

### Post by ChameleonQS on 2010-10-05
thanks, im downloading it again lol
will try this, hopefully it works *fingers crossed*

---

### Post by ChameleonQS on 2010-10-05
it doesnt work

 ```
<erywhere-opensource-src-4.7.0$ sudo make uninstall                          
[sudo] password for cqs: 
make: *** No rule to make target `uninstall'.  Stop.
cqs@ALMCQSX:~/Desktop/qt-everywhere-opensource-src-4.7.0$ 

```

---

### Post by Ayuthia on 2010-10-05
Did you rebuild it via ./configure or ./autogen.sh?  I don't think that the needed Makefile is there until you do that step.

---

### Post by anglican on 2010-10-05
> **Ayuthia said:**
> Did you rebuild it via ./configure or ./autogen.sh?  I don't think that the needed Makefile is there until you do that step.Right, that's why I said:
> download the tarball, extract it and configure it:wink:

H

---

### Post by ChameleonQS on 2010-10-05
> **anglican said:**
> Right, that's why I said:
:wink:

H

sorry for missing it anglican, thanks both of you

---

### Post by ChameleonQS on 2010-10-05
ok i used (./configure) but it doesnt make the make file so i cant use the (make) command

---

### Post by gandaran on 2010-10-05
> **ChameleonQS said:**
> ok i used (./configure) but it doesnt make the make file so i cant use the (make) command
what are the errors?
do you remember all the commands you used to install it, (read the readme file for the install instructions), only when it comes to the install command part, type sudo make uninstall instead.

---

### Post by anglican on 2010-10-06
> **ChameleonQS said:**
> ok i used (./configure) but it doesnt make the make file so i cant use the (make) commandYou mentioned that you had removed some stuff with the package management system. You may have removed something essential for a QT4 build, in which case ./configure will fail and not generate Makefiles. Try restoring packages you have removed. If configure fails it usually tells you why and which pre-requisite is missing.

H

---

### Post by ChameleonQS on 2010-10-07
anglican you were right it worked. 
thanks alot
my fault that it didnt work properly the first time
thanks alot!

---

### Post by conmat on 2010-12-17
Check out "checkinstall" (no pun intended)

[http://www.asic-linux.com.mx/~izto/checkinstall/](http://www.asic-linux.com.mx/~izto/checkinstall/)

Automatic uninstall with Synaptic.

---

