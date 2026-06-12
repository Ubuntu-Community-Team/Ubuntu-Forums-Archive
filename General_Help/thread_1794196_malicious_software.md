---
title: "malicious software"
date: 2011-06-30
forum: General Help
---

### Post by Helveticus on 2011-06-30
Hello

I have Ubuntu running in a vm with Windows 7 as host. Now if I downlod per filesharing a programme for Ubuntu, will the probability for getting a virus oder so indead 0? I have read that there are no viruses and so for Ubuntu.

---

### Post by smurphy_it on 2011-06-30
Typically nothing to worry about.  A virus would have to be coded specifically for linux, and most likely exploit a known bug.  Not to mention, the user's are standard for the most part.

If you are worried about it, you can always install the application and then use app-armor to lock it down.  (that or install the application in a change root jail).

---

### Post by oldos2er on 2011-06-30
> **Helveticus said:**
> Hello

I have Ubuntu running in a vm with Windows 7 as host. Now if I downlod per filesharing a programme for Ubuntu, will the probability for getting a virus oder so indead 0?

What?

Only download programs from the repositories, and there should be no problems.

---

### Post by 1clue on 2011-06-30
There is never 'nothing to worry about.'

If your Ubuntu installation is a VM on a Windows system, then any of the files which define the Ubuntu system (hard disk files, configuration files etc) can be corrupted, as can the VMware binary itself.

If your Ubuntu and Windows have a shared folder, then the files which are in that folder can be corrupted.

If your Ubuntu shares via samba, ftp or ssh with the Windows system, then there is a chance of corruption that way.

The big question is, what are the ramifications?  Not so clear.

The first scenario, it's just like any other Windows corruption.

The second, third and fourth scenarios, if Ubuntu accesses a file which has a Windows virus on it then chances are nothing happens.  If it's a Word document and you run anything from Ubuntu which understands the Word plugins or script languages, then it's possible the virus behaves the same as it would on Windows, only affecting your Linux system.  If you're running Ubuntu properly then only your personal files would be affected, not the whole disk.

If the virus is scripted in some language which is understood on both Windows and Linux, then there is a significant chance that something would happen.  The good news is that often deliberate care needs to be made to be cross platform.  The bad news is that there are more cross-platform situations every year.

---

### Post by tgalati4 on 2011-06-30
Presumably, running in a virtual machine puts the guest operating system (in this case ubuntu) in a "sandbox".  Anything that happens or can happen stays inside that sandbox.  This is also known as running your guest OS in a "jail", such that anything malicious would stay in its "jail".

However downloading files from unknown websites such as music or videos that could be run in the Windows environment could lead to vulnerabilities on the Windows side since the file is now opened in the Windows environment and is no longer in "jail".

A better situation is to run Ubuntu on it's own machine.  Keep the Windows machine intact.  The less you use it, the less problems you will have.  To share files on Ubuntu, just right-click the folder and set sharing on.  Then you can share whatever files on Ubuntu with other machines on your network.  Your Windows virus scanner would presumably check any files pulled over from the share.

In a way, use Ubuntu as your "firewall" and keep your Windows machines clean by not using them to browse the web.  But don't get a false sense of security by using Ubuntu in a VM to downloading files from an unknown website.

---

### Post by 1clue on 2011-06-30
Theoretically what you say is right.  The problem is though if the host system gets infected then the VM is just a bunch of files in the host system, which can be corrupted just like any other file.

Another problem is that almost every virtualization environment implements some sort of file sharing or even application sharing "feature" to "help" you get work done.  I run a mac at work with Parallels.  The Windows VM somehow got mime mapped on the mac and vice versa, so I can be in Mac OS and double click on a file, and it launches Parallels to view a PDF.  For the record, a PDF looks a thousand times better on a Mac than on Windows.  Likewise, I can be in Windows and double click on something and it opens on the Mac.  Infuriating.

My point here is that when you have so many "helpful features" the chances for malware to actually work skyrockets.  If you're on Linux and open a Word document, there is a possibility that it will open in Windows with some sort of access to your Linux files, which means the malware works and operates inside your Linux partition.

---

