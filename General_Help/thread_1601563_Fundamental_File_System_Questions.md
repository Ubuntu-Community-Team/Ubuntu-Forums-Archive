---
title: "Fundamental File System Questions"
date: 2010-10-20
forum: General Help
---

### Post by buddyd16 on 2010-10-20
I have been using Ubuntu off and on for a couple years now and have come to the realization that I still do not have a grasp on how exactly the file system works. I have read through some documentation which helped me get a bit of grasp on where items are placed and why they are placed there but there are a couple things I need some clarification on mostly associated with compiling from source code.

lets say I have a folder in my home directory for program source code files:
1. when I compile and install a program from there where exactly is it installed to? 
2. Is the program set up in that same directory or is it in the usr/bin directory? 
3. After installing it is it ok to delete the initial source files?(Probably not advisable in case of a problem with the install but if the install were flawless would deleting the source effect anything?)
4. If I download the updated source code and recompile and install does the new install overwrite the existing one or does it get installed as a different program?

Any answers or links to documentation for me to read on my own are very appreciated

---

### Post by psusi on 2010-10-20
It depends on the program and how you configure it,  but it is customary for make install to put programs in /usr/local/bin.  Yes, you can delete the source after you install, and assuming you build it again with the same configuration ( i.e. you don't tell it to install somewhere else ) then it will overwrite the old one.

---

### Post by srs5694 on 2010-10-20
Psusi's response is correct, but there are some additional wrinkles that can be important:


[list]
[*]The program binary is likely to go in /usr/local/bin (or perhaps /usr/local/sbin or even some other location), but many program packages include man pages, library files, and other files. These will go elsewhere, such as /usr/local/man or /usr/local/lib. Traditionally these all go in /usr/local, but it depends on the specific program.
[*]Keeping the source code around is sometimes desirable because many programs include an "uninstall" target -- that is, you can type "sudo make uninstall" to remove all the files you installed via "sudo make install".
[*]You can keep the source code but minimize the disk space it consumes by typing "make clean". This removes intermediate files created when compiling the software.
[*]Installing a new version over an old version replaces files, as psusi says; however, if the two versions have different files (say, a new program has renamed something), then any files present from the old version but not in the new one will remain in place. This is one reason you might want to use that uninstall target I mentioned earlier -- using the uninstall target from the *old* version before installing the new version will reduce the odds of leaving an "orphaned" file or two.
[/list]


These complications are the reason that package files managed by a package manager, such as the Debian system that Ubuntu uses, are so popular. A centralized package manager eliminates these little risks and annoyances, so that (for instance) when you upgrade, you don't have to worry about old files being left behind; the package manager knows enough to remove any stray files from old packages that you're upgrading. Of course, if you're installing something obscure enough to not have a Debian package, or if you need to customize it in some way, managing one or two packages by compiling locally is perfectly acceptable. If you find yourself doing this sort of thing a lot, you might want to look into alternatives like building your own Debian packages or using a source-based distribution like Gentoo. Depending on your needs, such alternatives may help you manage your system more effectively.

---

### Post by buddyd16 on 2010-10-20
Thanks for the responses.

I had a feeling that is how installing from source worked. 

srs5694 - thanks for going into it in deeper detail I was not aware of the "make clean" command. I assume the make manual would go over the commands that are available in some detail correct?

I have probable installed 1 program from source in the last couple years it just kind of dawned on me that I had no idea what was actually being placed where. It also sounds like a PPA is along the same lines but includes the additional steps to remove/overwrite previous installs and also grabbing the correct dependencies which is a good option when available.

---

