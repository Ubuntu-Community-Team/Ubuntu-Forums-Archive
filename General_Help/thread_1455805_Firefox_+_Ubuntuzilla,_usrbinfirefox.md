---
title: "Firefox + Ubuntuzilla, /usr/bin/firefox"
date: 2010-04-16
forum: General Help
---

### Post by Skizzik0 on 2010-04-16
Hello folks, 

I have a problem between Ubuntuzilla (firefox-mozilla-build, 3.6.3-0ubuntu1) and firefox-3.0-branding (3.0.19+nobinonly-0ubuntu0.9.04.1). 

It started when Synaptic tried to upgrade my default branded firefox, I don't remember the exact errors but now the packet firefox-3.0-branding is broken. 

Trying to resolve the issue I removed ubuntuzilla using the python script. 

When I try to remove firefox-3.0-branding it will attempt to remove that packet, upgrade firefox-3.0 and install abrowser-3.0-branding. It fails with the following error (loosely translate i'm afraid):
attempt to overwrite '/usr/bin/firefox' which is also in packet firefox-mozilla-build

It seems that both packets are claiming /usr/bin/firefox, there are no diverts in place (dpkg-divert --list) regarding /usr/bin/firefox

There's no file called 'firefox' in /usr/bin/, only firefox-3.0

I've also attempted to re-install ubuntuzilla (using the python script) which fails and suggest I run 'apt-get -f install', doing so results aptitude attempting to upgrade 'firefox-3.0' which results in the same dpkg error as before "attempt to overwrite '/usr/bin/firefox' which is also in firefox-mozzila-build". 

I'm guessing I need to sort out the dpkg-divert so I no longer have 2 packets claiming /usr/bin/firefox (which doesn't even exist!). 

Any help is appreciated.

---

### Post by lovinglinux on 2010-04-16
Try...

```
sudo apt-get purge firefox
sudo apt-get install firefox
```

Do you have a firefox symlink in /usr/**local**/bin/?

---

### Post by Skizzik0 on 2010-04-17
> **lovinglinux said:**
> Try...

```
sudo apt-get purge firefox
sudo apt-get install firefox
```Do you have a firefox symlink in /usr/**local**/bin/?

The only thing in /usr/local/bin/ is unbuntuzilla.py

There's no packet called firefox installed, trying to 'sudo apt-get purge firefox-3.0-branding' or 'sudo apt-get purge firefox-mozilla-build' results in (loosely translated again, my xubuntu is localized Dutch): 

```

You probably want to do 'apt-get -f install' to solve the following:
The following packets have requirements that are not met:
 firefox-3.0: Requirements: firefox-3.0-branding (>= 3.0.3+nobinonly-0ubuntu1~) but it will be not be installed or
                   abrowser-3.0-branding (>= 3.0.3+nobinonly-0ubuntu1~) but it will not be installed
E: There are requirements that are not met. You should execute 'apt-get -f install' without specifying packets, (or you can specify your own solution). 
```Doing a 'sudo apt-get -f install' results in an error about overwriting /usr/bin/firefox' because it's also in firefox-mozilla-build. 

I think either fixing the divertions or somehow removing both firefox (both default and mozilla-build) packets without having to install abrowser instead (so I can do a fresh install) might fix the problem but I don't know much about divertions and I'm not familiar enough with aptitude to know if there's any way to force it to only remove without trying to install a new packet (that will clash with /usr/bin/firefox).

---

### Post by lovinglinux on 2010-04-17
> **Skizzik0 said:**
> I think either fixing the divertions or somehow removing both firefox (both default and mozilla-build) packets without having to install abrowser instead (so I can do a fresh install) might fix the problem but I don't know much about divertions and I'm not familiar enough with aptitude to know if there's any way to force it to only remove without trying to install a new packet (that will clash with /usr/bin/firefox).

Here is the solution.

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

---

