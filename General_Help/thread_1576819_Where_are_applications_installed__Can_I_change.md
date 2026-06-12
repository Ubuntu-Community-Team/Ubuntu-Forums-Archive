---
title: "Where are applications installed?  Can I change?"
date: 2010-09-17
forum: General Help
---

### Post by UncleBoarder on 2010-09-17
Bracing for backlash... :-)

I'm a Windows user new to Ubuntu.  I severely customize Windows because it's MY computer not Bill Gate's.

Now I'm trying to understand Ubuntu.  One of the things I always do to Windows is create my own directory structure for program installations,  I do not use "Program Files".

How do I do the same in Ubuntu?  I want a directory structure for Apps, Utils, Programming.  And I want to choose what directory my applications are installed in when I install them.

From what I've seen that appears to be impossible.  It appears programs are installed in /bin /sbin /usr/local and /home

Can I control where things are installed?

---

### Post by flick on 2010-09-17
The simple and easy answer is no, IF you are using standard repositories and using Ubuntu's standard package/program installation utilities, for example, the Ubuntu Software Center.

If you compile your own software from source, you can alter where program files will install themselves to. It's rarely a good idea to do so, however, like any OS, Linux comes with a certain basic structure that developers have grown accustomed to, so official packages/programs respect and use those conventions...and can and will conflict with custom stuff that does not respect those conventions unless the customizer gets to be pretty knowledgeable. 

I've been happily using Ubuntu for five years now, and have rarely needed to venture outside the official repos. Your mileage may vary.

If you're interested in a good no-frills crash course in compiling software under Linux :

[http://everydaylht.com/howtos/system-administration/compiling-software-from-source-code/](http://everydaylht.com/howtos/system-administration/compiling-software-from-source-code/)

---

### Post by kalos on 2010-09-17
> **UncleBoarder said:**
> I want to choose what directory my applications are installed in when I install them.

You cannot do that if you use apt-get because apt-get will also update applications, so they need to stay where it put them.

However, you are free to make your own structure for programs that you install yourself. I have done that myself for applications that aren't packaged with apt-get (examples: world of goo or other games and bleeding-edge versions of eclipse). Generally, there's no install process. I just unzip into my destination directory. However, the automatic housekeeping that comes with apt-get makes me always search out apt-get versions first :)

---

### Post by Jesus_Valdez on 2010-09-17
Why do you want this? What is the advantanges that you want to achive by installing software in a different folder?

Also, you can try other linux distribution if you want total control of your PC, like those where you need to compile everything.

---

