---
title: "Registered ROTT on Karmic X64"
date: 2010-03-10
forum: General Help
---

### Post by kghosh22 on 2010-03-10
Ever wanted to play your favourite ROTT (the registered version) on Linux ?
(Karmic repositories contain the binary for the shareware version only)
Well now you can !

Installing registered version of ROTT in Karmic - 64bit.

Un-install the ROTT version available in the repositories (since this runs only the shareware version).

Download the rott-registered-1.1.1-0.pm.1.1.x86_64.rpm from -
[http://rpm.pbone.net/index.php3/stat/4/i...4.rpm.html](http://rpm.pbone.net/index.php3/stat/4/i...4.rpm.html)

Mkdir /home/<User>/.rott
Mkdir /home/<User>/.rott/registered

Dump all the files from the registered ROTT CD into /home/<User>/.rott/registered/
Note these files should include the Darkwar WAD files.

Use an archive manager (file-roller) to extract the file rott-registered.bin from rott-registered-1.1.1-0.pm.1.1.x86_64.rpm.
Place the file rott-registered.bin into /home/<User>/.rott/registered/
Make sure it belongs to <User> and is executable.

Create a script /home/<User>/ROTT, containing -

cd /home/<User>/.rott/registered
./rott-registered.bin

and make ROTT executable.

Add ROTT (the script) to your panel and enjoy the registered version of ROTT on linux.

-K.Ghosh

---