### Post by Skizzik0 on 2010-04-17
> **lovinglinux said:**
> Here is the solution.

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
```
I'm afraid that didn't work, there's no file or folder called /usr/bin/firefox anymore (it's already been removed) and ubuntuzilla.py also removed the divertions. I think I pointed this out in my opening post aswell. 

My understanding of the problem (although I am unexperienced with Linux, packets and dpkg-divert) that there SHOULD be a diversion in place when both packets are installed. By default, both packets have /usr/bin/firefox. Ubuntuzilla normally diverts /usr/bin/firefox to /usr/bin/firefox.ubuntu for the 'regular' firefox (is this possible, diverting a file for only 1 packet?). When I removed Ubuntuzilla using the python script this diversion was also removed. In aptitude however, the 2 firefoxes are both still installed. Trying to uninstall the default ubuntu firefox automatically tries to install abrowser which then causes an error as /usr/bin/firefox is in use by mozilla-firefox-build. 

Would it be possible to divert /usr/bin/firefox to another file (a non-existant file, perhaps) only for firefox-mozilla-build (= ubuntuzilla). Hopefully this will let me fix the error with the default unbuntu firefox by removing it + installing abrowser. 

Another possible solution I thought of, would it be possible to remove the default firefox without installing abrowser (as installing abrowser gives the error because firefox-mozilla-build already uses /usr/bin/firefox)?

---

### Post by lovinglinux on 2010-04-17
Contact [nanotube](http://swiss.ubuntuforums.org/member.php?u=66474) from Ubuntuzilla.

---

### Post by nanotube on 2010-04-18
Hi

don't know what kind of a mess you made there :) or why you're still using the script when there's now a repository... The script and the repository don't really play well together...

Suggest you try the following:
1. remove package firefox-mozilla-build ("sudo apt-get remove firefox-mozilla-build")
2. run "sudo apt-get -f install" and let it take care of the firefox3.0 package
3. install package firefox-mozilla-build ("sudo apt-get install firefox-mozilla-build")
4. do not mess with the 'ubuntuzilla script' anymore, that's deprecated.

---

### Post by Skizzik0 on 2010-04-18
> **nanotube said:**
> Hi

don't know what kind of a mess you made there :) or why you're still using the script when there's now a repository... The script and the repository don't really play well together...

Suggest you try the following:
1. remove package firefox-mozilla-build ("sudo apt-get remove firefox-mozilla-build")
2. run "sudo apt-get -f install" and let it take care of the firefox3.0 package
3. install package firefox-mozilla-build ("sudo apt-get install firefox-mozilla-build")
4. do not mess with the 'ubuntuzilla script' anymore, that's deprecated.

It's a mess indeed. I didn't know about the repository until this mess, as I've never had a reason to look past the script before. 

Trying to remove firefox-mozilla-build gives the following error: 
"The following packages have non-fulfilled requirements: 
         firefox-3.0-branding: Requirements: firefox-3.0 (= 3.0.19+nobinonly-0ubuntu0.9.04.1) but 3.0.18+build1+nobinonly0ubuntu0.9.04.1will be installed
E: There are non-fulfilled requirements. You should run 'apt-get -f install' without specifying packages (or you can specify a solution). "

I've also tried 'sudo apt-get install firefox-3.0' in an attempt to meet the requirement above but this didn't work because of /usr/bin/firefox again. 'apt-get -f install' has the same issue.

---

### Post by nanotube on 2010-04-18
Can you remove firefox-3.0-branding?

---

### Post by Skizzik0 on 2010-04-18
Nope: 

The following packages have non-fulfilled requirements:
   firefox-3.0: Requirements: firefox-3.0-branding (>= 3.0.3+nobinonly-0ubuntu1~) but it will not be installed or
                                  abrowser-3.0-branding (>= 3.0.3+nobinonly-0ubuntu1~) but it will nto be installed
E: there are non-fulfilled requirements. You should use 'apt-get -f install' without specifying packages, (or you can specify a solution).

I've also tried to install abrowser-3.0-branding, it refused to do this with the same error as above aswell as saying abrowser-3.0-branding conflicts with firefox-3.0-branding (duh).

---

### Post by nanotube on 2010-04-18
ok, could you post exactly what the error is from "sudo apt-get -f install"
and also post your output of "dpkg-divert --list"

---

### Post by Skizzik0 on 2010-04-19
Durrr I'm a goof, didn't see the thread had already reached page 2! 

Anyway here's the complete output to those 2 commands: 

sudo apt-get -f install
```
 Packagelists are being read... done
