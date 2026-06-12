---
title: "need help with samba and 9.10"
date: 2010-02-22
forum: General Help
---

### Post by thompsw on 2010-02-22
i'm typing this from ubuntu 9.10 -- just realized that i don't have caps with the keyboard ... that's obviously a problem but not what i started writing about.

this is a new install of 9.10 in a fresh partition, just installed vmware 2.0, trying to upgrade from my previous setup of 7.10 and vmware 1.0.  

i have vmware running with a new xp install on that and was trying to access a share from the linux host so that i could start installing other programs ... but cannot get samba to work.  from my searching on this forum i found that i needed to install samba-common-bin, which i did.  that got me beyond the first problem but now i am getting another error message trying to setup a share with nautilus ...

Samba's testparm returned error 1: Loaded smb config files from --parameter-name=usershare allow guests
lp_load: refreshing parameters from --parameter-name=usershare allow guests
params.c:OpenConfFile() - Unable to open configuration file "--parameter-name=usershare allow guests":
	No such file or directory
Error loading services.

---

### Post by thompsw on 2010-02-23
Ideas anyone ?  Perhaps I should have posted this question in installation / upgrades ...

Dave.

---

### Post by anaconda on 2010-02-23
Hmmm..
When I installed samba to ubuntu 10.04 I needed to install these packages:
sudo apt-get install samba-common samba smbfs

I think you might still be missing the "smbfs" package?
Well.. I dont actually know what packages samba-common-bin installs, but propably not smbfs....

---

### Post by thompsw on 2010-02-23
Ah ha -- thanks for the suggestion but I did solve the problem, or at least it looks like it's shared (am about to fire up VMware) -- I did two things -- 1) I applied all the updates, something that I hadn't done since the new install of 9.10.  That then made the sharing setup "smart enough" to say that I could share folders that I didn't own -- bingo -- I then ran sudo nautilus, since root owned the folders in question, and it worked.

So -- I might have been missing some packages or whatever, but I'm now rolling again.

It will be interesting to see if VMware now clobbers the keyboard again and takes away caps ...

Dave.

---

