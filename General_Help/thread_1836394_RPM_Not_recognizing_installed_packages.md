---
title: "RPM Not recognizing installed packages"
date: 2011-08-31
forum: General Help
---

### Post by tyelford on 2011-08-31
Hi all,

I am trying to install a program and I have the script files to install it. However, there is one line in the script file that keeps erroring out and I don't know how to fix it.

The script is calling this:

$ZIP=`rpm -q zip`

if [ ${ZIP} ] ; then
#stuff

else
echo The zip package is not installed

Now when i manually type the command:
rpm -q zip
I get:
package zip is not installed

But if i type:
zip
I get information about the zip package with man files and such.

On the old computer that this script came from if I type
rpm -q zip
I get
zip-2.31-3.fc7

Anyone know how to get rpm to recognize that zip is installed?

Thanks
Tyson

---

### Post by kbaumen on 2011-08-31
Why are you not using the following command?

```
sudo apt-get install zip
```

---

### Post by coffeecat on 2011-08-31
Your old computer appears to be running Fedora:

> **tyelford said:**
> 
On the old computer that this script came from if I type
rpm -q zip
I get
zip-2.31-3.fc7

What distro are you running on the computer you are trying to run the script on now? If you have a script designed for Fedora, it won't work in Ubuntu.

---

### Post by decrepit on 2011-08-31
As said, ubuntu uses synaptic not RPM, it would be better if you could find your packages in the ubuntu repos.
kbaumen's code will do this if zip is in there

---

### Post by kbaumen on 2011-08-31
I don't know about earlier versions, but on 10.04 zip comes with the standard installation. (I did a clean install a couple of days ago and checked for zip to find it already installed).

---

