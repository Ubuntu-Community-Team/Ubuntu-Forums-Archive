---
title: "apt-get not working because of broken package"
date: 2010-06-21
forum: General Help
---

### Post by j4ss on 2010-06-21
Dear community,

I'm very new to ubuntu and am excperiencing a slight problem.

The problem seems to appear with the following packages:

openoffice.org-common
openoffice.org-core

ant it said before that the broken package is python-uno.

I uninstalled openoffice completely and now when I try to install it again from synaptic, it goes:

```
E: /var/cache/apt/archives/openoffice.org-core_1%3a3.2.0-7ubuntu4.1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.2/program/libfrmli.so')
```


And in the details (i'm sorry i dont know how to copy paste all of this) the last row says: 

```
Errors were encountered while processing:
 python-uno
```

And now the package python-uno appears when I apply the filter 'Broken' in Synaptic. 

I also got a recommendation to run apt-get install -f. Not sure what it does, but here's the output, maybe this will give more info:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-core
The following packages will be upgraded:
  openoffice.org-core
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/27.9MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 155296 files and directories currently installed.)
Preparing to replace openoffice.org-core 1:3.2.0-7ubuntu4 (using .../openoffice.org-core_1%3a3.2.0-7ubuntu4.1_i386.deb) ...
Unpacking replacement openoffice.org-core ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a3.2.0-7ubuntu4.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.2/program/libfrmli.so')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a3.2.0-7ubuntu4.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have an Acer Aspire 5520 laptop and i'm running 10.04 LTS.

I'd be very grateful for any help!

---

### Post by spcwingo on 2010-06-21
You can try:

```
sudo apt-get remove --purge openoffice.org*
```

then:

```
sudo apt-get install openoffice.org
```

If that doesn't work, just let me know so we can try something else.

---

### Post by j4ss on 2010-06-21
thank you for your reply. it did not work. Running sudo apt-get remove --purge openoffice.org* gives the following:

it list all the packages that I selected (a long list) and after that:


```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  aspell: Depends: dictionaries-common (> 0.40) but it is not going to be installed
  aspell-en: Depends: dictionaries-common (>= 0.49.2) but it is not going to be installed
  hunspell-en-ca: Depends: dictionaries-common (>= 0.10) but it is not going to be installed or
                           openoffice.org-updatedicts
  hunspell-en-us: Depends: dictionaries-common (>= 0.10) but it is not going to be installed
  myspell-en-au: Depends: dictionaries-common (>= 1.0) but it is not going to be installed
  myspell-en-gb: Depends: dictionaries-common (>= 0.10) but it is not going to be installed or
                          openoffice.org-updatedicts
  myspell-en-za: Depends: dictionaries-common (>= 0.10) but it is not going to be installed or
                          openoffice.org-updatedicts
  python-uno: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.1) but it is not going to be installed
  wbritish: Depends: dictionaries-common (>= 0.20) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by spcwingo on 2010-06-21
Okay, try this:

Open Synaptic and look at the bottom left of the window.  Press the button there marked "Custom Filters".  Above that you should see "Broken".  Select that filter and uninstall (mark for removal and apply) all the packages that the filter brings up.  Then try to install openoffice again.

---

### Post by j4ss on 2010-06-22
This gets me back to the problem I described in my first post.

```
E: /var/cache/apt/archives/openoffice.org-core_1%3a3.2.0-7ubuntu4.1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.2/program/libfrmli.so')
```

It wants to install python-uno again and fails again.

---

### Post by plucky on 2010-06-22
```
sudo apt-get clean
sudo apt-get install -f
```

The "sudo apt get clean" command will clear out the /var/cache/apt/archives/ of all the downloaded .deb packages and then the "sudo apt-get install -f" command will download the broken package again and try to fix it.

If you want to keep your downloaded packages,then go to /var/cache/apt/archives and remove the openoffice.org-core_1%3a3.2.0-7ubuntu4.1_i386.deb package as that is the one that seems to be broken.


Good Luck

---

### Post by j4ss on 2010-06-22
This seems to have worked.

Thanks a lot guys!

---

