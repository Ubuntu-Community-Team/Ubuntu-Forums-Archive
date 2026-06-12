---
title: "Can this be installed?"
date: 2009-09-01
forum: General Help
---

### Post by CycloneJoker on 2009-09-01
I just installed Ubuntu Netbook Remix on my Acer Aspire One last night, and so far I love it.  My only problem so far is connecting to my campus's network.

Jumping online using my wired connection in my dorm room works beautifully because Ubuntu doesn't need the same Cisco client my Powerbook needs or my Acer needed when it had XP Home.  But when I'm in the dining hall near my dorm, the campus requires the use of a VPN client when connecting to the wireless network.  They list two clients for Linux, which, when downloaded, are recognized by Ubuntu as being executable files.  But when I click on "Run" or "Run in Terminal", nothing happens.  Nothing at all.  And clearly I lack the experience with the Terminal to try and execute the setup files from there.

But, I'm not really sure if it's meant to run.  The Readme says that it's been reported to work with various other Linux distros, like Fedora and Red Hat, but not specifically Ubuntu.  And of course, campus tech services won't touch Linux issues, so I wouldn't get any help from them.

Like I said, this is my only issue with Ubuntu so far.  Otherwise I've been genuinely enjoying it so far.  What should I do?

---

### Post by SoftwareExplorer on 2009-09-01
Does it work if you right click the file, go to Properties. Then go to permissions tab and Check the check box about Allow execution.

---

### Post by SoftwareExplorer on 2009-09-01
Also, where are you clicking run, or run in terminal? Second, would a vpn client from the repositories work? Third, Weclome to the Ubuntu forums :P
Edit:What are the two clients they listed?

---

### Post by CycloneJoker on 2009-09-03
Sorry it took so long to reply.

The VPN Clients listed on the site that comes up are:

Linux Version 4.0.4 VPN Client
Linux Version 4.6 VPN Client

The "Run" and "Run in Console" commands come up in a dialog box whenever I double click on the VPN_Install file.  I also set it to allow execution.  But it still does nothing.

I'm also not sure about any other VPN client.  Campus Technology Services doesn't handle Linux issues, apparently, only those for Macs and PCs.

---

### Post by jaxxstorm on 2009-09-03
> **CycloneJoker said:**
> Sorry it took so long to reply.

The VPN Clients listed on the site that comes up are:

Linux Version 4.0.4 VPN Client
Linux Version 4.6 VPN Client

The "Run" and "Run in Console" commands come up in a dialog box whenever I double click on the VPN_Install file.  I also set it to allow execution.  But it still does nothing.

I'm also not sure about any other VPN client.  Campus Technology Services doesn't handle Linux issues, apparently, only those for Macs and PCs.

I'm going to take a guess here, and it is a wild guess, that it is either a .run or .sh file.

I'm afraid you'll have to dig into the terminal for it to get working though.

Download it, then move it to your home directory. (firefox downloads files to /home/$USER/Desktop by default, so move it to /home/$USER)

Then open a terminal and do these commands exactly;

```

sudo chmod 777 name_of_file
./name of file

```

To make things easier in the terminal, just type the first three characters of the file name and hit the [TAB] button on your keyboard - it should autocomplete the file name, but it is case sensitive.

Hope that helps, I've subscribed this thread so if you have any trouble/success post back here :D

---

### Post by CycloneJoker on 2009-09-03
Okay, so I moved just the executable file by itself (vpn_install) to my user directory and entered this into the Terminal:

```
sudo chmod 777 vpn_install
```

And nothing happens.  To give a better idea of what happens, this is what I see when I load the terminal:

```
joshua@joshua-laptop:~$
```

I enter the sudo command you gave me after that, and all that happens is that I get the same thing over again, as if I didn't enter a code at all.  If I leave the "vpn_install" file in it's original folder and try the same sudo command, I get:

```
chmod: cannot access 'vpn_install': No such file or directory.
```

---

### Post by CycloneJoker on 2009-09-08
Okay, so after a little experimenting between classes today, I managed to get the vpn_install executable to run in the terminal.  But I seem to have hit another snag.  This is a clip of what happened in the terminal:

