---
title: "Create batch reinstallation script from Synaptic Package Manager"
date: 2011-05-01
forum: General Help
---

### Post by dragonfly41 on 2011-05-01
If I ever have to reinstall ubuntu 10.10 I may need to refer to the history of installations and have an auto-reinstall script ready.   I know that I can create a cloned backup image using backup software such as clonezilla or dd command line .. but I may need to re-install a different mix of applications if I ever have to start again.

I can backup the status of installed (manual) programs in Synaptic Package Manager and Ubuntu Software Centre.   But I first have to select from all those listed and marked green.

Synaptic Package Manager > Status > Installed > File > Generate package download script.

Here is an example of the generated script if I just select one package .. apache2 .. from the list of 1391 listed packages ..

```

#!/bin/sh
wget -c http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.16-1ubuntu3.1_i386.deb

```So how can I filter out from the 1391 listed packages only those packages which I have installed on top of the standard ubuntu distribution (e.g. LAMP, tomcat6 and many others which I installed after a fresh installation of ubuntu)?

Ubuntu Software Centre also provides a useful history of installations by date of installation.  But again I can't export the history of installations.

From the information provided by Synaptic Package Manager and Ubuntu Software Centre I need to export a log of all applications I have installed on top of the standard ubuntu distribution.


[COLOR=DarkRed]**[EDIT]**[/COLOR]

Synaptic Package Manager
Status
select .. Installed (manual)
highlight all files by
           .... click on top entry line
           .... hold down Shift
           .... click on last line

right click on block of all files (1391) .. Mark for Reinstallation
wait some time as list of selected files is marked

Then .. Toolbar > File > Generate package download script

after script is created .. e.g. to ~/Desktop

right click on block of selected files .. Unmark
wait some time as list of selected files is unmarked

Now open the created reinstallation script on Desktop.

Every installed package is listed .. I see 1391 packages ..

But the problem now is to filter out only those which have been installed over ubuntu.

---

### Post by dragonfly41 on 2011-05-01
I've found by experiment that if I go to Synaptic Package Manager and select menu tab "Origin"
and then go through the package groups
click on first column .. Status .. to sort all marked (green) packages together
I can create a more filtered reinstallation script for each of these menu categories.

---

### Post by oldfred on 2011-05-01
You do not have to filter the list. It will only reinstall the ones that are not installed. I have found that you should edit list to remove some older packages, I am still adding python 2.5 back in for example. Your list may have OpenOffice and now LibreOffice is the standard.

You can also do it from command line.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

---

### Post by dragonfly41 on 2011-05-01
Thanks for those added tips oldfred .. I've been searching for that command line approach ..

I've already taken earlier advice by splitting my installation into two partitions to simplify reinstallation
/
/home

but that is only part of the precaution and reinstalling from a backed up list of packages will help.

other precautions I've thought of include changing documentroot for apache2 and tomcat6 to /home locations   ... 

/home/user/public_html      for apache2
/home/user/webapps          for tomcat6

---

