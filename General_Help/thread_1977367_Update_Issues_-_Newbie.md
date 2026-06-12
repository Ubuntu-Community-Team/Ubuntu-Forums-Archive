---
title: "Update Issues - Newbie"
date: 2012-05-10
forum: General Help
---

### Post by Nathan Morrison on 2012-05-10
New to Linuxin General, installed Ubuntu and am getting the swing of things... Figured out how to open terminal, and how to achieve root.

I'm running 10.0.4, and I've got both wifi and hard wire connected.

Can't seem to do updates and install packages. 

Here's what happens:

root@nath-SDrive:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gedit liboil0.3 libqtcore4
The following NEW packages will be installed:
  liboil0.3 libqtcore4
The following packages will be upgraded:
  gedit
1 upgraded, 2 newly installed, 0 to remove and 61 not upgraded.
17 not fully installed or removed.
Need to get 0B/2,284kB of archives.
After this operation, 7,201kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: parse error, in file 'var/lib/dpkg/status' near line 183 package 'libclutter-1.0.0':
 'Depends' field, reference to 'libx11-6': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@nath-SDrive:~#




Any help would be great, specifically the commands to type into the terminal to get the right dpkg files.

I've tried to reinstall through Synaptic, and I've tried to remove dpkg using the Ubuntu software system (with intent to re-install it clean...).  But neither works, as each informs me that I have 8 broken packages... 

Thanks so much Linux genius.

- Nath

---

### Post by carl4926 on 2012-05-10
You shouldn't be as root
Only as user, then use sudo

I see from your code you have a root # terminal

Open synaptic and fix broken packages

Don't switch to su - for what you are trying to do
And when you ever are su - you don't then need sudo

---

### Post by Nathan Morrison on 2012-05-10
Thanks Carl!  

I've opened the Synaptic Package Manager, and have filtered for Broken packages.

I have a list of several:
gedit
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
libqt4-dbus
libqt4-network
libqt4-xml
libqtgui4


When I choose one of them and mark it for reinstallation, and then click apply...  I get the following message:

dpkg: parse error, in file '/var/lib/dpkg/status' near line 183 package 'libclutter-1.0.0':
 'Depends' field, reference to 'libx11-6': version contains `'
E: Sub-rocess /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 183 package 'libclutter-1.0.0':
 'Depends' field, reference to 'libx11-6': version contains ` '


How can I fix this?

Thanks,

- Nathan

---

### Post by plucky on 2012-05-10
> dpkg: parse error, in file '/var/lib/dpkg/status' near line 183 package 'libclutter-1.0.0':
'Depends' field, reference to 'libx11-6': version contains `'

The status file it cannot open is a text file that can be edited.

There is also a backup file that might be ok.

Open a terminal and run ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-broken
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

The first command changes the "status" file to a file called "status-broken".
The second command then moves the file status-old to become the new status file.

If that doesn't work you can reverse the naming of the files back to how it was.

**Alternatively** 

You could make a copy of the file with ```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-backup
```

Then edit the file with ```
gksudo gedit /var/lib/dpkg/status
``` and search for **Package: libclutter** and correct the error **'Depends' field, reference to 'libx11-6': version contains `'**

If you make a mess of the edit,you still have an original copy of the file.

This is what my libclutter package look like ```
Package: libclutter-1.0-0
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 1092
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: clutter-1.0
Version: 1.2.4-0ubuntu1
Depends: libc6 (>= 2.7), libcairo2 (>= 1.4.10), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.23.5), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.20.0), libx11-6 (>= 0), libxcomposite1 (>= 1:0.3-1), libxdamage1 (>= 1:1.1), libxext6 (>= 0), libxfixes3 (>= 1:4.0.1)
Description: Open GL based interactive canvas library
 Clutter is an Open GL based interactive canvas library, designed for creating
 fast, mainly 2D single window applications such as media box UIs,
 presentations, kiosk style applications and so on.
Original-Maintainer: Ross Burton <ross@debian.org>
```

Probably easier to use the status-old file first and if that doesn't work,use the Howto and edit the file.

Good Luck

---

### Post by Nathan Morrison on 2012-05-10
So thanks Plucky!  I think I've found the problem in libclutter

However, I've now created an even bigger one.  

My dpkg file is empty...  Is there a command to reinstall dpkg?

Or can someone post the appropriate coding so that I can edit the file in gedit?

Thanks!

- Nathan

---

### Post by plucky on 2012-05-11
> **Nathan Morrison said:**
> So thanks Plucky!  I think I've found the problem in libclutter

However, I've now created an even bigger one.  

My dpkg file is empty...  Is there a command to reinstall dpkg?

Or can someone post the appropriate coding so that I can edit the file in gedit?

Thanks!

- Nathan

Do you mean the status file?

Did you make a copy?

Post the output for ```
ls -l /var/lib/dpkg/
```

---

### Post by Nathan Morrison on 2012-05-11
Actually no Plucky, I mean the dpkg file itself.  

Now when I try to run updates in Terminal, it's telling me that it cannot exec dpkg

So I used  your trick to pull the file up in gedit (didn't make any changes...) and the file is blank.  I'm thinking that's the issue.

The status file is still good, and in fact reads very much like the one you posted, with the obvious changes because I'm running a different system...

I believe the file is: /usr/bin/dpkg

Thoughts as to how to update or replace this file?

Thanks,

- Nathan

---

### Post by Nathan Morrison on 2012-05-11
> **plucky said:**
> Do you mean the status file?

Did you make a copy?

Post the output for ```
ls -l /var/lib/dpkg/
```

Hi Plucky,

I tried this, and got this:

**1s: command not found**

Then I tried it with the prefix: sudo apt-get... and I got this:
**E: Command line option '1' [from -1] is not known.**

Thanks,

- Nathan

---

### Post by Nathan Morrison on 2012-05-11
Figured out how to get my dpkg back in the usr/bin

I loaded ubuntu onto another computer, and copied the file to a thumb drive from that system's bin folder.

Then I moved it in from the terminal using the mv command.

Brilliant, thanks for that trick Plucky.

I'm now back to the point where I'm trying to fix broken packages.  I can't seem to do so properly, but I'll start a new thread about that topic as this issue is pretty much resolved.  Thanks all!

- Nathan

---

### Post by ammofreak on 2012-05-12
Hi ):P
If you have broken packages, then go to *Synaptic Package Manager*, then *Edit*, then *Fix Broken Packages*...hope this helps...:)

---

