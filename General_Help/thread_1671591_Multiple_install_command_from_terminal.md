---
title: "Multiple install command from terminal"
date: 2011-01-20
forum: General Help
---

### Post by Linuxson25 on 2011-01-20
Hi

I am busy installing and updating 20 pc's with Ubuntu on it, one at a time. Don't have sufficient cap to hook every single pc up to the internet to update and install software, so I downloaded all necessary dependencies to one folder on my flashdrive ( the program I need to install on all of them is Wine )

Now...is there a command that will run the install of this file from the folder, letting Terminal know that all dependencies are also in this folder? Do I need to type "sudo apt-get install ....." with every single package name listed in the command?? ](*,)

---

### Post by Vigh on 2011-01-20
sudo apt-get install program1 program2 program3 

will install multiple programs in one command

sudo apt-get build-dep program1 to build dependencies if I remember correctly

---

### Post by sisco311 on 2011-01-20
> **Linuxson25 said:**
> Hi

I am busy installing and updating 20 pc's with Ubuntu on it, one at a time. Don't have sufficient cap to hook every single pc up to the internet to update and install software, so I downloaded all necessary dependencies to one folder on my flashdrive ( the program I need to install on all of them is Wine )

Now...is there a command that will run the install of this file from the folder, letting Terminal know that all dependencies are also in this folder? Do I need to type "sudo apt-get install ....." with every single package name listed in the command?? ](*,)

Copy the .deb. files in /var/cache/apt/archives/ and install the package via apt-get, Synaptic or Software Center:
```
sudo cp /media/USB-NAME/*.deb /var/cache/apt/archives/
```
```
sudo apt-get install wine
```

---

### Post by Cheesehead on 2011-01-20
Let's hope you copied the original Wine .deb package(s) from your /var/cache/apt/archives, and not a lot of other possibilites that will cause you much frustration.

Copy the .deb(s) to the target machine's /var/cache/apt/archives.
If it makes you feel safer, go offline.
Install Wine normally (sudo apt-get install wine).

Sometimes, offline installations take a couple trips if you turn out to be missing a dependency or two.

A simpler and more automated method of doing this kind of offline install is provided by the 'apt-zip' package.

There are two ways to do it online with private networks: Use a caching server ('apt-cache-ng' and similar packages) or use p2p ('debtorrent' or 'apt-p2p' packages)

---

