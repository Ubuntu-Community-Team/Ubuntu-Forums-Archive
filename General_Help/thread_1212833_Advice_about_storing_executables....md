---
title: "Advice about storing executables..."
date: 2009-07-14
forum: General Help
---

### Post by mouratos1a on 2009-07-14
Please forgive my ignorance...
I would like to ask the community what is the common directory to place a program downloaded ?
I mean the following:
Let's say I download a program in a .tar form, where should I store it and where should I extract it in order to run the installer?
Will the installer always install in the directory where it (the installer) was located?
I know there is no program files like windows in linux and some progs are installed in certain dirs regardless the installer's dir...
Could someone of the gurus clarify a little this mess?
Thank you for the time spent on my thread...
Mouratos

---

### Post by mcduck on 2009-07-14
If you are installing the program just for yourself you can keep it in your home directory. For system-wide installs I'd recommend putting the program in /opt, which is intended for programs that don't belong to the distribution and that are installed from third-party packages etc.

What comes to archived programs you download and how to install them, there really is no standard as the archive is just and archive, it can contain anything. You really just have to read the instructions included in the archive. If it's a ready-to-run program binary extract it where you want to put the program. If it's a binary installer or source code it makes no difference where you extract the archive, at this point you aren't installing anything just extracting the install files themselves.

Of course it should be mentioned that downloading programs manually isn't exactly a common way to install software in the first place.. ;)

---

### Post by mouratos1a on 2009-07-14
> **mcduck said:**
> If you are installing the program just for yourself you can keep it in your home directory. For system-wide installs I'd recommend putting the program in /opt, which is intended for programs that don't belong to the distribution and that are installed from third-party packages etc.

What comes to archived programs you download and how to install them, there really is no standard as the archive is just and archive, it can contain anything. You really just have to read the instructions included in the archive. If it's a ready-to-run program binary extract it where you want to put the program. If it's a binary installer or source code it makes no difference where you extract the archive, at this point you aren't installing anything just extracting the install files themselves.

Of course it should be mentioned that downloading programs manually isn't exactly a common way to install software in the first place.. ;)

Thank you very much for the swift response...
It clarifies many issues...
I was bumped by your last comment...
Which is the common way to install software?
To be more specific...I am interesting on finding a program that categorizes CDs DVDs etc. similar to WhereIsIt well known from Windows...I found here ([http://ubuntuforums.org/showthread.php?t=877756&highlight=whereisit](http://ubuntuforums.org/showthread.php?t=877756&highlight=whereisit)) a precise thread that gives many options. How should I install one of them? 
Is there a way other than downloading the linked programs?
Thank you for your time...
Mouratos

---

### Post by 3rdalbum on 2009-07-14
> **mouratos1a said:**
> Please forgive my ignorance...
I would like to ask the community what is the common directory to place a program downloaded ?
I mean the following:
Let's say I download a program in a .tar form, where should I store it and where should I extract it in order to run the installer?

Anywhere you want. It doesn't matter where the installer is, because it will always install to the correct place. Same as on Windows.

> Will the installer always install in the directory where it (the installer) was located?

It will install into the correct directories for system-wide use (i.e any user account on your computer can run it)

> Could someone of the gurus clarify a little this mess?

It's not a mess, and it's not so much a case of "Why isn't this like Windows" as "Why didn't Windows do things the same as us" (Unix was around for decades before Windows).

Programs (just the programs themselves) get stored in /usr/bin/. Their data gets stored in /usr/share/. Manual pages are stored in /usr/share/man/. Icons can be stored in one of a number of places - it doesn't really matter where, because the ".desktop" file (which gets stored in /usr/share/applications/) will know where the icon is.

The Linux system knows that executables are stored in /usr/bin/ - that's why you can just type the name and it will run, rather than have to type the full file path. The system that creates a database of manual pages is more efficient when all manual pages are stored in one particular place - it doesn't have to go searching around the filesystem just to find one page. Your .desktop files are stored in one particular place where the main menu generator can find them very quickly (same as on Windows, when you think about it).

Occasionally a program will go into /opt - this is a bit of an oddity and usually demonstrates that the program developer isn't really familiar with Linux. If the program goes anywhere else, then they *really* don't know what they are doing. Even programs found in /opt will still be accessible from the command-line.

But this begs the question: Why do you need to know where the programs store their files? You can always type their name in a terminal to run them; you don't need to worry about a file path. Why would you ever need to fiddle around with the actual file locations for all the internal bits? You certainly don't need to delete specific files from locations - the package manager can deal with that on its own when you remove a package.

---

### Post by mouratos1a on 2009-07-14
> **3rdalbum said:**
> Anywhere you want. It doesn't matter where the installer is, because it will always install to the correct place. Same as on Windows.



It will install into the correct directories for system-wide use (i.e any user account on your computer can run it)



It's not a mess, and it's not so much a case of "Why isn't this like Windows" as "Why didn't Windows do things the same as us" (Unix was around for decades before Windows).

Programs (just the programs themselves) get stored in /usr/bin/. Their data gets stored in /usr/share/. Manual pages are stored in /usr/share/man/. Icons can be stored in one of a number of places - it doesn't really matter where, because the ".desktop" file (which gets stored in /usr/share/applications/) will know where the icon is.

The Linux system knows that executables are stored in /usr/bin/ - that's why you can just type the name and it will run, rather than have to type the full file path. The system that creates a database of manual pages is more efficient when all manual pages are stored in one particular place - it doesn't have to go searching around the filesystem just to find one page. Your .desktop files are stored in one particular place where the main menu generator can find them very quickly (same as on Windows, when you think about it).

Occasionally a program will go into /opt - this is a bit of an oddity and usually demonstrates that the program developer isn't really familiar with Linux. If the program goes anywhere else, then they *really* don't know what they are doing. Even programs found in /opt will still be accessible from the command-line.

But this begs the question: Why do you need to know where the programs store their files? You can always type their name in a terminal to run them; you don't need to worry about a file path. Why would you ever need to fiddle around with the actual file locations for all the internal bits? You certainly don't need to delete specific files from locations - the package manager can deal with that on its own when you remove a package.

Thank you very much for the detailed answer to my post...
The reason I am asking has a name on it...
It's called CDnavigator ...
I downloaded the tar file , extracted it in desktop then from command line wrote "sh install.sh" it did install in the same directory the installer was located...
Now I cannot run the program   and don't know how to get rid of it ...
That is why I am asking all these details...

---

### Post by mcduck on 2009-07-14
> **mouratos1a said:**
> Thank you very much for the swift response...
It clarifies many issues...
I was bumped by your last comment...
Which is the common way to install software?
To be more specific...I am interesting on finding a program that categorizes CDs DVDs etc. similar to WhereIsIt well known from Windows...I found here ([http://ubuntuforums.org/showthread.php?t=877756&highlight=whereisit](http://ubuntuforums.org/showthread.php?t=877756&highlight=whereisit)) a precise thread that gives many options. How should I install one of them? 
Is there a way other than downloading the linked programs?
Thank you for your time...
Mouratos

In Linux programs are usually installed with the package management, which will list, download and install all programs available on Ubuntu's servers, and also handles automatic updating of your software. Not just the OS itself like in Windows but every program.

In Ubuntu, take a look at the Add/Remove-tool in Applications menu (it provides easy way to install some of the most commonly used graphical applications), and for a full-featured package manager go for System/Administration/Synaptic Package Manager. 

And be sure to read this: [http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

