---
title: "transfer all packages to a new install"
date: 2009-10-21
forum: General Help
---

### Post by nbo10 on 2009-10-21
I have a new system that has installed ubuntu. But I can't connect this computer to the internet to install programs and packages. I have used the command dpkg --get-selections > ~/Desktop/packages.txt on my current machine to get all the packages I want to install on the new system. How can I download all those packages so that I can install them on the new computer? 


The "Generate package download script" under synaptic package manager doesn't seem to work.

Thanks

---

### Post by Barriehie on 2009-10-21
What is preventing the new machinr from connecting to the internet???
 
Barrie

---

### Post by nbo10 on 2009-10-21
It's not really important why I can't connect the computer to the internet. But it boils down to security issues at work.

---

### Post by itsjareds on 2009-10-21
You can use the -d switch on apt-get to download packages only to /var/cache/apt/archives/.

The following command lines assumes that your package list is at ~/packages.txt, and you want to copy these files to your flash drive at /media/usb.

```

sudo apt-get clean
cd /var/cache/apt/archives
sudo apt-get install -d $(cat ~/packages.txt)
sudo apt-get build-dep -d $(cat ~/packages.txt)
```

If you want to compress these packages into a .tar.gz archive,
```
sudo tar czf packages.tar.gz *.deb
sudo mv packages.tar.gz /media/usb
```

If you don't want to compress,
```
sudo cp *.deb /media/usb
```

Then if you want to clean up the files you downloaded (these will remain on the USB once they are copied):
```
sudo apt-get clean
```

Then in your new install, assuming your flash drive (or whichever media you used) is mounted at /media/usb:
```
cd /media/usb
mkdir ~/packages
ln -s /media/usb/packages.tar.gz ~/packages/packages.tar.gz
cd ~/packages
tar xzf packages.tar.gz
rm packages.tar.gz
sudo dpkg -iEG *.deb
```

To clean the temporary directory and packages (packages on your flash drive will not be deleted):
```
rm *.deb
cd ..
rmdir packages
```

Hope this helps

---

### Post by Johnny B on 2009-10-21
#create list of installed packaged:
> sudo dpkg --get-selections > $HOME/package.selections

#restore list: 
> sudo dpkg --set-selections < $HOME/package.selections 

---

### Post by jmszr on 2009-10-21
nbo10,

These may also be of help: [https://help.ubuntu.com/9.04/add-applications/C/offline.html](https://help.ubuntu.com/9.04/add-applications/C/offline.html) and: [https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD) .

---

### Post by itsjareds on 2009-10-21
Hmm.. APTonCD seems much easier than what I posted. I'd recommend doing that also.

---

### Post by nbo10 on 2009-10-21
> **itsjareds said:**
> 

```

sudo apt-get clean
cd /var/cache/apt/archives
sudo apt-get install -d < ~/packages.txt
sudo apt-get build-dep -d < ~/packages.txt
```


This seems like what I want to do but the packages don't download. The output is

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python2.4-dbg diffstat libfftw3-dev python-all-dbg liblapack-dev libblas-dev patchutils quilt python-docutils python-roman python-dbg
  python2.5-dbg cdbs intltool gfortran-4.3 fdupes gfortran libjsw2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.

```

And nothing is downloaded to the current dir.

---

### Post by itsjareds on 2009-10-22
Err, I hadn't really tested my script all the way through. I fixed it in my post above but the script still doesn't work. You'll be better off using APTonCD or apt-zip.

Someone on the Ubuntu irc channel told me about this program apt-zip, which seems like exactly what you need. Unfortunately I couldn't find any good manuals on how to use the command.

[http://linux.about.com/cs/linux101/g/aptzip.htm]("http://linux.about.com/cs/linux101/g/aptzip.htm")

---

### Post by davidryderuk on 2009-10-22
I second using APTonCD. I used it for pretty much the same purpose as you a while ago and it seemed to work great. 

However their is quite a major bug in the version of APTonCD shipped with jaunty.

[https://bugs.launchpad.net/aptoncd/+bug/272509](https://bugs.launchpad.net/aptoncd/+bug/272509)

Thus I would recommend downloading the latest version, which doesn't have the bug. 

[http://downloads.sourceforge.net/aptoncd/aptoncd_0.1-1_all.deb](http://downloads.sourceforge.net/aptoncd/aptoncd_0.1-1_all.deb)


After you've produced the cd then you can just use the feature in the Software sources program that allows you to add repositories on cd's. 

[https://help.ubuntu.com/community/APTonCD#Using%20Local%20Repository](https://help.ubuntu.com/community/APTonCD#Using%20Local%20Repository)

---

### Post by nbo10 on 2009-10-22
I have AptonCD, but I still need to download all the packages that I want to put on the CD. the first try with 

```
sudo apt-get install -d $(cat ~/packages.txt)
```

Didn't seem to download the packages. But I'll try more when I get home tonight.

---

### Post by davidryderuk on 2009-10-22
Packages are cached automatically when you update your computer and install new programmes. Therefore you probably don't need to download the packages again. The link I gave you was for a rather old version of ATPonCD, but the latest version should find the cached packages on your computer.

---

### Post by nbo10 on 2009-10-22
> **davidryderuk said:**
> Packages are cached automatically when you update your computer and install new programmes. Therefore you probably don't need to download the packages again. The link I gave you was for a rather old version of ATPonCD, but the latest version should find the cached packages on your computer.

Only a handful of packages were cached, I think 43. Not all the packages installed were in the cache.

I've come across a  Keryx Project that I'm going to try when I get home.

---

### Post by nbo10 on 2009-10-22
So the Keryx project didnt work But I did find a solution. This website, [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=266551](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=266551) gave the suggestion to use 'aptitude download' command. First I edited the packages file so that only the package names was in the file, I could probably have done this in the python script but I didn't. Then I used the following python script to download all the packages in the file.

```

#!/usr/bin/env python

from subprocess import Popen
import os
print 'start program'
os.chdir('/home/user/debtran') #change dir to download dir
cmd = 'echo $HOME' # test commands
cmd2 = 'aptitude download zlib1g-dev' #test command
strfn = '/home/user/debtran/packages.txt' #file with package names
f = open(strfn, "r") #open file to read package names
pacl = [] # array with package names

for line in f:
    pacl.append(line.rstrip("\n")) # string the newline
    

for ar in pacl:  #lop through all packages

    cmd3 = 'aptitude download ' + ar #+ ' &' #create command to pass to Popen
    print cmd3 #print the command
    returncode = Popen(cmd3, shell=True)
    returncode.wait() #wait for the command to finish 
 
print 'all are downloaded'

```

---

