---
title: "Lexmark X2600 dpkg error"
date: 2012-08-22
forum: General Help
---

### Post by mjm1231 on 2012-08-22
Lexmark 2600 dpkg install error


I just recently upgraded to Ubuntu 12.04 and am having trouble with installing the driver for the Lexmark X2600. There are a number of threads about installing this printer, and some of them were useful in the past as I had used this printer for several years under 10.04.
	
I extracted the self extracting shell script, and am running the startupinstaller.sh. This errors out during the dpkg install, stating that the problem is caused by a blank line in the Description field in the control file.

This is very much like the bug discussed here: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/916799](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/916799)

So, taking a cue from that bug report I attempted to edit the control file and repackage the .deb. I've never done that before, but how hard can it be? The .deb file is contained in arch.tar...

tar xvf arch.tar
dpkg -x llexmark-inkjet-1.0-1.i386.deb fixup
dpkg -e lexmark-inkjet-1.0-1.i386.deb fixup
cd fixup
nano control
(remove blank lines in the Description, save and exit)
cd ..
dpkg -b fixup lex.deb
mv lex.deb lexmark-inkjet-1.0-1.i386.deb.
rm -rf fixup
tar -c -f arch.tar *
(replace original arch.tar with new arch.tar)

Rerun script, and still get error stating that there is a problem with a blank line in the description field. To prove that I am not crazy, I copy the arch.tar to a second location, and verify that it has the modified control file. Yup, it does. But after I run the installer, the tar file in the install path has the old control file with the bad bad blank lines. How does that happen?


I also tried manually installing the printer (dpkg -i lexmark-inkjet-1.0-1.i386.deb) and that installs the printer. But the printer does not work due to a cups-insecure-printer error.

Help!

---

### Post by dino99 on 2012-08-22
Seems like this user have found the solution:

[http://lembra.wordpress.com/2011/07/20/installing-lexmark-printer-2600-series-on-linux/](http://lembra.wordpress.com/2011/07/20/installing-lexmark-printer-2600-series-on-linux/)

---

### Post by mjm1231 on 2012-08-23
That doesn't work for me. After re-extracting the original driver script, though, I discovered that arch.tar is extracted only after running startupinstaller.sh. How startupinstaller.sh does this magic is beyond my bash script reading skills to discern. As near as I can understand it, startupinstaller.sh launches gtk.... but the script doesn't seem to specify... gtk running what?? So I have no idea where arch.tar is coming from or how to get it use my modified version.

---

### Post by mjm1231 on 2012-08-23
I was able to manually install the driver with the modified control file, then set all permissions and driver file ownerships manually and get the printer to install without errors. Scanning works fine, so tomorrow I will post complete instructions in case anyone needs them.

However, it still does not print, with CUPS error log showing the following:
(/usr/local/lexmark/lxk08/bin/printdriver) crashed on signal 11

So maybe this driver no longer works under Ubuntu 12.04.

---

### Post by wingnux on 2012-08-25
I'm running Ubuntu 12.04 64bit and in desperate need to get this printer to work. Please, post your instructions so I can give it a try.

Thanks in advance!

---

### Post by mjm1231 on 2012-08-26
Sorry, I had a very busy couple of days. Here is the method I used to get the scanner working.

Open a terminal, and navigate to the folder where the downloaded driver is. A lot of these commands require sudo, so I just ran sudo su and ran the whole thing as root.

./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark
cd lexmark/
tar xvf instarchive_all --lzma

To resolve the blank line after description error, I needed to edit and repackage the .deb file

dpkg -x lexmark-inkjet-1.0-1.i386.deb fixup
dpkg -e lexmark-inkjet-1.0-1.i386.deb fixup

cd fixup
cd DEBIAN


open the control file in the editor of your choice

nano control

remove any line breaks separating "Description:" from the text of the description (Lexmark Z2300 etc...). I also removed any line breaks within the description, just in case.
(I prefer a text editor, such as SciTE, that can show the newline characters for this.)

save and close the control file

cd ..
cd ..
dpkg -b  fixup newlexdriver.deb

Now install the new driver manually:

dpkg -i newlexdriver.deb

To resolve the cups-insecure-filter error

sudo chown -hR /usr/lib/cups/filter
sudo chown -hR /usr/lib/cups/backend
sudo chgrp -hR /usr/lib/cups/filter
sudo chgrp -hR /usr/lib/cups/backend

The lexmark driver installs additional files, so you also need:

sudo chown root -hR /usr/loca/lexmark/lxk08/bin
sudo chgrp root -hR /usr/loca/lexmark/lxk08/bin

I think I may have used the chown and chgrp commands on all of /usr/local/lexmark/lxk08, but I can't remember at this point.

This gives me a working scanner, but the printer still fails. CUPS error log shows:

/usr/local/lexmark/lxk08/bin/printdriver) crashed on signal 11.

So close. Right now I only need this to work as a scanner, so good enough for me.

As for 64 bit, there is some good information here:
[http://www.ubuntu-ventures.com/2010/12/install-lexmark-i386-drivers-on-64-bit.html](http://www.ubuntu-ventures.com/2010/12/install-lexmark-i386-drivers-on-64-bit.html) (wish I had found that sooner, would have saved me a lot of trouble reinventing the wheel)
and also here:
[http://ubuntuforums.org/showthread.php?t=1243920](http://ubuntuforums.org/showthread.php?t=1243920)

Good Luck!

---

### Post by wingnux on 2012-08-27
Thanks! Gonna give it a try.

---

### Post by topsites on 2013-01-17
dpkg-deb: error: failed to read archive `lexmark-inkjet-1.0-1.i386.deb': No such file or directory

That makes a lot of sense...
The closest file I see is:  lexmark-inkjet-08-driver-1.0-1.i386.deb
So then, changing:

dpkg -x lexmark-inkjet-1.0-1.i386.deb fixup
dpkg -e lexmark-inkjet-1.0-1.i386.deb fixup

To 
dpkg -x lexmark-inkjet-08-driver-1.0-1.i386.deb fixup
dpkg -e lexmark-inkjet-08-driver-1.0-1.i386.deb fixup

works but...
Get to the part about cd fixup
that's good to but...
cd DEBIAN results in a:
bash: cd: DEBIAN: No such file or directory

Oddly enough the control file is within fixup...
Pico'd that...
Save and close.

Of course now we try
dpkg -b fixup newlexdriver.deb
dpkg-deb: error: failed to open package info file `fixup/DEBIAN/control' for reading: No such file or directory

So then...
Go back to ./fixup
MKDIR DEBIAN
cd DEBIAN
cp /path-to/fixup/control control
cd ..
cd ..

And one more time:
dpkg -b fixup newlexdriver.deb
Seems to have worked!

And:
dpkg -i newlexdriver.deb

Which is all fine and dandy...
Now what do I do, I still don't have a printer configured and it's not in my drop-down list.

Tried - 
./startupinstaller.sh
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
Error opening terminal: xterm.

---

