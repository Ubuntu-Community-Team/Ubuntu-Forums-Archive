---
title: "ubuntu 11.10 64 bit - multiarch dependency hell !!"
date: 2012-02-13
forum: General Help
---

### Post by interzoneuk on 2012-02-13
Hi

I'm trying to install a .deb package for the kerio VPN client - its only 32 bit...

[http://www.kerio.com/control/download#tabset-tab-2](http://www.kerio.com/control/download#tabset-tab-2)

Previously installing 32bit libs would have worked now I cant install correctly 
-----------------------------------

[INDENT]morgan@morgan-N150:~/Downloads$ sudo dpkg -i kerio-control-vpnclient-7.2.2-3443-linux.deb 
Selecting previously deselected package kerio-control-vpnclient:i386.
(Reading database ... 152054 files and directories currently installed.)
Unpacking kerio-control-vpnclient:i386 (from kerio-control-vpnclient-7.2.2-3443-linux.deb) ...
dpkg: dependency problems prevent configuration of kerio-control-vpnclient:i386:
 kerio-control-vpnclient:i386 depends on openssl; however:
  Package openssl:i386 is not installed.
 kerio-control-vpnclient:i386 depends on procps; however:
dpkg: error processing kerio-control-vpnclient:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 kerio-control-vpnclient:i386[/INDENT]

-----------------------------------------


I can't install openssl:i386 ..............


-------------------------------------------------------------
[INDENT] sudo apt-get install openssl:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libmicroblog4 : Depends: libkpimutils4 (= 4:4.7.4-0ubuntu0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
[/INDENT]
-------------------------------------------------------------


The really annoying thing is it does work... (i,.e kerio vpn)

However I am not able to install/upgrade anything with apt-get  - I have to remove the package - apt-get -f install would remove major parts of the os.

How does the multiarch system work?

How can I fix this dep hell (I thought only rpm systems had this issue)

Cheers

---

### Post by Vishnu V on 2012-02-13
I found a solution [here]("http://forums.kerio.com/t/17661/vpn-client-linux-64bit/"), but i never tried it



```

sudo dpkg -i --force-architecture --force-depends kerio-control-vpnclient-###-linux.deb
sudo apt-get install ia32-libs

```

---

### Post by interzoneuk on 2012-02-13
Hi

I think the multiarch changes in Ubuntu 11.10 prevent this from working correctly

[https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#A32-bit_compatibility_on_amd64_systems](https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#A32-bit_compatibility_on_amd64_systems)

> "Ubuntu 11.10 provides "multiarch" support for installing 32-bit library and application packages on 64-bit systems. For all amd64 installs and upgrades, select 32-bit software (like Skype and Flash), will now be installable directly using the same 32-bit packages that are used on i386 installations. You are not required to install the ia32-libs compatibility package. For users, this change means that the 32-bit libraries will always be available at the same time as their 64-bit counterparts, even in the case of security updates, and users will only need to install those 32-bit libraries required by the user's application(s). "

I did 

sudo dpkg -i --force-architecture --force-depends kerio-control-vpnclient-###-linux.deb

sudo apt-get install ia32-libs

As mentioned the application does work - however I can't update/install any packages (without removing the vpn client package)

So - it works but breaks apt-get...

Any suggestions?

---

### Post by Vishnu V on 2012-02-13
Sorry, problem is there

---

### Post by nowashburn on 2012-10-16
Well, I've come up with 2 other ways to do this, though I'm not sure if they are really any better than what was mentioned before nor do I know if they will cause any harm to your system so use at your own risk.

METHOD 1:

1. Download Kerio VPN Client 7.3.2-4445 for Ubuntu 32 bit from [http://www.kerio.com/control/download](http://www.kerio.com/control/download) to your ~/Downloads directory

2. Follow the instuctions here: [http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724) and create a videbcontrol file in your ~/Downloads directory.

3. In terminal run ~/Downloads videbcontrol kerio-control-vpnclient-7.3.2-4445-linux.deb (or replace with the name for whatever version you downloaded). When in vi editor, replace the FULL line that reads "Architecture: i386" to now read "Architecture: amd64". 

4. There should now be a file called kerio-control-vpnclient-7.3.2-4445-linux.modified.deb in the same ~/Downloads directory. You can now install this deb file like you would normally in the Ubuntu Software Center. When installing though the software center there will be a configuration process so have your VPN credentials ready. After configuring and installing you should be automatically connected to your VPN network :)

5. There is no GUI for this client so be sure to read the README file located at: /usr/share/doc/kerio-control-vpnclient/README and learn how to control the client.

METHOD 2:

follow ALL of the same steps above EXCEPT step 3 is different:

3. In terminal run ~/Downloads videbcontrol kerio-control-vpnclient-7.3.2-4445-linux.deb (or replace with the name for whatever version you downloaded). When in vi editor, remove the FULL line that starts with "Depends:". Save the file and exit vi editor. This removes and dependancy checks so IT IS UP TO YOU TO MAKE SURE YOU HAVE THE NESSASARY DEPENDANCIES INSTALLED.  I also noticed that after installing and configuring with this method the Ubuntu Software Center does not register the package to be installed even though everything seems to work just fine with the testing I have done.

Again, do this at your own risk as I am unsure how or why this really works, I was just playing around and came up with this. That being said, I have been using method 1 for quite some time now with no issues on Ubuntu 12.04 64 bit.

I have uploaded a tar.gz file to rapidshare with the files I have created and have used:
[https://rapidshare.com/files/4263275059/kerio.tar.gz](https://rapidshare.com/files/4263275059/kerio.tar.gz)

kerio.tar.gz includes the following:
- both method 1 and method 2 .deb files 
- both Kerio VPN Client stable version 7.3.2, and beta version 7.4.0 for both methods 1 and 2
- videbcontrol and nanodebcontrol (for those who like nano editor better). Full thanks to [http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

Feedback is appreciated. Thanks!

---

