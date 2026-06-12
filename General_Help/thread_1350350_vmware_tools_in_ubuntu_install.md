---
title: "vmware tools in ubuntu install"
date: 2009-12-09
forum: General Help
---

### Post by heatopher on 2009-12-09
Hi, not sure where to put this post, so here it is in "General", though I fear that this might be a bit peculiar. Well, I am hoping the solution can be simple. 

I've just recently installed Ubuntu on vmware (the base being XP on a netbook). Obviously I want to be able to move files around on the netbook between the two systems, and so I tried last night setting up the sharing via VM>Settings>Options>Shared Folders (had previously been trying to set up Samba, which I guess was way over the top). Supposedly that was OK, but then when I looked in /mnt/hgfs there was nothing there. I searched a bit on the net, and it seemed from what I could gather that maybe I needed to reinstall the VM tools. So I tried to do that, and then got stuck. I can go over the history in more detail if needed (please say it's not necessary!), but for now let me show you the useless loop that I'm currently stuck in. It looks like the uninstall file got uninstalled, but not everything else did, and that's why I'm not getting anywhere. Does that seem like a logical surmise? The /mnt/hgfs folder which I initially had last night is now no longer around. I assume that means that that is something which is installed by the vmware tools???  All help appreciated :~}  

Anyway, here's what I'm getting when I try to install from the command line, following the instructions found in the vmware help: 

root@ubuntu:~# ./vmware-tools-distrib/[vmware-install.pl]("http://vmware-install.pl/") 
A previous installation of VMware Tools has been detected.

The previous installation was made by the tar installer (version 4).

Keeping the tar4 installer database format.

You have a version of VMware Tools installed.  Continuing this install will 
first uninstall the currently installed version.  Do you wish to continue? 
(yes/no) [yes] yes

Error: Unable to execute "/usr/bin/[vmware-uninstall-tools.pl]("http://vmware-uninstall-tools.pl/").

Uninstall failed.  Please correct the failure and re run the install.

Execution aborted.

Found VMware Tools CDROM mounted at /media/cdrom1. Ejecting device /dev/sr0 ...

root@ubuntu:~#

---

### Post by heatopher on 2009-12-09
Shameless bump :~\

Just doing this because I initially had JavaScript turned off, and so the formatting of my message was messed up, which might have put people off replying. If this is the wrong place for this question, please tell me where to go. I'm getting very frustrated. Thanks...

---

