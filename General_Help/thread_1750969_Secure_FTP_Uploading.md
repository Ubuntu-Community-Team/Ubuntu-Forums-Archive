---
title: "Secure FTP Uploading"
date: 2011-05-06
forum: General Help
---

### Post by chome4 on 2011-05-06
Just had a website hacked while developing it on a Windows PC. Nightmare. Away from my Ubuntu machine so currently slumming it in the world of Windows!

Can someone recommend a secure FTP tool for Linux? I'm using GFTP. I'm not concerned about viruses on my Linux PC but I do move files between both operating systems on various machines.

---

### Post by Lars Noodén on 2011-05-06
Here are some clients that support [SFTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS).

Bluefish [http://bluefish.openoffice.nlhttp://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS/](http://bluefish.openoffice.nlhttp://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS/)

Cyberduck [http://cyberduck.ch/](http://cyberduck.ch/)

Dolphin

Fetch [http://fetchsoftworks.com/fetch/](http://fetchsoftworks.com/fetch/)

Filezilla [http://filezilla-project.org/](http://filezilla-project.org/)

FireFTP [http://fireftp.mozdev.org/](http://fireftp.mozdev.org/)

Fugu [http://rsug.itd.umich.edu/software/fugu/](http://rsug.itd.umich.edu/software/fugu/)

Konqueror [http://www.konqueror.org/](http://www.konqueror.org/)

lftp [http://lftp.yar.ru/](http://lftp.yar.ru/)

Nautilus

PuTTY [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Yafc [http://yafc.sourceforge.net/](http://yafc.sourceforge.net/)

---

### Post by chome4 on 2011-05-06
Thanks for that.

---

### Post by andrew.46 on 2011-05-06
> **chome4 said:**
> Can someone recommend a secure FTP tool for Linux? I'm using GFTP. 

Does your copy of gFTP not offer secure FTP? I attach a screenshot of my own copy with this enabled, I have a dim memory of this being disabled because of some licensing issues. If this is the case I can give you the necessary steps to get this going...

---

### Post by Lars Noodén on 2011-05-06
> **andrew.46 said:**
>  I attach a screenshot of my own copy with this enabled

Looks more like [FTPS](http://en.wikipedia.org/wiki/FTPS) (FTP-SSL) than [SFTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS) (Secure FTP).

---

### Post by andrew.46 on 2011-05-06
> **Lars Noodén said:**
> Looks more like [FTPS](http://en.wikipedia.org/wiki/FTPS) (FTP-SSL) than [SFTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS) (Secure FTP).

Ooops I believe I have spread confusion here, my apologies for my temporary brain lapse :(. Unless I am badly mistaken (again!) with gFTP SFTP is invoked by using the *SSH2* option, yet another screenshot attached...

---

### Post by AugustinMa on 2011-06-08
> **Lars Noodén said:**
> Looks more like [FTPS](http://en.wikipedia.org/wiki/FTPS) (FTP-SSL) than [SFTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#SFTP_is_not_FTPS) (Secure FTP).
Yes, the profusion of similarly named protocols *is* confusing. 

The various protocols are listed in a table here:
[http://linux.overshoot.tv/wiki/networking/lftp#A_multitude_of_protocols](http://linux.overshoot.tv/wiki/networking/lftp#A_multitude_of_protocols)
I created the table because I myself was very recently badly confused. Things should be clearer now.

The whole page provides useful information about using lftp for secure uploading.

I hope it helps someone.

Blessings,
Augustin.

---

