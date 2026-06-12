---
title: "Accessing a share on Ubuntu from W7 machine"
date: 2011-08-06
forum: General Help
---

### Post by Bonesnap on 2011-08-06
Hello all! :)

I was running a Ubuntu 10.04 installation as a media server for just over a year and everything was setup and functioning properly. My OS drive had bad sectors so I took the opportunity to install Ubuntu 11.04 (and replace the drive, of course). I've got everything up and running except one thing.

11.04 seems to be a lot more strict when it comes to file sharing. Either that or I forget how I setup my 10.04 installation. I'm trying to enable my volume for file sharing, but I am running into problems.

I have Samba installed, and I selected the proper volume to share, gave it full read/write permissions and set the visibility to "visible". The workgroup is the same between my W7 machine and Ubuntu 11.04. For whatever reason though I am unable to map the drive in Windows.

However...

I can manage to get the volume to map if I open the volume (in Ubuntu) and right-click and select "Properties" and then select the "Sharing" tab. I enable "Share this folder", give it a share name and check "Allow others to create...". If I do that, I can map the volume and all seems well. HOWEVER... this only allows me to write to the root directory of my share, and not to sub folders. This is of course a problem.

If I uncheck "Share this folder" then the drive cannot be mapped and there is no access to it. It's as if Samba doesn't even matter. I've double-checked my Samba settings and I'm at my wits' ends here. I don't remember having this trouble at all with 10.04. Is there something completely different with 11.04 and file sharing, or am I just forgetting a step?

Also, no network settings were changed at all between installations.

Any help would be greatly appreciated. Thank you for reading! :)

---

### Post by Bonesnap on 2011-08-06
Anyone?

I've tried a few other things and nothing seems to be working. It's as if Samba doesn't even exist on my Ubuntu machine. The only way I can get my volume to map and have (limited) rights is to manually go to the volume and enable file sharing.

---

