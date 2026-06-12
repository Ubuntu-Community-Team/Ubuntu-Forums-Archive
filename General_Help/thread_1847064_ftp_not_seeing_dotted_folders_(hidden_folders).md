---
title: "ftp not seeing dotted folders (hidden folders)"
date: 2011-09-20
forum: General Help
---

### Post by zainka on 2011-09-20
Hi

This is actually not related strictly to Ubuntu but I know there is many clever minds here which may explain whats going on. 

I have a ftp enabled nas server at home, sitecom md-253 and on which I have hosted my git repositories. Since I cant use ftp too clone into a repository, and since md253 is not very well prepared for ssh (changing its public key upon reboot!) I try to download the .git (bare) folder locally using ftp and thus have a local copy of the repository. Yeah, i know, not smart when it comes to version controll having two versions of the repository, but I am the only user.

However, the problem I see now is that when using yafc, or any other ftp clients, I am unable to download hidden folders. Not just .git folders but any hidden folders stored on linux nas boxes (i.e. dotted folders). So, when I try to download through ftp the .git folder to create a local copy of the repository, since I am unable to clone through ftp, I just get the message that this is not a regular file. I am not able to see it either when issuing command "ls -a" when using yafc. 

Is this a limit with yafc, with the ftp-server on my nas or with ftp protocol. How can i solve this problem???


Thanks in advance
Breg
Vidar

---

### Post by dcstar on 2011-09-20
> **zainka said:**
> Hi

This is actually not related strictly to Ubuntu but I know there is many clever minds here which may explain whats going on. 

I have a ftp enabled nas server at home, sitecom md-253 and on which I have hosted my git repositories. Since I cant use ftp too clone into a repository, and since md253 is not very well prepared for ssh (changing its public key upon reboot!) I try to download the .git (bare) folder locally using ftp and thus have a local copy of the repository. Yeah, i know, not smart when it comes to version controll having two versions of the repository, but I am the only user.

However, the problem I see now is that when using yafc, or any other ftp clients, I am unable to download hidden folders. Not just .git folders but any hidden folders stored on linux nas boxes (i.e. dotted folders). So, when I try to download through ftp the .git folder to create a local copy of the repository, since I am unable to clone through ftp, I just get the message that this is not a regular file. I am not able to see it either when issuing command "ls -a" when using yafc. 

Is this a limit with yafc, with the ftp-server on my nas or with ftp protocol. How can i solve this problem???


Thanks in advance
Breg
Vidar

You cannot download "." names to any NTFS based NAS device as these are illegal filenames, so make sure the destination device is filesystem compatible with them.

---

### Post by zainka on 2011-09-21
Its not NTFS based. The md253 is Linux driven and uses ext filesystem, and i believe Ubuntu is as-well ;) 

However, Windows, or NTFS based filesystems if you like, does NOT prohibit dotted folders, they just hide the feature so darn well. 
In fact, if you try to create a dotted folder using explorer, you will fail, but try the same in a command prompt with mkdir and you will be surprised ;O) ...

So NTFS or not has actually nothing to do with it, and especially not in my case since all systems are ext based.

---

### Post by zainka on 2011-09-28
I was just thinking. Could it be a well hidden setting in yafc which enable the visability of dotted folders?

Or is it as I fear a limitation with FTP (a bug as I would have called it) which dont allow folders and files beginning with a dot???

Thanks in advance

Vidar

---

### Post by zainka on 2012-10-18
Hi

Stumbled uppon this thread of mine again and thought I should give a uppdate.

What i found was that:

-Yafc do support dotted folders or files to some extent, but do not list  
 them. I have not found a way to make them vissible by default. But they 
 are accessible.
-To access them I need to know the exact name and to enter that manually. 
-To delete, atleast dotted folders, I need to rename it to a non-dotted 
 name before deleting or else it will fail. 

Breg
Vidar

---

