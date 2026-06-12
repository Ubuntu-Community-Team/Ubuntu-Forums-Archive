---
title: "[HELP] I can't install Ubuntu"
date: 2010-08-22
forum: General Help
---

### Post by El Sol on 2010-08-22
Hey Guys,

I can't install Ubuntu into my HP Mini 1001Tu. When I tried to install using Live-USB, I stuck on step 3(Keyboard Layout) of the installation phases... 

It's not a hang, as I can exit/quit the installation easily...

I googled ways to fix this problem, but I can't seem to find the cure for this...

Please help..T_T

---

### Post by davidmohammed on 2010-08-22
in these cases I would recommend you download the alternate CD and try that.  It works better on some problematic hardware setups.

---

### Post by J V on 2010-08-22
Did you check the md5sum of the disc before you put it onto the usb stick? It could be there was a download error...

---

### Post by finkey on 2010-08-22
Did you format the target drive with Ext3 filesystem before installation?  Otherwise it won't go.

---

### Post by El Sol on 2010-08-22
> **J V said:**
> Did you check the md5sum of the disc before you put it onto the usb stick? It could be there was a download error...

may I know how to check??

---

### Post by El Sol on 2010-08-22
> **finkey said:**
> Did you format the target drive with Ext3 filesystem before installation?  Otherwise it won't go.

I will try this and keep you updated...:D

thanks!

---

### Post by El Sol on 2010-08-22
> **finkey said:**
> Did you format the target drive with Ext3 filesystem before installation?  Otherwise it won't go.

It doesn't work...the problem still persists...:(

---

### Post by El Sol on 2010-08-22
> **davidmohammed said:**
> in these cases I would recommend you download the alternate CD and try that.  It works better on some problematic hardware setups.

alternate CD??..do u mean burn it into a CD?? hahaha..my HP Mini doesn't have any CD-Rom...

---

### Post by techunit on 2010-08-22
If you have access to a windows computer you can follow this guide I put together about creating a Ubuntu Live USB. perhaps you followed a different process and there was some unforeseen error.
[URL="http://ubuntuvideotutorials.org/category/utilities-2/bootable-flashdrive/"]
Here are the guides[/URL]

---

### Post by El Sol on 2010-08-22
> **techunit said:**
> If you have access to a windows computer you can follow this guide I put together about creating a Ubuntu Live USB. perhaps you followed a different process and there was some unforeseen error.
[URL="http://ubuntuvideotutorials.org/category/utilities-2/bootable-flashdrive/"]
Here are the guides[/URL]

Thanks for the video guide, but I'm using Live USB rite now...hahaha ;)

---

### Post by El Sol on 2010-08-22
YAY! Somehow it worked dy...

MIGHT be because of formatting the target drive with Ext3 filesystem, just now I didn't restart..hahhaa

---

### Post by finkey on 2010-08-22
Good job, El Sol.  Ext3 format of target drive worked for me.  I used Acronis Disk Director for the job.

---

### Post by El Sol on 2010-08-22
> **finkey said:**
> Good job, El Sol.  Ext3 format of target drive worked for me.  I used Acronis Disk Director for the job.

Thanks! :D

---

### Post by chips24 on 2010-08-22
just as a side not, you should never use ext4 to install ubuntu. It will be unable to read any disk drives other than its own.

---

### Post by El Sol on 2010-08-22
> **chips24 said:**
> just as a side not, you should never use ext4 to install ubuntu. It will be unable to read any disk drives other than its own.

Can I change my current ext3 to ext4 ??

and sorry, this might be out of topic, but I don't like Firefox, can I uninstall it?..I read somewhere in the net, that if I uninstall Firefox I will uninstall the whole desktop?..is that true?

thanks! ;)

---

### Post by finkey on 2010-08-22
To change Ext3 to Ext4, you'd have to format the target drive as Ext4, and reinstall your programs.  It's a lot of work, but if you want to do it, you can.  Thanks also to Chips 24, I learned from your post.  I am guessing Ext4 is meant to completely isolate Ubuntu from other operating systems.

I don't think it's true that uninstalling Firefox will uninstall the desktop too.  Firefox is stand alone.  I'd use Synaptic Package Manager, do a Quick Search for Firefox, right click the shaded box, and choose **mark for remova**l, or **complete removal**.  I'm going to try take out Firefox right now, and post back to see if this flushed my desktop.  I don't think so...

===== 5 minutes later ======

Okay, took Firefox out, restarted computer, put it back.  No problem with the desktop at all.  El Sol, if you are satisfied with this thread, mark as [SOLVED].

---

### Post by El Sol on 2010-08-23
> **finkey said:**
> To change Ext3 to Ext4, you'd have to format the target drive as Ext4, and reinstall your programs.  It's a lot of work, but if you want to do it, you can.  Thanks also to Chips 24, I learned from your post.  I am guessing Ext4 is meant to completely isolate Ubuntu from other operating systems.

I don't think it's true that uninstalling Firefox will uninstall the desktop too.  Firefox is stand alone.  I'd use Synaptic Package Manager, do a Quick Search for Firefox, right click the shaded box, and choose **mark for remova**l, or **complete removal**.  I'm going to try take out Firefox right now, and post back to see if this flushed my desktop.  I don't think so...

