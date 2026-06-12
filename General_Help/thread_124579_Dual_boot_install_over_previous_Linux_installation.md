---
title: "Dual boot install over previous Linux installation"
date: 2006-02-01
forum: General Help
---

### Post by JeffV on 2006-02-01
I want to install ubuntu and try it out, but I want to make sure I don't do something wrong because of my current setup.  Right now I have Fedora Core 4 installed and am dual booting with Win XP.  Grub was successfully installed so it gives me the option to choose between them.  The two OS's are installed on two physically different disks.  

Now, I'd like to remove Fedora and switch to ubuntu.  Should it install ok as long as I just tell it to use the partition that I used for Fedora?  Will the boot loader be able to figure out that Fedora is gone and Ubuntu is there in it's place?  Or will an entirely new boot loader be installed?  Is there anything special I have to do to achieve this?

---

### Post by o_fortuna on 2006-02-01
[QUOTE=JeffV]I want to install ubuntu and try it out, but I want to make sure I don't do something wrong because of my current setup.  Right now I have Fedora Core 4 installed and am dual booting with Win XP.  Grub was successfully installed so it gives me the option to choose between them.  The two OS's are installed on two physically different disks.  

Now, I'd like to remove Fedora and switch to ubuntu.  Should it install ok as long as I just tell it to use the partition that I used for Fedora?  Will the boot loader be able to figure out that Fedora is gone and Ubuntu is there in it's place?  Or will an entirely new boot loader be installed?  Is there anything special I have to do to achieve this?[/QUOTE]
You should be just fine. I've installed Ubuntu over other linux distros (Linspire) and it worked just fine; Ubuntu will install Grub and configure it properly. Just make sure you pick the right partition. You have no idea how much sleep I lost when I thought I had erased my old Ubuntu (I was afraid to turn the computer off and find out :D).

---

### Post by JeffV on 2006-02-01
OK, great!  I think I'll play around with the Live CD a little bit first, but I'm pretty sure I'll end up installing it on my machine.  Thanks!

---

