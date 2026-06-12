---
title: "unable to remove bad package installed from .deb"
date: 2012-03-06
forum: General Help
---

### Post by romanodog on 2012-03-06
I installed a raid configuration package for highpoint rocketraid that I got from the manufacturer's web site.  I'm not sure exactly what happened but something got messed up along the way.

No matter what I try to do (install something else, remove the package, etc.)  I get this message
```
sudo apt-get install -f hptraidconf
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package hptraidconf needs to be reinstalled, but I can't find an archive for it.

```I attempted the steps shown here with no luck: [http://ubuntuforums.org/showpost.php?p=10045070&postcount=6](http://ubuntuforums.org/showpost.php?p=10045070&postcount=6)

Any suggestions?  I don't really need to get this installed again because I have a working package installed now, but I'm unable to install anything else because of this one broken package.

Thanks in advance.

---

### Post by Bobhuber on 2012-03-06
> **romanodog said:**
> I installed a raid configuration package for highpoint rocketraid that I got from the manufacturer's web site.  I'm not sure exactly what happened but something got messed up along the way.

No matter what I try to do (install something else, remove the package, etc.)  I get this message
```
sudo apt-get install -f hptraidconf
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package hptraidconf needs to be reinstalled, but I can't find an archive for it.

```I attempted the steps shown here with no luck: [http://ubuntuforums.org/showpost.php?p=10045070&postcount=6](http://ubuntuforums.org/showpost.php?p=10045070&postcount=6)

Any suggestions?  I don't really need to get this installed again because I have a working package installed now, but I'm unable to install anything else because of this one broken package.

Thanks in advance.
dpkg --remove --force-remove-reinstreq {packagename}

---

### Post by romanodog on 2012-03-06
Here's what I get when I try that:
```
$ sudo dpkg --remove --force-remove-reinstreq hptraidconf
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 115684 files and directories currently installed.)
Removing hptraidconf ...
dpkg (subprocess): unable to execute installed pre-removal script: No such file or directory
dpkg: error processing hptraidconf (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 hptraidconf

```

For the record, the link I posted in the first post mentioned to remove "hptraidconf.postrm" however I never had that file in the first place.

---

### Post by matt_symes on 2012-03-06
Hi

Try this.

Open a terminal and type these commands. Enter your password when prompted. It will not be echoed to the screen.

```
echo "exit 0;" | sudo tee /var/lib/dpkg/info/hptraidconf.prerm
```

```
echo "exit 0;" | sudo tee /var/lib/dpkg/info/hptraidconf.postinst
```

```
sudo dpkg --remove --force-remove-reinstreq hptraidconf
```

The above three commands will create the two files it is looking for and then try to reinstall the package.

Post back errors.

Kind regards

---

### Post by romanodog on 2012-03-06
> **matt_symes said:**
> Hi

Try this.

Open a terminal and type these commands. Enter your password when prompted. It will not be echoed to the screen.

```
echo "exit 0;" | sudo tee hptraidconf.prerm
``````
echo "exit 0;" | sudo tee hptraidconf.postinst
``````
dpkg --remove --force-remove-reinstreq hptraidconf
```The above three commands will create the two files it is looking for and then try to install the package.

Post back errors.

Kind regards

Same thing:
```
o$ sudo dpkg --remove --force-remove-reinstreq hptraidconf
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 115684 files and directories currently installed.)
Removing hptraidconf ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing hptraidconf (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 hptraidconf

```

A little different this time

---

### Post by romanodog on 2012-03-06
ooh, i added #!/bin/sh to the top of the files and it worked!

THANK YOU!!

---

### Post by Bobhuber on 2012-03-06
> **romanodog said:**
> Here's what I get when I try that:
```
$ sudo dpkg --remove --force-remove-reinstreq hptraidconf
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 115684 files and directories currently installed.)
Removing hptraidconf ...
dpkg (subprocess): unable to execute installed pre-removal script: No such file or directory
dpkg: error processingdpkg --remove --force-remove-reinstreq (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 hptraidconf

```For the record, the link I posted in the first post mentioned to remove "hptraidconf.postrm" however I never had that file in the first place.
Try this . We will try to remove the bad script first if it exists.

sudo rm /var/lib/dpkg/info/hptraidconf.postrm
sudo dpkg --remove --force-remove-reinstreq  hptraidconf
sudo dpkg --purge --force-remove-reinstreq hptraidconf

Looks like I'm too late. Glad you got it straightened out.

---

### Post by matt_symes on 2012-03-06
Hi

I should have said, navigate to /var/lib/dpkg/info and run the above commands. I will ammend my above post to make it absolutely clear what i meant. It looks like you created those file in the correct directory though.

They need to be executable as well.

```
sudo chmod 755  /var/lib/dpkg/info/hptraidconf.prerm
```

```
sudo chmod 755  /var/lib/dpkg/info/hptraidconf.postinst
```

```
sudo dpkg --remove --force-remove-reinstreq hptraidconf
```

Post back any errors.

Kind regards

---

### Post by matt_symes on 2012-03-06
Hi

> **romanodog said:**
> ooh, i added #!/bin/sh to the top of the files and it worked!

THANK YOU!!

Nicely done. :)

It sounds like you did not need too much help with that one. You made them executable yourself i take it.

Kind regards

---

### Post by Diametric on 2012-03-06
> **romanodog said:**
> ooh, i added #!/bin/sh to the top of the files and it worked!

THANK YOU!!

Please mark your threads as solved once you have your answer.

---

