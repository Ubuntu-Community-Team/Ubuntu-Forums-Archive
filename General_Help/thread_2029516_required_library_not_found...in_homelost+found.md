---
title: "required library not found...in /home/lost+found"
date: 2012-07-19
forum: General Help
---

### Post by smcrossman on 2012-07-19
I recently did 2 clean installs of 12.04 amd64 with NVidia;

2nd time around I can actually install packages before everything was giving me headaches about dependencies and conflicts.

Anyway, I decided it was time to move beyond basic Samba for my home network to try to get full access to my NAS.  I knew one step of that process was to add NFS.  Which seems to require NIS, or at least binding and something to get the portmapper going.  Anyway....so far so good But I am hitting a wall on the compiling of the libraries because I have a couple of files not found.

1 was the /lib/x86_64-linux-gnu/libc.so.6; I came across somethin online telling how to locate the file (ITS everywhere!) but I think the easiest one to reclaim and somehow link to ypbind (however I do that!) would be the one sitting in my /home/lost+found file.  What is the best process for this?

and what is the purpose of this file again? how do things end up there?

Thanks for any & all help!

---

### Post by steeldriver on 2012-07-19
lost+found directories are used by the system when repairing broken filesystems - you shouldn't have any need to go in there except in a recovery situation - all the libraries and headers should be in standard system directories such as /lib, /usr/lib, /usr/include and so on

I'm kind of confused here about why you are needing to compile anything - AFAIK the only additional thing you should need to set up a nfs client is the nfs-common package which is available in repositories (no need to compile anything)

---

### Post by smcrossman on 2012-07-20
Likely I'm working off old documentation. But I guess it also matters that I'm setting up a server not just a client.

The documentation I'm using is [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

For NIS I started with:
[https://help.ubuntu.com/community/SettingUpNISHowTo]("https://help.ubuntu.com/community/SettingUpNISHowTo")
but that wasn't so great so I moved on to:
[http://tldp.org/HOWTO/NIS-HOWTO/ypserv.html]("http://tldp.org/HOWTO/NIS-HOWTO/ypserv.html")
[http://tldp.org/HOWTO/NIS-HOWTO/setting_nis.html]("http://tldp.org/HOWTO/NIS-HOWTO/setting_nis.html")

Basically when I started with NFS some of the files just weren't there. Then I couldn't get any response from the portmapper. So I decided to install NIS as an option.  So technically it isn't NFS dependency exactly but NIS.

And yes the lib is in the system but its saying its > could not read symbols: Bad value
collect2: ld returned 1 exit status


So my immediate leap was that it was the lib since everything else is saying no missing deps; but now I'm suspecting I'm missing another step of setting something else up.

I thought I was ready for a challenge! LOL

So honestly, can I get NFS Server up & running without NIS?  Maybe I've processed through enough of the missing pieces that the basic server install will work now. I know I finally got my portmapper responding last night, and I've reformatted my shares to proper form finally. I'll try to restart both later and see if it works. I forget to try to keep things simple...if the documentation leads me down an overly involved path I get caught!

Thanks for the wakeup! I'll be back if things don't work or if I do need to figure out the NIS install.

---

### Post by smcrossman on 2012-08-11
I still don't have nis installed. I gave up for a while since more pressing life issues came up. I am still sparadically having issues with existing files & libraries not being available for updates, upgrades and installs. I'm going to close this out since I'm thinking I'm going to have to look more at my config and setup before asking for help with that issue.  The nis issue will come back around after that.

Thanks for the input and suggestions!

---

