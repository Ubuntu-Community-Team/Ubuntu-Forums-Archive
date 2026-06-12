---
title: "Does anybody know what this means and if I can fix it! (see inside for more details)."
date: 2009-06-26
forum: General Help
---

### Post by Teabicky on 2009-06-26
> (Reading database ... dpkg: unrecoverable fatal error, aborting:  files list file for package `libdbus-qt-1-1c2' is missing final newline E: Sub-process /usr/bin/dpkg returned an error code (2)
 
[COLOR="DarkOrange"]Using Ubuntu 9.04[/COLOR]

I am getting this message when ever I (unsuccessfuly) try to perform an update, either with the update manager or apt-get.

Its the "unrecoverable fatal error" that seems worrying.

---

### Post by ajgreeny on 2009-06-26
Try using synaptic to fix any broken packages.

---

### Post by drs305 on 2009-06-26
If the problem is simply a missing "newline", this command should fix it:
```

sudo cp /var/lib/dpkg/info/libdbus-qt-1-1c2.list /var/lib/dpkg/info/libdbus-qt-1-1c2.list.bak  # Make backup of current file
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libdbus-qt-1-1c2.list
```

---

### Post by Teabicky on 2009-06-26
Thanks to both of you for suggestions.  I have used the one from "drs305" because it seemed specific to my issue, but I will bear ajgreeny's advice in mind if I have any further package problems.   am not good enough to fix these problems with the command line on my own.

Thanks again.

---

### Post by Teabicky on 2009-06-26
> (Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `libdbus-qt-1-1c2' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)


hmmm... apt-get update works now but I am still getting above message with apt-get update.....the plot thickens.

---

### Post by drs305 on 2009-06-26
> **Teabicky said:**
> hmmm... apt-get update works now but I am still getting above message with apt-get update.....the plot thickens.

Here is the contents. Just open and replace the entire contents with this:

```

gksudo gedit /var/lib/dpkg/libdbus-qt-1-1c2.list

```

> 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libdbus-qt-1-1c2
/usr/share/doc/libdbus-qt-1-1c2/NEWS.gz
/usr/share/doc/libdbus-qt-1-1c2/AUTHORS
/usr/share/doc/libdbus-qt-1-1c2/copyright
/usr/share/doc/libdbus-qt-1-1c2/changelog.gz
/usr/share/doc/libdbus-qt-1-1c2/README.gz
/usr/share/doc/libdbus-qt-1-1c2/changelog.Debian.gz
/usr/lib
/usr/lib/libdbus-qt-1.so.1.0.0
/usr/lib/libdbus-qt-1.so.1


---

### Post by Teabicky on 2009-06-26
Have tried that but I am still getting the same problem.  Intrestingly 

/var/lib/dpkg/libdbus-qt-1-1c2

did not exist on my system, so I have made it and copied the info you have suggested.

any more suggestions would still be appreciated.

---

### Post by Teabicky on 2009-06-26
have tried all suggestions and the problem persists.

This is the contents of my /var/lib/dpkg....
> 
alternatives   diversions             lock              status      updates
available      diversions-old         parts             status-old
available-old  info                   statoverride      tmp.ci
cmethopt       libdbus-qt-1-1c2.list  statoverride-old  triggers

This is the contents of libdbus-qt-1-1c2.list in gedit.....


> 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libdbus-qt-1-1c2
/usr/share/doc/libdbus-qt-1-1c2/NEWS.gz
/usr/share/doc/libdbus-qt-1-1c2/AUTHORS
/usr/share/doc/libdbus-qt-1-1c2/copyright
/usr/share/doc/libdbus-qt-1-1c2/changelog.gz
/usr/share/doc/libdbus-qt-1-1c2/README.gz
/usr/share/doc/libdbus-qt-1-1c2/changelog.Debian.gz
/usr/lib
/usr/lib/libdbus-qt-1.so.1.0.0
/usr/lib/libdbus-qt-1.so.1


This is what I see when running the command sudo apt-get update...

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsasl2-2 libsasl2-modules libssl0.9.8 openssl thunderbird
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/14.6MB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `libdbus-qt-1-1c2' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

I hope this info gives a clearer picture of my problem.
:confused::confused::confused:

---

### Post by drs305 on 2009-06-26
Teabicky,

I installed that library to obtain the contents of the .list file. I have now deleted the file and performed an "apt-get udpate" without any problems. I then removed the library without Synaptic complaining. Since you backed up the file with a command in an earlier post, just delete the file outright and see if that solves it.

I prefer not posting "sudo rm" commands but you can do it that way or open nautilus as root and then find and delete the file. It will go into root's trash unless you use SHIFT-DELETE.
```

gksudo nautilus /var/lib/dpkg/info

```

---

### Post by dka on 2009-06-26
Have you tried to use apt-get autoclean or autoremove to delete partial or completed downloads no longer in use?

---

### Post by Teabicky on 2009-06-26
I think that I hav followed instrucions but seem to hav found more problems....... might it be easier for me to reinstall the os?

> sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libsasl2-2 libsasl2-modules libssl0.9.8 openssl thunderbird
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/14.6MB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `cdrdao' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)


Thanks for your patience!

---

### Post by Teabicky on 2009-06-26
> **dka said:**
> Have you tried to use apt-get autoclean or autoremove to delete partial or completed downloads no longer in use?
 
Yeah, I did do that to start with but didn't seem to work.

---

