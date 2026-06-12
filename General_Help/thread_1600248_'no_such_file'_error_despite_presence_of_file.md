---
title: "'no such file' error despite presence of file"
date: 2010-10-18
forum: General Help
---

### Post by shadowofgrael on 2010-10-18
I just installed a program and do not know what is causing this error.
When I run it from the applications menu I get the following error "Could not launch 'FirstClass Client' :Failed to execute child process "/opt/firstclass/fcc" (No such file or directory)". I opened up a terminal and looked at the location. The file is there.
I do not know much at all in this area but do not understand why this error is occurring. Any help would be nice.

Terminal output: <will@will-Latitude-E6400:/opt/firstclass$ ls -al
total 15128
drwxr-xr-x 10 root root    4096 2009-11-18 13:22 .
drwxr-xr-x  3 root root    4096 2010-10-18 17:51 ..
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 download
-rw-r--r--  1 root root     867 2009-11-18 12:29 fcapps
-rwxr-xr-x  1 root root 7521991 2009-11-18 13:22 fcc
-rwxr-xr-x  1 root root 5315334 2009-11-18 13:22 fccicons.rez
-rw-r--r--  1 root root 2587680 2009-11-18 13:22 fcc.rez
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 fcctemp
-rw-r--r--  1 root root     141 2009-11-18 12:29 fcfonts
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 fcp
-rw-r--r--  1 root root   10281 2009-11-18 12:29 firstclass.png
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 Images
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 plugins
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 settings
drwxr-xr-x  6 root root    4096 2009-11-18 13:22 .svn
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 tools>

---

### Post by coffee412 on 2010-10-18
> **shadowofgrael said:**
> I just installed a program and do not know what is causing this error.
When I run it from the applications menu I get the following error "Could not launch 'FirstClass Client' :Failed to execute child process "/opt/firstclass/fcc" (No such file or directory)". I opened up a terminal and looked at the location. The file is there.
I do not know much at all in this area but do not understand why this error is occurring. Any help would be nice.

Terminal output: <will@will-Latitude-E6400:/opt/firstclass$ ls -al
total 15128
drwxr-xr-x 10 root root    4096 2009-11-18 13:22 .
drwxr-xr-x  3 root root    4096 2010-10-18 17:51 ..
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 download
-rw-r--r--  1 root root     867 2009-11-18 12:29 fcapps
-rwxr-xr-x  1 root root 7521991 2009-11-18 13:22 fcc
-rwxr-xr-x  1 root root 5315334 2009-11-18 13:22 fccicons.rez
-rw-r--r--  1 root root 2587680 2009-11-18 13:22 fcc.rez
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 fcctemp
-rw-r--r--  1 root root     141 2009-11-18 12:29 fcfonts
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 fcp
-rw-r--r--  1 root root   10281 2009-11-18 12:29 firstclass.png
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 Images
drwxr-xr-x  3 root root    4096 2009-08-06 01:15 plugins
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 settings
drwxr-xr-x  6 root root    4096 2009-11-18 13:22 .svn
drwxr-xr-x  3 root root    4096 2009-11-18 13:22 tools>

One post is sufficient.

try this in a term window:

> cd /opt/firstclass
./fcc


Now, Send me a lobster! :P

---

### Post by shadowofgrael on 2010-10-19
The same result: <will@will-Latitude-E6400:/opt/firstclass$ ./fcc
bash: ./fcc: No such file or directory>

I normally wouldn't ask about something this specific, but it was the conflicting presence and absence of the file that I was wondering about

---

### Post by Pfaffa on 2010-10-19
Try:
sudo nautilus /opt/firstclass

Goto the file and them rename it to 'fcc', then try it.  This will make sure the file isn't hiding any non printing characters or unicode look a likes in its name.

---

### Post by oldos2er on 2010-10-19
> **shadowofgrael said:**
> The same result: <will@will-Latitude-E6400:/opt/firstclass$ ./fcc
bash: ./fcc: No such file or directory>


Are you running 64-bit Ubuntu?

---

### Post by shadowofgrael on 2010-10-19
yes I am running 64 bit. I don't like the sound of that question though. Is this a problem?

---

### Post by shadowofgrael on 2010-10-19
<will@will-Latitude-E6400:/opt$ sudo nautilus ./firstclass/
[sudo] password for will: 
Initializing nautilus-gdu extension

** (nautilus:2898): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '2898'

(nautilus:2898): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


^C>

I renamed the file as requested. results are still the same

---

### Post by oldos2er on 2010-10-19
> **shadowofgrael said:**
> yes I am running 64 bit. I don't like the sound of that question though. Is this a problem?

You may need to install ia32-libs if you haven't already; without it you get the error you described when trying to run 32-bit apps (i.e. the system doesn't "see" them).

---

