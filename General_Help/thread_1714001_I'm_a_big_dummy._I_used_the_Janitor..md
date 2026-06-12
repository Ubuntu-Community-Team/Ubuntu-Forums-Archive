---
title: "I'm a big dummy. I used the Janitor."
date: 2011-03-24
forum: General Help
---

### Post by Husker on 2011-03-24
Hi. I'm fairly new to Ubuntu. I love it and haven't had any problems I couldn't figure out by just reading these forums.

Until now. I ran the janitor, and now I have a a "software index is broken" message. I can't install or remove any software. I have tried Synaptic and ran the "sudo apt get install f" command.

The problem seems to be libdvdcss2, it is marked for removal, but can't be removed. Does anybody have any ideas on what I can to do to fix this? Any help would be greatly appreciated.

Thanks,
Chris

---

### Post by Husker on 2011-03-24
If it helps, sudo apt showed this:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libseed0 gir1.0-pango-1.0 gir1.0-gtk-2.0 gir1.0-gstreamer-0.10
  gir1.0-clutter-1.0 libgirepository1.0-0 gir1.0-atk-1.0 gnome-js-common
  gir1.0-freedesktop gir1.0-glib-2.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libdvdcss2
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 188171 files and directories currently installed.)
Removing libdvdcss2 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libdvdcss2 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libdvdcss2
E: Sub-process /usr/bin/dpkg returned an error code (1)

and this:

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I have 10.04 lucid Lynx

---

### Post by oldos2er on 2011-03-24
> **Husker said:**
>  Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first. 

Have you tried either of these suggestions?

---

### Post by Husker on 2011-03-24
> **oldos2er said:**
> Have you tried either of these suggestions?

Yes. I tried both. This is what I get from Synpatic: E: libdvdcss2: subprocess installed post-removal script returned error exit status 2

I posted what I see from sudo apt-get install -f above.

---

### Post by oldos2er on 2011-03-24
I didn't understand what you meant by "sudo apt." 

Maybe give this a try: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096)

---

### Post by Husker on 2011-03-24
> **oldos2er said:**
> I didn't understand what you meant by "sudo apt." 

Maybe give this a try: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096)

I searched and saw a similar problem; screenlets error code, but I'm not getting that error code.


dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libdvdcss2 (--remove):
subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
libdvdcss2
E: Sub-process /usr/bin/dpkg returned an error code (1)

At this point, I'm willing to give it a shot. 

Thanks for your help, I appreciate it because I need all the help I can get.

---

### Post by oldos2er on 2011-03-25
Sorry I don't know what else to suggest for you.

---

### Post by Husker on 2011-03-25
> **oldos2er said:**
> Sorry I don't know what else to suggest for you.

Thanks for trying. I appreciate it.

---

### Post by Habitual on 2011-03-25
Try this script from karthick87:
[http://askubuntu.com/questions/15584/off-line-repository-and-software-removal](http://askubuntu.com/questions/15584/off-line-repository-and-software-removal)

It works wonders.

---

### Post by Krytarik on 2011-03-25
I believe it is about this package:
[http://packages.medibuntu.org/lucid/libdvdcss2.html](http://packages.medibuntu.org/lucid/libdvdcss2.html)

It is being pulled by this one:
[http://packages.ubuntu.com/lucid/libdvdread4](http://packages.ubuntu.com/lucid/libdvdread4)

Try re-installing the first mentioned manually with "dpkg":
[http://manpages.ubuntu.com/manpages/lucid/en/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/dpkg.1.html)

Good luck!

---

### Post by Husker on 2011-03-25
> **Krytarik said:**
> I believe it is about this package:
[http://packages.medibuntu.org/lucid/libdvdcss2.html](http://packages.medibuntu.org/lucid/libdvdcss2.html)

It is being pulled by this one:
[http://packages.ubuntu.com/lucid/libdvdread4](http://packages.ubuntu.com/lucid/libdvdread4)

Try re-installing the first mentioned manually with "dpkg":
[http://manpages.ubuntu.com/manpages/lucid/en/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/dpkg.1.html)

Good luck!

Thanks. I tried it, but it didn't work. I did it using sudo, not root or superuser though...
I don't know if that makes a difference?

---

### Post by Husker on 2011-03-25
> **Habitual said:**
> Try this script from karthick87:
[http://askubuntu.com/questions/15584/off-line-repository-and-software-removal](http://askubuntu.com/questions/15584/off-line-repository-and-software-removal)

It works wonders.

I'm going try this next. I'm confused about this though:

"Copy the script and paste it in your text editor.And save the file with .sh extension(ie cleaner.sh)Right click the file choose properties>>permissions and check execute.."

I'll go do some research and hopefully figure it out.

Thanks for helping me.

---

### Post by Krytarik on 2011-03-25
> **Husker said:**
> Thanks. I tried it, but it didn't work. I did it using sudo, not root or superuser though...
I don't know if that makes a difference?
No, no difference at all. Any output of the failed install, and the issued command, would be nice.

---

### Post by Husker on 2011-03-25
> **Krytarik said:**
> No, no difference at all. Any output of the failed install, and the issued command, would be nice.

~$ sudo dpkg -i libdvdcss2
dpkg: error processing libdvdcss2 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libdvdcss2

Thats what I got. I'm probably doing it wrong.

---

### Post by Krytarik on 2011-03-25
> **Husker said:**
> ~$ sudo dpkg -i libdvdcss2
dpkg: error processing libdvdcss2 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libdvdcss2

Thats what I got. I'm probably doing it wrong.
- download the .deb-file
- run the command against those file, you need to specify its full name

---

### Post by Husker on 2011-03-25
This is a probably a dumb question, but since I can't download anything because libdvdcss2 can't be deleted, what do I do to download the .deb?

---

### Post by Krytarik on 2011-03-25
> **Husker said:**
> This is a probably a dumb question, but since I can't download anything because libdvdcss2 can't be deleted, what do I do to download the .deb?
The deb-package-file from the site I posted earlier, the first link.

---

### Post by Husker on 2011-03-26
> **Krytarik said:**
> The deb-package-file from the site I posted earlier, the first link.

Krytarik, you are awesome. It worked. Thanks for help and your patience. I owe you one or two.

Also, Thanks oldos2er and Habitual. I learned from your replies, and I appreciate it.

Chris

---

### Post by Krytarik on 2011-03-26
> **Husker said:**
> Krytarik, you are awesome. It worked. Thanks for help and your patience. I owe you one or two.

Great that it finally worked! :)

You're welcome!

---

