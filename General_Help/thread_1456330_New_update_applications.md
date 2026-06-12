---
title: "New/ update applications"
date: 2010-04-17
forum: General Help
---

### Post by paulvic on 2010-04-17
Whenever I try to install or update applications I get this message:

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

I've tried what the message suggests, via the Synaptic Package Manager, without success.

Can I reinstall my software management system?  This is a new computer and was working perfectly for a while.  I'd hate to have to give up on this computer, or on Ubuntu, just because I have a glitch.  Surely there has to be a way to solve this?

Thanks,

Paul

---

### Post by 3rdalbum on 2010-04-17
> **paulvic said:**
> Whenever I try to install or update applications I get this message:

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

I've tried what the message suggests, via the Synaptic Package Manager, without success.

Can I reinstall my software management system?

No - even if you could, that probably wouldn't fix the problem. Reinstalling software to fix problems is only really applicable to Windows XP.

Can you run this command for us:

```
sudo apt-get update
```

And give us the exact output of it. Also, can you copy and paste in the contents of the file '/etc/apt/sources.list' into this thread so we can see it.

---

### Post by paulvic on 2010-04-17
> **3rdalbum said:**
> No - even if you could, that probably wouldn't fix the problem. Reinstalling software to fix problems is only really applicable to Windows XP.

Can you run this command for us:

```
sudo apt-get update
```

And give us the exact output of it. Also, can you copy and paste in the contents of the file '/etc/apt/sources.list' into this thread so we can see it.



Paul here, thanks for your help.

When I run sudo apt-get update I get the following.  (NOTE: there's  a long delay at the end of the process, resulting in the final error message.)

Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg                
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release 
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release 
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources      
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources     
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources 
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages       
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages   
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages 
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages 
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources        
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources    
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources  
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2540B]
Fetched 2729B in 2min0s (23B/s)
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.



Finally, when I run terminal and ask for sources I get:

paulvic@paulvic:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied


Thanks again.

Paul

---

### Post by gmargo on 2010-04-17
> **paulvic said:**
> 
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Finally, when I run terminal and ask for sources I get:

paulvic@paulvic:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied


To dump the contents of /etc/apt/sources.list use the cat command:
```

cat /etc/apt/sources.list

```But it is plainly clear that you need to edit the file to comment out the dl.google.com reference.  (Was that for the google browser?  I think I read somewhere that the path for that has changed.)  Then run apt-get update again.

---

### Post by snowpine on 2010-04-17
Looks like the Google browser is not available for your LPIA architecture. To remove the repository from your software sources:

```
gksu gedit /etc/apt/sources.list
```

and type a # symbol at the start of the Google lines to comment them out. Then save the file and try updating again. Good luck!

---

### Post by paulvic on 2010-04-18
> **gmargo said:**
> To dump the contents of /etc/apt/sources.list use the cat command:
```

cat /etc/apt/sources.list

```But it is plainly clear that you need to edit the file to comment out the dl.google.com reference.  (Was that for the google browser?  I think I read somewhere that the path for that has changed.)  Then run apt-get update again.

Thanks so much for your help.  I ran cat/etc/apt/sources.list but see no problems:

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

Any ideas?

Paul

---

### Post by paulvic on 2010-04-18
> **snowpine said:**
> Looks like the Google browser is not available for your LPIA architecture. To remove the repository from your software sources:

```
gksu gedit /etc/apt/sources.list
```

and type a # symbol at the start of the Google lines to comment them out. Then save the file and try updating again. Good luck!

Thanks for your help.  I ran gksu... and a text window opened up with the following:

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted


I see no problems here, nothing to do with Google.

Thanks again,

Paul

---

### Post by snowpine on 2010-04-18
Hi Paul, the Google link must be in a separate file. While you have your 'gksu gedit' window open (as above), do File->Open and look in the /etc/apt and /etc/apt/sources.list.d folders for additional text files that contain the dl.google.com link.

Alternately, if you prefer a GUI way of doing things, you can go to your System menu, choose Administration->Software Sources, and uncheck dl.google.com there. 

