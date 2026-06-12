---
title: "programs under the systems/administration folder won't authenticate"
date: 2009-09-01
forum: General Help
---

### Post by PhantomFragg on 2009-09-01
This is really my first time here at the forums, and I was wondering if anyone could solve my problems...

I don't have much experience with ubuntu, but I'll do my best.

Whenever I click on ubuntu help, it shows that it's starting, however, it never loads after 20 seconds. That's not the only program that will do that, unfortunately... going to system/administration/authorizations will do the same. Anything I try to unlock will come up with this generic error message: an unexpected error has occured. I bought this laptop with the previous owner's username and password. However, I can't unlock anything, and it doesn't ask for a password either.

I also have something called GNOME, which has my sound, about me, power management and mouse configurations, but I can't seem to open ANY of those programs. It says: Failed to execute child process "gnome-sound-properties" (No such file or directory). Last I checked, I had sound in the system, and the previous user has their sound there and running

Also, while trying to run synaptic package manager, I get this error message: Failed to run /usr/sbin/synaptic as user root.
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator. :confused:

I really would like some guidance, because I'm getting rather attached to Ubuntu. :)

Oh, and I have Ubuntu release 9.04 (jaunty) with kernel linux 2.6.28-15-generic. also, gnome 2.26.1

---

### Post by PhantomFragg on 2009-09-17
Man, I never thought I would be ignored so much as I have just had. I thought, as a new member, I could get some help with my problems with ubuntu. I never new this forum would snub me out because I just wanted some help.

Thanks guys. I feel welcome here.

--pf

---

### Post by wojox on 2009-09-17
Here this will help:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by PhantomFragg on 2009-09-25
> **wojox said:**
> Here this will help:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I was unable to reset the password for the /root folder, which is what I needed to do.
There are important updates for my computer that I cannot install because Synaptic Package Manager can't remove a file because it's protected by /root.

Does anyone know how to reinstall gnome? Or is that something I shouldn't do?

---

### Post by philinux on 2009-09-25
Open a terminal, Apps>Accessories>terminal.

Do these commands one at a time and post back the errors.

```
sudo apt-get update
```
then

```
sudo apt-get upgrade
```

I assume when you first installed everything was ok. What have you done to get to this point? Have you followed any tutorials etc?

---

### Post by PhantomFragg on 2009-09-25
> **philinux said:**
> Open a terminal, Apps>Accessories>terminal.

Do these commands one at a time and post back the errors.

```
sudo apt-get update
```then

```
sudo apt-get upgrade
```I assume when you first installed everything was ok. What have you done to get to this point? Have you followed any tutorials etc?

the first code ran fine, the second one hit with this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  adobe-flashplugin: Depends: libnspr4-dev but it is not installed
                     Depends: libnss3-dev but it is not installed
E: Unmet dependencies. Try using -f.

That's that folder that won't let me get rid of the old version.

[EDIT:] Oh, also, I bought this computer used from a friend, but that friend has since moved away due to his family, and when I got it, some of these programs wouldn't work for me. His user is still here, in fact, I had to access that in order to run sudo.
I'm trying to make me the primary user, since I bought it, but I'm having trouble with gnome as well.

---

### Post by philinux on 2009-09-25
Ok so lets try what it says.

```
sudo apt-get -f install 
```

---

### Post by PhantomFragg on 2009-09-25
> **philinux said:**
> Ok so lets try what it says.

```
sudo apt-get -f install 
```

OK, Synaptic Package Manager also ran into this problem.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  lynx libwxgtk2.8-0 java-common sun-java6-bin unixodbc odbcinst1debian1
  sun-java6-jre libwxbase2.8-0 python-wxversion imagemagick-doc imagemagick
  python-wxgtk2.8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnspr4-dev libnss3-dev
The following packages will be REMOVED:
  linux-headers-2.6.28-11
The following NEW packages will be installed:
  libnspr4-dev libnss3-dev
0 upgraded, 2 newly installed, 1 to remove and 47 not upgraded.
2 not fully installed or removed.
Need to get 255kB/519kB of archives.
After this operation, 63.7MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main libnss3-dev 3.12.3.1-0ubuntu0.9.04.2 [255kB]
Fetched 255kB in 1s (191kB/s)       
(Reading database ... 156768 files and directories currently installed.)
Removing linux-headers-2.6.28-11 ...
dpkg: error processing linux-headers-2.6.28-11 (--remove):
 cannot remove file `/usr/src/linux-headers-2.6.28-11/arch/frv/mm/Makefile': Not a directory
Errors were encountered while processing:
 linux-headers-2.6.28-11
E: Sub-process /usr/bin/dpkg returned an error code (1)

I went to the directory to find what the problem was, and I see "frv" but it's a shell script (application/x-shellscript) type of item.

---

### Post by philinux on 2009-09-25
To be honest in this case I would get the latest Jaunty iso burn it and do a clean install. Backup any important stuff.

We've no idea what the previous owner did. Or how deep the rabbit hole goes.

---

### Post by PhantomFragg on 2009-09-25
> **philinux said:**
> To be honest in this case I would get the latest Jaunty iso burn it and do a clean install. Backup any important stuff.

We've no idea what the previous owner did. Or how deep the rabbit hole goes.

Crap. Well, thanks so much for your help, I'll get that done soon.

"Or how deep the rabbit hole goes" huh? Well, I suppose I'll nuke it from orbit. :lolflag:

Should I consider this closed?

---

### Post by darknight2183 on 2009-09-25
Well, the reinstall will fix all the problems that your having.  But more to the point, I'd try running 

sudo dpkg-reconfigure -a

That should fix the errors that apt is having.  Also, since it's a little unclear to me, are you signing in with his user account to run sudo's or yours.  Reason I ask is that non-admins (aka your user isn't in /etc/sudoers) are able to authenicate.

---

### Post by philinux on 2009-09-25
Unless you need help with a new install. You could start a new thread and mark this solved if thats what you want. 

At least with a clean install the machine will feel like your own.

I set mine up with three partitions using the manual partition method.

/ =root for the system
/home = separate home partition
/swap = for hibernating etc and like windows page file.

---

