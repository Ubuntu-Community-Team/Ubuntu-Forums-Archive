---
title: "Installing TV tuner"
date: 2009-07-10
forum: General Help
---

### Post by VijayV on 2009-07-10
This is the instruction that came with the tuner I have done everything up to this point but I dont know how to change to the correct directory in the terminal.  Could someone spell this out for me please?

The tools directory has several sets of tools you can use to verify that your
card is working.  We recommend starting with the tools under 
dvb-atsc-tools-1.0.2. Copy that directory to your harddrive, change to that
directory and type:

   > make
   > make install (as root)

---

### Post by t4thfavor on 2009-07-10
Follow the instructions, copy the folder to your home directory.

Then after installing build-essential, open that directory in the terminal, and issue the two commands.

The make compiles the source code to binary (.exe's) and then the make install installs the exe's into apropriate directories on your PC so they can be run from the commandline.

---

### Post by VijayV on 2009-07-10
install --mode=u=rwx,go=rx chopatscfile dtvsignal dtvscan getatsc atscpackets /usr/bin
install: cannot remove `/usr/bin/chopatscfile': Permission denied
install: cannot remove `/usr/bin/dtvsignal': Permission denied
install: cannot remove `/usr/bin/dtvscan': Permission denied
install: cannot remove `/usr/bin/getatsc': Permission denied
install: cannot remove `/usr/bin/atscpackets': Permission denied
make: *** [install] Error 1

this is the error i get when doing make install now

---

### Post by t4thfavor on 2009-07-10
you dont have correct permissions to the files. Its not good practice, but do sudo make and then sudo make install.

Or look into changing the permissions.

---