Hope you find it, I'm sure it's there somewhere, probably a file called /etc/apt/sources.list.d/google or something like that. :)

---

### Post by 3rdalbum on 2010-04-18
> **snowpine said:**
> You can go to your System menu, choose Administration->Software Sources, and uncheck dl.google.com there.

+1

I'd much prefer you do this; if you modify the sources.list file manually you could accidentally break it. I see it happen literally ten times a week on here :-)  If you use the GUI method to disable that particular software source you can't cause any damage to your package manager.

What are you like for installing/reinstalling Ubuntu? I ask because the Dell Mini version of Ubuntu is compiled to "LPIA" architecture rather than the more common "i386" that your processor also supports. If you install the i386 version of Ubuntu, you'll be able to use common proprietary software (that is generally not compiled to LPIA) and you'll also be able to use a recent version of Ubuntu such as 9.10 or the soon-to-be-released 10.04.

---

### Post by paulvic on 2010-04-19
> **snowpine said:**
> Hi Paul, the Google link must be in a separate file. While you have your 'gksu gedit' window open (as above), do File->Open and look in the /etc/apt and /etc/apt/sources.list.d folders for additional text files that contain the dl.google.com link.

Alternately, if you prefer a GUI way of doing things, you can go to your System menu, choose Administration->Software Sources, and uncheck dl.google.com there. 

Hope you find it, I'm sure it's there somewhere, probably a file called /etc/apt/sources.list.d/google or something like that. :)

Great, that works, I used the GUI route with Software Sources to uncheck the dl.google link.

What do I do now?  Just reboot?  Or run the update?

I think I'm making progress.

Paul

---

### Post by snowpine on 2010-04-19
> **paulvic said:**
> Great, that works, I used the GUI route with Software Sources to uncheck the dl.google link.

What do I do now?  Just reboot?  Or run the update?

I think I'm making progress.

Paul

Yup, just refresh your software sources, using the GUI application of your choice (Update Manager, Synaptic, Software Center, etc.) or:

```
sudo apt-get update
```

And it should skip the Google site this time. :)

---

### Post by paulvic on 2010-04-19
> **3rdalbum said:**
> +1

I'd much prefer you do this; if you modify the sources.list file manually you could accidentally break it. I see it happen literally ten times a week on here :-)  If you use the GUI method to disable that particular software source you can't cause any damage to your package manager.

What are you like for installing/reinstalling Ubuntu? I ask because the Dell Mini version of Ubuntu is compiled to "LPIA" architecture rather than the more common "i386" that your processor also supports. If you install the i386 version of Ubuntu, you'll be able to use common proprietary software (that is generally not compiled to LPIA) and you'll also be able to use a recent version of Ubuntu such as 9.10 or the soon-to-be-released 10.04.

That's an idea, switch to i386.  Then again I've been very happy with this Dell version of Ubuntu, except for the glitch we're talking about here.

Maybe after this is all over... Then again, I've never installed Ubuntu, I bought this computer from Dell with Ubuntu pre-installed.

Paul

---

### Post by paulvic on 2010-04-19
> **snowpine said:**
> Yup, just refresh your software sources, using the GUI application of your choice (Update Manager, Synaptic, Software Center, etc.) or:

```
sudo apt-get update
```

And it should skip the Google site this time. :)



Yep, that worked, the Google site was skipped.

Now what do I do?  Just reboot?

Paul

---

### Post by snowpine on 2010-04-19
> **paulvic said:**
> Yep, that worked, the Google site was skipped.

Now what do I do?  Just reboot?

Paul

No need to reboot, you should be able to install software, use the update manager, etc. normally now.

I have a Dell Mini as well, they are great machines. :)

---

### Post by paulvic on 2010-04-19
> **snowpine said:**
> No need to reboot, you should be able to install software, use the update manager, etc. normally now.

I have a Dell Mini as well, they are great machines. :)

Yes, I like this Dell Mini a lot.  Unfortunately I still can't install applications.  After running apt-get update I ran as follows:
paulvic@paulvic:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be REMOVED:
  cli-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 295kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 39 files and directories currently installed.)