Tree of requirements being build
Status information being read... done
The following extra packages will be isntalled: 
   firefox-3.0
Suggested/recommended packages: 
   firefox-3.0-gnome-support
The following packages will be upgraded: 
  firefox-3.0
1 packages upgraded, 1 package re-installed, 0 to be removed and 0 not upgraded. 
1 packet not completely installed or removed. 

0B/888kB of archives needs to be retried. 
This operation will use 0B of extra diskspace. 
Do you wish to proceed [Y/n]? Y
(Reading database ... 198047 files and folders installed. )
Preparing to replace firefox-3.0 3.0.18+build1+nobinonly-0ubuntu0.9.04.1 (by .../firefox-3.0_3.0.19+nobinonly-0ubuntu0.9.04.1_i386.deb) ...
Extracting replacement firefox-3.0 ...
dpkg: error handling /var/chache/apt/archives/firefox-3.0 3.0.19+nobinonly-0ubuntu0.9.04.1_i386.deb (--unpack):
  attempt to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build
Please restart all running instances of firefox-3.0, or you will experience problems. 
Errors found while handling: 
  /var/cache/apt/archives/firefox-3.0 3.0.19+nobinonly-0ubuntu0.9.04.1_i386.deb
E: sub-process /usr/bin/dpkg returned an error code (1) 
```No firefox related diversions up: 
```
diversion of /bin/sh to /bin/sh.distrib by dash
diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash
diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common
diversion of /usr/bin/screen to /usr/bin/screen.real by screen-profiles
diversion of /usr/share/vim/vim72/doc/help.txt to /usr/share/vim/vim72/doc/help.txt.vim-tiny by vim-runtime
diversion of /usr/share/vim/vim72/doc/tags to /usr/share/vim/vim72/doc/tags.vim-tiny by vim-runtime
local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu
local diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu
```

---

### Post by nanotube on 2010-04-19
well it seems that you have somehow hosed the firefox-mozilla-build diversion. put it back:
```
sudo dpkg-divert --package firefox-mozilla-build --add --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```

then try 'sudo apt-get -f install' again.

---

### Post by Skizzik0 on 2010-04-19
Yeeeees, that's what I was asking for! I'll try it right away.

*edit*
That did it!
Thanks for the great support, best support I've ever had with any product. :D

---

### Post by lovinglinux on 2010-04-19
> **Skizzik0 said:**
> Yeeeees, that's what I was asking for! I'll try it right away.

*edit*
That did it!
Thanks for the great support, best support I've ever had with any product. :D

:popcorn: :popcorn: :popcorn:

Thanks nanotube for helping the OP and solving the problem. I knew you would fix it ;)

---

### Post by nanotube on 2010-04-19
> **Skizzik0 said:**
> Yeeeees, that's what I was asking for! I'll try it right away.

*edit*
That did it!
Thanks for the great support, best support I've ever had with any product. :D

Excellent! Glad to help :)

---

### Post by nanotube on 2010-04-19
> **lovinglinux said:**
> :popcorn: :popcorn: :popcorn:

Thanks nanotube for helping the OP and solving the problem. I knew you would fix it ;)

Thanks for your confidence in me! :) :guitar:

---

### Post by lovinglinux on 2010-04-19
> **nanotube said:**
> Thanks for your confidence in me! :) :guitar:

Well, is not the first time I recommend contacting you for troubleshooting this kind of issue and you solve it. I hope you don't mind. I just do it when is Ubuntuzilla related stuff anyway.

---

### Post by nanotube on 2010-04-20
> **lovinglinux said:**
> Well, is not the first time I recommend contacting you for troubleshooting this kind of issue and you solve it. I hope you don't mind. I just do it when is Ubuntuzilla related stuff anyway.

absolutely - no problem. :)

---