### Post by UncleBoarder on 2010-09-17
Would I be pushing the envelope too far to move my /bin directory to my second drive?  My goal is to have a small system drive (It's a small solid state drive) and use my second drive for applications.

I've already moved /home to my second drive, so if moving /bin isn't too radical, it seems it would reduce the drive space needed in the future as I install applications.

Thoughts?

---

### Post by Jesus_Valdez on 2010-09-17
Why don't you try a minimal installation instead?

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by UncleBoarder on 2010-09-17
Wow, that's cool!

But my question stands.  Is moving /bin a bad idea?

---

### Post by 3rdalbum on 2010-09-18
> **UncleBoarder said:**
> Wow, that's cool!

But my question stands.  Is moving /bin a bad idea?

Moving /bin is a bad idea, and won't free up much space. You could move /usr/ instead and free much more space without breaking your system.

Linux programs are smaller than Windows programs anyway so you might not need to do this anyway. You can categorize your programs in the menu rather than in the filesystem.

---

### Post by UncleBoarder on 2010-09-19
I tried moving /usr.  I like the idea but the reality is that it slows down my system because I moved it from a SSD to a HD.  So what I really want is a way to decide which apps are installed on the SSD and which apps are installed on the HD.

In Windows I would do that at installation by selecting the install directory.

Can someone help me with doing it in Ubuntu?

---

### Post by bodhi.zazen on 2010-09-19
FYI :


[IMG]http://techbu.com/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg[/IMG]

[Linux file system explained for beginners | TechBU]("http://techbu.com/2009/06/28/linux-file-system-explained-for-beginers/") 

[LinuxFilesystemTreeOverview - Community Ubuntu Documentation]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview") 

You can mount various parts of your file system on alternate partitions, a separate /home or /data partition is most common, this preserves your data if you wish to re-install Ubuntu.

You can specify a location when you compile applications from source code, it is "standard practice" to specify /usr/local for example , in the "configure" step

```
./configure --prefix=/usr/local
```[https://wiki.ubuntu.com/CompilingSoftware](https://wiki.ubuntu.com/CompilingSoftware)

If all that is Greek , stay with the defaults until you are more familiar with Linux.

---

### Post by kaway1337 on 2010-09-19
you could move the applications you want to the SSD and add symlinks in /bin to point to the new location on the SSD.

eg assuming you want the application "/bin/grep" in the "bin" directory on your SSD (mounted as "/mnt/SSD")
```

mv /bin/grep /mnt/SSD/bin
ln -s /mnt/SSD/bin/grep /bin/grep

```

you have to use symbolic links (hence "-s") rather than hard links because you are crossing a system boundary.

this would make the application appear as if it was in both places at the same time, so you dont run into path issues (which you will do if you just straight up move the file).

---

### Post by 3Miro on 2010-09-19
The problem is far more complicated that you think. One of the reasons that you have this "complicated" setup with /bin /usr and /home under Linux is because Linux apps are nothing like windows app.

When some company makes a windows app, they make it almost completely self contained. That is, the app comes with all the libraries that it needs to run. Due to legality, even if two apps can share a component, they will both come with their own separate component.

When someone makes an app under Linux, they alway break it downs into a bunch of individual components. Then different apps share those components. **Shared libraries** are located under /lib /usr/lib and /usr/share/lib). All Linux program share components and that is why they cannot be separated like the ones under windows.

The main advantage of such an approach is that the sum total of all Linux programs is much smaller than what you would expect under Windows. Ubuntu is happy to live with Gnome, KDE and XFCE along with a large assortment of apps on a 20GB drive. So if your sdd is at least 20GB, I wouldn't worry about it. If you stick to Gnome only, 10 - 15GB will probably be OK as well. Keep an eye on the disk usage (from System -> Admin -> System Monitor) and if the drive starts to get full, erase something.

---

### Post by bodhi.zazen on 2010-09-19
If you moved all the files in /bin to a new partition, you would be better off mounting /bin in /etc/fstab.

Links will work if you have a few files, and in fact, if you look, firefox, for example, is a link.

---

### Post by UncleBoarder on 2010-09-19
You guys are awesome.  I kind of expected "go back to windows" comments, but I didn't get even one.  And thanks for the detailed explanation of Ubuntu vs. Windows! :-)

I'll play with your suggestions this week.

THANKS!!!

---

### Post by 3Miro on 2010-09-19
> **UncleBoarder said:**
> You guys are awesome.  I kind of expected "go back to windows" comments, but I didn't get even one.  And thanks for the detailed explanation of Ubuntu vs. Windows! :-)

I'll play with your suggestions this week.

THANKS!!!

And then you will go back to Windows ;-):biggrin:;-)

---

### Post by SeijiSensei on 2010-09-19
One other aspect of file locations has to do with the boot process.  *nix machines boot up first in single-user mode (rather like "safe mode" in Windows) without any multi-tasking yet enabled.  This is called runlevel 1.  At this runlevel the /usr branch of the directory tree is not used at all.  In the olden days when disk space was at a premium, /usr was often on another partition or another drive.  So Unix was built to only use files in /usr when the system is running in multi-user mode, which are typically runlevels 3 (text mode) or 5 (X-Windows).

All this means that files in /bin and /sbin are ones the system expects to have available at all runlevels.  It wouldn't be a good idea to arbitrarily move files from these directories to another drive that may, or may not, be mounted when the OS needs them.

It's customary to put applications that are outside the packaging system in /usr/local.  So, for instance, if I want to compile a program from scratch, I'll download the source "tarball" to /usr/local/src and extract and compile it there.  After compilation, the binaries are usually automatically installed in /usr/local/bin or /usr/local/sbin, with their accompanying shared libraries in /usr/local/lib and configuration files in /usr/local/etc.  Older programs sometimes use /opt instead of /usr/local, but almost all contemporary programs install to the latter.

If you did move /usr to a separate drive, I can't see that it would slow things down much once a program is loaded into memory.  Linux aggressively caches the disk drives, so you shouldn't notice much effect once the program and its associated libraries are loaded.  Well-behaved *nix programs don't write files to /usr either; they only write to /var, /tmp, and /home/username.  In fact, I believe it's possible to mount /usr read-only, a relic of the days when you had many users sharing a single machine with a common set of programs that the administrator needed to protect from accidental or malicious damage.

I'd **strongly** suggest you not tamper with the default file system layout until you have a lot more experience with Linux.  I've been using it for over fifteen years, and I still leave everything  where the distribution puts it.  By doing so I can insure that updates won't break.  Unlike many proprietary Windows programs, which have long periods between releases, open-source programs are constantly being patched and updated.  If you start moving things around, Ubuntu won't be able to keep your system up-to-date.  

This approach does mean that finding a program in /usr/bin can take some time; there are currently nearly 2,000 files in that directory on my system.  For the most part, though, the programs you're likely to be using will automatically show up in the menus when they're installed from the .deb package files.  Nearly all of the binaries will end up in /usr/bin.

---