Removing cli-common ...
dpkg: error processing cli-common (--remove):
 cannot remove `/.': Invalid argument
Errors were encountered while processing:
 cli-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


In other words I still have that invalid argument.  Any ideas?

Thanks,
Paul

---

### Post by snowpine on 2010-04-19
> **paulvic said:**
> 
The following packages will be REMOVED:
  cli-common

I'm not sure exactly what cli-common does, but it sounds important. :) You might not want to remove it.

---

### Post by paulvic on 2010-04-20
> **snowpine said:**
> I'm not sure exactly what cli-common does, but it sounds important. :) You might not want to remove it.

Right!  :-)  I want to remove and replace, but I can't do either.

Meanwhile I can't install applications.

Maybe this computer is toast.

Paul

---

### Post by gmargo on 2010-04-20
You could try "dpkg purge cli-common"

---

### Post by paulvic on 2010-04-21
> **gmargo said:**
> You could try "dpkg purge cli-common"

Here's what I got:

paulvic@paulvic:~$ dpkg purge cli-common
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
paulvic@paulvic:~$ 

Which alternative might work best?  Also, how can I back up cli-common before purging?  I'm having trouble finding the file.

Thanks, Paul

---

### Post by snowpine on 2010-04-21
I don't think you want to purge it if you don't know what it does. What about installing it?

```
sudo apt-get install cli-common
```

---

### Post by gmargo on 2010-04-21
> paulvic@paulvic:~$ dpkg purge cli-common
dpkg: need an action optionOops, omitted the double-dash.
```

dpkg --purge cli-common

```> I don't think you want to purge it if you don't know what it does.It's part of the Mono infection. Use "apt-cache show cli-common" or visit [http://packages.ubuntu.com/karmic/cli-common](http://packages.ubuntu.com/karmic/cli-common)

---

### Post by snowpine on 2010-04-21
> **gmargo said:**
> It's part of the Mono infection. Use "apt-cache show cli-common" or visit [http://packages.ubuntu.com/karmic/cli-common](http://packages.ubuntu.com/karmic/cli-common)

Thanks for the clarification. :)

---

### Post by paulvic on 2010-04-22
> **snowpine said:**
> Thanks for the clarification. :)

Perfect, Paul here, thanks.  When I run apt-cache show cli-common I get the following:

paulvic@paulvic:~$ apt-cache show cli-common
Package: cli-common
Priority: optional
Section: interpreters
Installed-Size: 288
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Mono Group <pkg-mono-group@lists.alioth.debian.org>
Architecture: all
Version: 0.5.6
Replaces: cli-common-dev (<< 0.5.1)
Depends: perl-modules
Filename: pool/main/c/cli-common/cli-common_0.5.6_all.deb
Size: 164988
MD5sum: 325d85a44eea1be9b06b9d6e3d12a3b7
SHA1: ec8bb9474c6e84f0ae1c2ce2576e0cf01a768ac7
SHA256: 7d0ee28f59e50b43eb901d3dadb87c58a324453e388915d44421611d88d8d1a8
Description: common files between all CLI packages
 This package must be installed if a CLI (Common Language Infrastructure)
 runtime environment is desired.
 .
 It covers useful integration and information for CLI implementations in
 Debian GNU/Linux, including:
  * The CLI policy describes how CLI packages should behave and integrate.
  * A FAQ for package maintainers of CLI/.NET applications.
  * Integration for CLRs (Common Language Runtime):
    + Installing libraries into existing GACs (Global Assembly Cache)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: edubuntu-desktop-addon

So, question: how do I install a fresh cli-common?  To get rid of the invalid character?

I went to the website, too, but couldn't figure out which cli-common to download.

Thanks, Paul

---

### Post by paulvic on 2010-04-22
> **gmargo said:**
> Oops, omitted the double-dash.
```

dpkg --purge cli-common

```It's part of the Mono infection. Use "apt-cache show cli-common" or visit [http://packages.ubuntu.com/karmic/cli-common](http://packages.ubuntu.com/karmic/cli-common)

I went to the website and downloaded cli-common.  But my system won't let me install it, because of the invalid character explained above.  "Broken" dependency.  Is there any way I can force the install?  The "force" command in Synaptic is unavailable.

Thanks, Paul

---

