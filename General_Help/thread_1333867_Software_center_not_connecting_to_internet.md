---
title: "Software center not connecting to internet"
date: 2009-11-21
forum: General Help
---

### Post by deepla on 2009-11-21
Hi I recently installed Ubuntu 9.1 from flash drive. (Acer laptop 1641nNWLMi, 512 MB,Intel graphics media accelerator 900, Pentium M 725 ). 

The problem that i have now is that the software centre or synaptic package manager does not connect to internet.

 Firefox was not connecting initially but after searching a bit i was able to find that i need to disable ipv6 in firefox. After this the wireless and the wired connections are working well for firefox but other applications does not connect to net. So I am not able to install any other program.

 When i installed ubuntu from the flash drive a warning came saying ' failed to load additional packages of apt config ' ( or something like that ).

 The error i get now when i press the reload button in synaptic package manager is

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...ic/Release.gpg](http://je.archive.ubuntu.com/ubuntu/...ic/Release.gpg) Could not connect to je.archive.ubuntu.com:80 (1.0.0.0), connection timed out

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...es/Release.gpg](http://je.archive.ubuntu.com/ubuntu/...es/Release.gpg) Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2](http://je.archive.ubuntu.com/ubuntu/...tion-en_US.bz2) Unable to connect to je.archive.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg](http://security.ubuntu.com/ubuntu/di...ty/Release.gpg) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2) Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2) Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2) Unable to connect to security.ubuntu.com http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2](http://security.ubuntu.com/ubuntu/di...tion-en_US.bz2) Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

Can you please help ?

---

### Post by Uncle Spellbinder on 2009-11-21
[http://ubuntuforums.org/showthread.php?t=1333810](http://ubuntuforums.org/showthread.php?t=1333810)

---

### Post by deepla on 2009-11-22
Uncle spellbinder, Nice to hear your problem is solved. But i get the same error

---

### Post by MelDJ on 2009-11-22
change your software sever?

---

### Post by deepla on 2009-11-29
Thanks for the reply. Sorry i could not reply earlier. I did change my server but no use. The update manager did update once but it is not reloading any more. The curious thing i found is that i am able to download the individual packages without any problem through firefox if i use the address given by the software centre. 

eg:W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/appconfig/libappconfig-perl_1.56-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/appconfig/libappconfig-perl_1.56-2_all.deb)

is a warning i get . but i am able to download the package through firefox

I even installed skype this way and is working. This is very tedious and what could be the reason . I think the server is not having any problem and the net connection is also ok, but something is stopping the synaptic package manager and software centre. Can you please give some clue ?

---

### Post by deepla on 2009-12-30
Hi. Thanks for all who tried to help. I found the solution here.
[http://www.linuxforums.org/forum/ubuntu-help/157482-solved-cannot-update-install-programs-through-synaptic.html](http://www.linuxforums.org/forum/ubuntu-help/157482-solved-cannot-update-install-programs-through-synaptic.html)

---