===== 5 minutes later ======

Okay, took Firefox out, restarted computer, put it back.  No problem with the desktop at all.  El Sol, if you are satisfied with this thread, mark as [SOLVED].

Thanks!! How to mark this thread as [SOLVED]?? I tried to edit my first post..but there's no option to change it to [SOLVED] :D

---

### Post by finkey on 2010-08-23
El Sol, I'm sorry, my mistake, I thought it could be done by editing the first post in the thread, but there's no subject line to change. Glad it all worked out for you.  Off topic, you may have heard about a great light weight program that installs .deb files with all dependencies, called **gdebi-gtk**.  .deb files are usually drivers or programs provided by third parties.  Synaptic Package Manager may or may not find them.  For example,  I got Skype using a .deb file.  So just run **gdebi-gtk** command from a terminal or from the Run Application program.  It's very user friendly and installs downloaded .deb files with all dependencies.

---

### Post by sydbat on 2010-08-23
> **chips24 said:**
> just as a side not, you should never use ext4 to install ubuntu. It will be unable to read any disk drives other than its own.Source? I have never had a problem, and I cannot find anything about this via Google.

---

### Post by El Sol on 2010-08-24
> **finkey said:**
> El Sol, I'm sorry, my mistake, I thought it could be done by editing the first post in the thread, but there's no subject line to change. Glad it all worked out for you.  Off topic, you may have heard about a great light weight program that installs .deb files with all dependencies, called **gdebi-gtk**.  .deb files are usually drivers or programs provided by third parties.  Synaptic Package Manager may or may not find them.  For example,  I got Skype using a .deb file.  So just run **gdebi-gtk** command from a terminal or from the Run Application program.  It's very user friendly and installs downloaded .deb files with all dependencies.
No problem..hahaha ;)

I'm totally new to Linux haha so I don't understand what you mean by .deb files...haha googled it, still can't understand..

gonna take some time for me to understand I think..haha

but thanks anyway!..

@Abahsis

sama2..:D

---

### Post by finkey on 2010-08-24
I'm new to it too.  But I gather (someone please correct me if I'm wrong) .deb files are installation files, for example, device drivers, that are written for Linux by a device manufacturer.  The driver may not necessarily be available through the repositories (Linux program banks) accessed by Synaptic Package Manager (the Linux program installer). With Windows, we don't worry about dependencies (other files necessary to make a program work).  But Linux needs them, because they vary from one type of Linux to another.  Gdebi-gtk knows which dependencies to fetch for Ubuntu, and installs them alongside the .deb file.

---

### Post by sydbat on 2010-08-25
> **finkey said:**
> I'm new to it too.  But I gather (someone please correct me if I'm wrong) .deb files are installation files, for example, device drivers, that are written for Linux by a device manufacturer.  The driver may not necessarily be available through the repositories (Linux program banks) accessed by Synaptic Package Manager (the Linux program installer).Yes, .deb are install files for everything on a Debian-based distro (like Ubuntu). Most things are found via the repositories, but there are a few things that you might need to download and finding the .deb makes it much easier to install. Also, looking through trusted places like this forum for links to PPA's (developers "repos") can help avoid stumbling upon a questionable download source that could be laced with malware.
> With Windows, we don't worry about dependencies (other files necessary to make a program work).Windows also uses dependencies, they just use a different name/type - DLL. And when installing a Windows program onto a Windows machine, all the dependencies are part of whatever program. Windows does not use shared library resources like Linux does. Windows programs tend to install all the DLL's into the specific program folder, and not look elsewhere for the same DLL's (which explains the "bloat" term that people bandy about). Whereas Linux applications are (usually) designed to look for the shared library and, if it does not find the necessary files, will insist that those dependencies are met. A Package Manager like Synaptic will look for and install those dependencies into the shared library folders, so other applications can then access them.
> But Linux needs them, because they vary from one type of Linux to another.You are partially correct about different distributions - for example, if I install Fedora as a dual boot, Fedora will not look at my Ubuntu / partition for shared files. However, if there are shared files in my /home partition (set as a shared /home between distros) that can be used by some application I install in Fedora, that application will use them. There are some Distribution specific dependencies, but far more are universal ones.
> Gdebi-gtk knows which dependencies to fetch for Ubuntu, and installs them alongside the .deb file.As I mentioned above, the resources are shared.

---

### Post by finkey on 2010-08-25
Thanks SydBat for this explanation - I wonder why Microsoft hasn't programmed for shared .dll files as well, the Linux way seems far more efficient.

---

### Post by sydbat on 2010-08-25
> **finkey said:**
> Thanks SydBat for this explanation - I wonder why Microsoft hasn't programmed for shared .dll files as well, the Linux way seems far more efficient.Not really Microsoft's fault. More the program developers. Some do not want to share their sources (hence proprietary), or more often, rely on needed DLL's to be present that are not. AFAIK, Windows does not automatically search for required library files like Linux, due to the lack of a package manager (this might be different with Windows 7, but I have not used Windows at all for almost 4 years).

---

### Post by El Sol on 2010-08-25
Thanks guys for the replies...:D

I've marked this thread as [SOLVE], it's from the "thread tools" right above my first post..:D

:D 

Many Thanks to all of you guys, especially Finkey..:D

---