```
joshua@joshua-laptop:~$ ./vpn_install
Sorry, you need super user access to run this script.
joshua@joshua-laptop:~$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]/joshua

Directory "/joshua" doesn't exist. Create ? [y]n

Directory where binaries will be installed [/usr/local/bin]/home/joshua

Automatically start the VPN service at boot time [yes]n

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


**Directory containing linux kernel source code [/lib/modules/2.6.28-15-generic/build]**

* Binaries will be installed in "/home/joshua".
* Modules will be installed in "/lib/modules/2.6.28-15-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.28-15-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
sh: Can't open ./driver_build.sh
Failed to make module "cisco_ipsec.ko".
joshua@joshua-laptop:~$ 
```

The bolded section seems to be where the trouble comes in.  The VPN Client's installer points itself at that directory, expecting that the required Kernel source files will be there, but apparently it can't find what it needs.

Any other place I should be pointing it?  Or have I just hit a roadblock entirely?

---

### Post by SoftwareExplorer on 2009-09-08
Just a guess, maybe the packages linux-headers-2.6.28-15 and linux-headers-2.6.28-15-generic need to be installed? Also, it would be a lot easier if a vpn client in the repository worked. kvpnc, vpnc and network-manager-vpnc all say they are cisco compatible, maybe they would work? Also, maybe you need to point the installer to /usr/src/linux-headers-2.6.28-15/arch/x86/ or /usr/src/linux-headers-2.6.28-15/arch/x86/include (I got that from looking at where the packages I mentioned put files).

---

### Post by jaxxstorm on 2009-09-08
it looks to me like it was looking for ./driver_build and it wasn't there.

When you run the script (which I'm assuing you're doing by running ./vpn_client)

try running sudo ./vpn_client instead - giving the script sudo powers will mean you don't run into any permission errors.

---

### Post by CycloneJoker on 2009-09-08
Okay, so after some searching, I thought I found my problem.  Turns out that driver_build.sh was a file in the original folder that the VPN installer came in.  So I figured if I put the installer back in the folder (I removed it because with any previous attempts, if it was in the folder with the other files, I'd get a "File does not exist" error, though using different code to try and run it.  In order to get it to run once back in the folder, I had to modify the code I used to this:

```
sudo ./vpnclient/vpn_install
```

Which started up the process as before.  But I still got the same error about not being able to open ./driver_build.sh.  I keep getting the error regardless of where I tell the script to find the headers, and driver_build.sh ONLY exists in that one folder.

---

### Post by CycloneJoker on 2009-09-09
Okay, I have found myself in a fresh new situation today, of course :)

After looking over the feedback I was getting from the Terminal, I realized something.  Originally, the installer couldn't find driver_build.sh because it wasn't in the same location as vpn_install.  And then, when I put vpn_install back into the original folder, it still couldn't run driver_build.sh because, while my sudo code ("sudo ./vpnclient/vpn_install") was running the installer from the folder, the installer would still be trying to run driver_build.sh using "./driver_build.sh" instead of "./vpnclient/driver_build.sh", and therefore would be unable to find the file because it was pointed to the wrong folder.

So I solved the problem by moving all the files in the folder into my "/home/joshua" directory, where the vpn_install had previously been located alone.  Then, when running the installer using the sudo command in Terminal, it would actually start the process.

Unfortunately, I seem to have hit a new crop of errors.  This is what I get now:

```
joshua@joshua-laptop:~$ sudo ./vpn_install
[sudo] password for joshua: 
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]no

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.28-15-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.28-15-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.28-15-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/joshua modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/joshua/linuxcniapi.o
/home/joshua/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
In file included from /home/joshua/Cniapi.h:15,
                 from /home/joshua/linuxcniapi.c:34:
/home/joshua/GenDefs.h:114: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
/home/joshua/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/joshua/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/joshua/linuxcniapi.c:347: error: ‘struct sk_buff’ has no member named ‘nh’
/home/joshua/linuxcniapi.c:348: error: ‘struct sk_buff’ has no member named ‘mac’
/home/joshua/linuxcniapi.c: In function ‘CniInjectSend’:
/home/joshua/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/joshua/linuxcniapi.c:456: error: ‘struct sk_buff’ has no member named ‘mac’
/home/joshua/linuxcniapi.c:457: error: ‘struct sk_buff’ has no member named ‘nh’
/home/joshua/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘h’
/home/joshua/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/joshua/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/joshua] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
joshua@joshua-laptop:~$ 
```

It seems to be hitting a roadblock with one of it's own files "linuxcniapi.c", among possible other blocks.

---

