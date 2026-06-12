---
title: "Download software with no Internet"
date: 2011-09-20
forum: General Help
---

### Post by argoz17 on 2011-09-20
I know the title is a little odd sounding but that was the only one I could think of haha. So let me first tell you what I am, I have Ubuntu 10.10. It is running on a Dell Dimensions desktop. I have no high speed internet at my house at all. But I do have a MacBook that I do all my internet stuff on it, like at the library or friends house. Now I know say I had windows on the Dell instead of Ubuntu, I can download Windows software onto my mac, burn it to cd or USB stick and install it on Windows....My question is, is there a way to do that on Ubuntu from Mac or Windows. Say I want Compiz on my Ubuntu, is there a way to download files onto Mac/Windows and put it onto my Ubuntu and install it, or would I need the internet? I would like to know if this is possible and if so how do I do it?

---

### Post by haqking on 2011-09-20
> **argoz17 said:**
> I know the title is a little odd sounding but that was the only one I could think of haha. So let me first tell you what I am, I have Ubuntu 10.10. It is running on a Dell Dimensions desktop. I have no high speed internet at my house at all. But I do have a MacBook that I do all my internet stuff on it, like at the library or friends house. Now I know say I had windows on the Dell instead of Ubuntu, I can download Windows software onto my mac, burn it to cd or USB stick and install it on Windows....My question is, is there a way to do that on Ubuntu from Mac or Windows. Say I want Compiz on my Ubuntu, is there a way to download files onto Mac/Windows and put it onto my Ubuntu and install it, or would I need the internet? I would like to know if this is possible and if so how do I do it?

Yeah just download the .deb files and then transfer them, or the source which is likely to be in a .tar file then extract them and compile them, or for system updates and packages then see here [http://keryxproject.org/](http://keryxproject.org/)

Some software will require dependencies so when you install from source or whatever you will need the packages which you would usually apt-get with but with the keyrx cd/dvd you wont have to have internet to do so.

---

### Post by argoz17 on 2011-09-20
Thanks for the quick reply! I am new to the whole compiling thing, exactly how does one do that...It is done in the Terminal I awesome?

---

### Post by haqking on 2011-09-20
> **argoz17 said:**
> Thanks for the quick reply! I am new to the whole compiling thing, exactly how does one do that...It is done in the Terminal I awesome?

**Well to be honest you should steer clear of compiling where possible, if the software is in the software centre then use that, however you dont want to use that due to no internet**.  

So once you know the software you want then visit the website if it has one, you mentioned compiz and im not sure if there is a package for it, if there is then it will be here [http://www.compiz.org/](http://www.compiz.org/)

However you would visit the site and see if a .deb is available and then you can use that, if it is source that you need to compile there there are a few things you need to know about archived packaging and compression formats as well as compiling.

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:
[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

and like i said you can use [http://keryxproject.org/](http://keryxproject.org/) for packages and updates offline, as to compile you will need the build-essential package

then you should be set ;-)

Have fun

Regards

haqking

---

### Post by patryk77 on 2011-09-20
I simply download the packages off [http://packages.ubuntu.com/](http://packages.ubuntu.com/) along with all dependencies.

Just stick all the packages in one folder (/tmp/debs) and run dpkg... ie:
sudo dpkg -i /tmp/debs/*.deb

That is the gist of it, but it may cause some broken dependencies sometimes requiring you to run apt-get -f install PACKAGE_NAME_HERE once you get the dependencies installed...

Another safer way to do this might be to install the same version of Ubuntu in VirtualBox on your MacBook, install apt-proxy on there, and configure your sources on the Dell to download from the virtual install of Ubuntu instead of the official Ubuntu repos.

Much safer, as all the dependencies will be met.

Of course, this requires a LAN between the Dell and the MacBook.

Let me know if you need more details (feel free to message me if I don't reply on here)

Edit: Then again, Keryx might be what you need and simpler to use :P

---

### Post by cpmman on 2011-09-20
If you have an external usb disc you could install ubuntu to that and boot it from bios on your mac/windows machine which you connect to the internet.  Either use the external for your desktop, again via bios or download only packages via apt-get or aptitude and copy to your desktop machine to install thus including dependencies.

---

