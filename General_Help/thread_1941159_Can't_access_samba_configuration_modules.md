---
title: "Can't access samba configuration modules"
date: 2012-03-15
forum: General Help
---

### Post by horseatingweeds on 2012-03-15
This is a new install of kubuntu 11.10. I've installed samba on Ubuntu before, so I tried installing it on this Kubuntu installation the same way. I installed samba, smbfs, and system-config-samba. I then tried running system-config-samba, but it complained that there was no active X server, so I figured I had installed the wrong thing for Kubuntu.

So I read this tutorial: [http://maketecheasier.com/easy-samba-sharing-setup-with-kde/2010/11/17](http://maketecheasier.com/easy-samba-sharing-setup-with-kde/2010/11/17)  Which says to install samba and kdenetwork-file-sharing. So I installed kdenetwork-file-sharing. But now when I try to run things like fileshare "*kdesudo kcmshell4 fileshare" *it says "Could not find 'fileshare'". Likewise with sambaconf.

I read this bug report, but I'm not sure what to make of it. [https://bugs.launchpad.net/ubuntu/+source/kde-baseapps/+bug/851668](https://bugs.launchpad.net/ubuntu/+source/kde-baseapps/+bug/851668)

When I use Dolphin and right-click->Properties->Share, I don't see what the tutorial shows. I just have a check box "Share with Samba" with a text box that contains the name of the file. 

Currently, I can reach windows shared from this Kubuntu, but when I try to access the Kubuntu machine from Windows Explorer on Windows machine, it regects my password. (Which I guess it should because I haven't configured anything linux shares or passwords yet.)

Also, I installed swat, but it only shows Home Status View and Password buttons. I'm not sure what to do with it. I'm reading about how to configure smb.conf directly. 

Any advice on getting to the graphic configuration modules?

Thanks.

---

