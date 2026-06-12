---
title: "Deleted my authentication files for software sources"
date: 2010-01-13
forum: General Help
---

### Post by Ifaistos on 2010-01-13
Hello everyone :-)

I tried to include new software sources for VLC and Wine.
Something went wrong and the authentication keys didn't work right, and were producing errors of authentication.

In one moment of carelessness (other word for stupidity) I deleted all the authentication keys from the software sources and of course with all the updates I am getting that software cannot be authenticated.

I clicked on "restore defaults" but still it isn't working right.  I tried for example to install "Filezilla" and I got a warning that software could not be authenticated and installation stopped.

Does anyone know how I can restore all the proper authenticating keys?

Thank you all in advance.

---

### Post by konqueror7 on 2010-01-13
> **Ifaistos said:**
> Hello everyone :-)

I tried to include new software sources for VLC and Wine.
Something went wrong and the authentication keys didn't work right, and were producing errors of authentication.

In one moment of carelessness (other word for stupidity) I deleted all the authentication keys from the software sources and of course with all the updates I am getting that software cannot be authenticated.

I clicked on "restore defaults" but still it isn't working right.  I tried for example to install "Filezilla" and I got a warning that software could not be authenticated and installation stopped.

Does anyone know how I can restore all the proper authenticating keys?

Thank you all in advance.

you may want to use '[launchpad-update]("http://deuified.blogspot.com/2009/06/automate-launchpad-ppas-gpg-keys.html")', which automatically download all keys corresponding with the entries in your sources.lst

---

### Post by Ifaistos on 2010-01-13
Unfortunately it didn't work :(

Maybe my sources.lst is broken?
I don't know...

edit: I tool a quick look at the script.  I don't think that it executed any of the commands inside the script.

---

### Post by konqueror7 on 2010-01-13
> **Ifaistos said:**
> Unfortunately it didn't work :(

Maybe my sources.lst is broken?
I don't know...

edit: I tool a quick look at the script.  I don't think that it executed any of the commands inside the script.

can you perhaps post the contents?```
cat /etc/apt/sources.lst
```

---

### Post by Ifaistos on 2010-01-13
I think that we've found the source of the problem....
This is what I get...


[B]cat /etc/apt/sources.lst
cat: /etc/apt/sources.lst: No such file or directory
[/B]
So I guess I need a way to reconstruct the file.

---

### Post by konqueror7 on 2010-01-13
sorry, type, it should be```
cat /etc/apt/sources.list
```

---

### Post by Ifaistos on 2010-01-13
cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by plucky on 2010-01-13
Try this from a terminal window
```
gpg --keyserver keyserver.ubuntu.com --recv 437D05b5
``` then ```
gpg --export --armor 437D05B5 | sudo apt-key add -
``` then ```
sudo apt-get update
``` and see if that works.

Good Luck

---

### Post by Ifaistos on 2010-01-13
this is what I got when I issued thee first command :(  

I guess it failed .. didn't it?

~$ gpg --keyserver keyserver.ubuntu.com --recv 437D05b5

gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/evans/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

---

### Post by plucky on 2010-01-13
> **Ifaistos said:**
> this is what I got when I issued thee first command :(  

I guess it failed .. didn't it?

~$ gpg --keyserver keyserver.ubuntu.com --recv 437D05b5

gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/evans/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

Yes

This is what I get ```
gpg --keyserver keyserver.ubuntu.com --recv 437D05b5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

```

Are you connected to the internet?

---

### Post by Ifaistos on 2010-01-13
Yes I am connected to the internet...

but as you can see it is blocking the calls 

**external program calls are disabled due to unsafe options file permissions**

so I guess I have to fix those permissions first on the gpg.conf file that is mentioning.

---

### Post by Ifaistos on 2010-01-13
bump

---

### Post by Ifaistos on 2010-01-14
bump... please help..

---

### Post by konqueror7 on 2010-01-15
sorry for not replying so fast...

can you please enter this command?```
ls -l ~/.gnupg/gpg.conf
```and post the output here,,thanks

---

### Post by Ifaistos on 2010-01-15
:~$ ls -l ~/.gnupg/gpg.conf
-rw------- 1 evans evans 28 2008-05-10 18:49 /home/evans/.gnupg/gpg.conf
:~$

---

### Post by konqueror7 on 2010-01-15
> **Ifaistos said:**
> :~$ ls -l ~/.gnupg/gpg.conf
-rw------- 1 evans evans 28 2008-05-10 18:49 /home/evans/.gnupg/gpg.conf
:~$
try,
```
chmod 770 ~/.gnupg/gpg.conf
chown -R $USER:$USER ~/.gnupg/gpg.conf
```

---

### Post by plucky on 2010-01-15
```
~$ gpg --keyserver keyserver.ubuntu.com --recv 437D05b5

gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/evans/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
```

I get this error when I run the command with **sudo** in front of it.

This is because using sudo makes you the "root" user and you do not have the correct permissions to use the .gnupg/gpg.conf file which is owned by your user.

Post output of ```
ls -la ~/.gnupg
```

Good Luck

---

### Post by Ifaistos on 2010-01-16
evans@Deep-Black:~$ ls -la ~/.gnupg
total 28
drwxrwxrwx   2 evans evans  4096 2010-01-12 12:36 .
drwxr-xr-x 142 evans evans 12288 2010-01-15 10:16 ..
-rw-------   1 evans evans    28 2008-05-10 18:49 gpg.conf
-rw-rw-rw-   1 evans evans  1196 2007-11-01 11:17 pubring.gpg
-rw-rw-rw-   1 evans evans     0 2007-06-16 19:03 pubring.gpg~
-rw-rw-rw-   1 evans evans     0 2007-06-16 19:03 secring.gpg
-rw-rw-rw-   1 evans evans  1200 2007-11-01 11:17 trustdb.gpg

---

### Post by Ifaistos on 2010-01-16
Conqueror, I did what you asked..

this is what I get...

evans@Deep-Black:~$ ls -l ~/.gnupg/gpg.conf
-rwxrwx--- 1 evans evans 28 2008-05-10 18:49 /home/evans/.gnupg/gpg.conf

edit : I think it works !!  I just updated without getting warning signs.  Could you please explain to me what we did that made the difference?  What was the problem?

Thanks !!

---

### Post by konqueror7 on 2010-01-16
> **Ifaistos said:**
> Conqueror, I did what you asked..

this is what I get...

evans@Deep-Black:~$ ls -l ~/.gnupg/gpg.conf
-rwxrwx--- 1 evans evans 28 2008-05-10 18:49 /home/evans/.gnupg/gpg.conf

have you tried update your cache again?
```
sudo apt-get update
```

---

### Post by Ifaistos on 2010-01-17
&#921; just updated without getting warning signs. Could you please explain to me what we did that made the difference? What was the problem?

Thanks !!

---

### Post by konqueror7 on 2010-01-18
> **Ifaistos said:**
> &#921; just updated without getting warning signs. Could you please explain to me what we did that made the difference? What was the problem?

Thanks !!

oh, the commands changed the file permissions and the owner of the file...for 'chmod', we changef it to writeable, readable, and executable for you and your group, forothers no permissions,,,

for 'chown' we changed the owner to you and your group...

you can check these commands further by issuing the 'man' command, for manual...

```
man chmod
man chown
```

i think the problem was, someone or something accidentally changed those permissions, so you weren't allowed to access or use it...glad it worked!

---

### Post by Ifaistos on 2010-01-19
Thank you conqueror :-)

---

