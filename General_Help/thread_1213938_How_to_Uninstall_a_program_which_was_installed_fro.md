---
title: "How to Uninstall a program which was installed from source?"
date: 2009-07-15
forum: General Help
---

### Post by UranUtan on 2009-07-15
Hi,

I have compiled Ekiga 3.25 from sources. It has replaced the version 3.20 which was installed by Ubuntu 9.04. 

However, the new version is unable to detect Audio device. I have run **sudo make uninstall** but it doesn't want to go away. Is there a way to remove it permanently so that I can reget the version from the repository?

Or better yet, if you know Ekiga, can you help me to fix the Audio Device detection issue in this post: [http://ubuntuforums.org/showthread.php?t=1213590](http://ubuntuforums.org/showthread.php?t=1213590)

Thanks very much in advance for any help.

---

### Post by Cheesemill on 2009-07-15
If you installed it using **checkinstall** instead of **make install** then you can remove it by simply doing a:
```
sudo dpkg -r <packagename>
```

I know this doesn't help if you used make install but it's usefull to know for future reference :)

---

### Post by mcduck on 2009-07-15
> **UranUtan said:**
> Hi,

I have compiled Ekiga 3.25 from sources. It has replaced the version 3.20 which was installed by Ubuntu 9.04. 

However, the new version is unable to detect Audio device. I have run **sudo make uninstall** but it doesn't want to go away. Is there a way to remove it permanently so that I can reget the version from the repository?

Or better yet, if you know Ekiga, can you help me to fix the Audio Device detection issue in this post: [http://ubuntuforums.org/showthread.php?t=1213590](http://ubuntuforums.org/showthread.php?t=1213590)

Thanks very much in advance for any help.

Usually "sudo make uninstall", ran in the directory where you have the program's source, does the trick. But you really should check the documentation that came with the source code, it should have instructions for uninstalling the program.

And in the future, I recommend using Checkinstall just like Cheesemill suggested.

---

### Post by UranUtan on 2009-07-15
Thanks very much for your quick answers gentlemen. For sure I will remember checkinstall. So instead of typing **sudo make install**, I just type **checkinstall** instead?

The documentation that came with the product [http://wiki.ekiga.org/index.php/Compiling_Ekiga](http://wiki.ekiga.org/index.php/Compiling_Ekiga) 

explicitly mentions **make install** (not even sudo, I wonder why sudo was left out). I hope that the author knows about checkinstall. If he doesn't mention it, may be because he has other ways to uninstall. The INSTALL doc that comes with the sources says nothing about the uninstall procedure.

I ran **sudo make uninstall** in the same repository than where I ran **sudo make install**. And I do the uninstall in the reverse order than the installation (Installation: 1:ptlib, 2:opal, 3:ekiga, Uninstall = 1:ekiga, 2:opal, 3:ptlib).

So if **sudo make uninstall** doesn;t solve my problem, is reformatting the OS the only solution?

---

### Post by mcduck on 2009-07-15
> **UranUtan said:**
> Thanks very much for your quick answers gentlemen. For sure I will remember checkinstall. So instead of typing **sudo make install**, I just type **checkinstall** instead?

The documentation that came with the product [http://wiki.ekiga.org/index.php/Compiling_Ekiga](http://wiki.ekiga.org/index.php/Compiling_Ekiga) 

explicitly mentions **make install** (not even sudo, I wonder why sudo was left out). I hope that the author knows about checkinstall. If he doesn't mention it, may be because he has other ways to uninstall. The INSTALL doc that comes with the sources says nothing about the uninstall procedure.

I ran **sudo make uninstall** in the same repository than where I ran **sudo make install**. And I do the uninstall in the reverse order than the installation (Installation: 1:ptlib, 2:opal, 3:ekiga, Uninstall = 1:ekiga, 2:opal, 3:ptlib).

So if **sudo make uninstall** doesn;t solve my problem, is reformatting the OS the only solution?
Yes, to use checkinstall you simply replace "make install" with "checkinstall" (of course you'll have to install Checkinstall first).

The instructions don't usually mention that because checkinstall isn't the standard way for installing apps from source, but just a handy tool for debian-based distributions to convert the compiled code into a .deb package and installing that so the program can be registered by package management. Since it's not a common Linux standard, and not part of the basic compiling tools, it's usually not mentioned in compiling instructions.

Not having "sudo" in the instructions would be because of the same reason, it's Ubuntu-specific thing and in most distributions people would log in as root to compile & install the program instead of using sudo to do that.

Anyway, if the package doesn't have any specific instructions for uninstalling you should probably try contacting the developers and ask them how it should be uninstalled. Or simply try tracking all the installed files and removing them by hand.

---

### Post by sedawk on 2009-07-15
First I recommend to stick with your version and trying to fix
that audio problem.

But:

What happens if you try to install the default ekiga (after deinstalling
it first?) with apt-get or dpkg ? There are some "force" options
you might try.

If this does not work, you can try this:
Most likely you compiled ekiga with something like
./configure;make;make install
As you said make uninstall does not work (I never tried to
do that myself, so I wouldn't be surprised if that is not
implemented).

What you can try to do is this:
./configure --prefix=/home/<user>/ekigadummy;make ;make install
This will install ekiga to /home/<user>/ekigadummy
Examine that directory to see which files ekiga installed.
If you are sure they are only used by ekiga you know what
you can remove from your default installation directory.
(This will not fully work if ekiga installs files out of
 <prefix> directory. E.g. some programs have a <prefix>
 directory but also install files to /etc instead of <prefix>/etc.
 So more actions are needed).

---

