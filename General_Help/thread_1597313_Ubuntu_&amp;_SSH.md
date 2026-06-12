---
title: "Ubuntu &amp; SSH"
date: 2010-10-15
forum: General Help
---

### Post by sarahfoxnz on 2010-10-15
Hello.

I've got the latest Ubuntu, & a working SSH. (new to both)

we have a local server / router, & from my Windows Pc - I can use Windows explorer to "see" the directory structure of the Ubuntu machine..

I've got full access to / (top) directory - while in SSH..

I'm wondering. - I need to add / install files outside of my /home/Username  folder, & seem to need to use "sudo" on anything i do.. - create directory.. / copy files etc.. 

is there a way I can create directories / edit files etc in my 'Windows exporer'.. 

Or is there a similar programme I can use - on both WinXP & Ubuntu?

Basically, i want to be able to copy entire directories, or Create / rename directories/files in a "visual' context..

Click / Rename / End - easy..

in SSH / Ubuntu - i seem to need to remember the FULL path name each time..  - & do everything via command-line.

---

### Post by luvshines on 2010-10-15
> **sarahfoxnz said:**
> Hello.

I've got the latest Ubuntu, & a working SSH. (new to both)

we have a local server / router, & from my Windows Pc - I can use Windows explorer to "see" the directory structure of the Ubuntu machine..

I've got full access to / (top) directory - while in SSH..

I'm wondering. - I need to add / install files outside of my /home/Username  folder, & seem to need to use "sudo" on anything i do.. - create directory.. / copy files etc.. 

is there a way I can create directories / edit files etc in my 'Windows exporer'.. 

Or is there a similar programme I can use - on both WinXP & Ubuntu?

Basically, i want to be able to copy entire directories, or Create / rename directories/files in a "visual' context..

Click / Rename / End - easy..

in SSH / Ubuntu - i seem to need to remember the FULL path name each time..  - & do everything via command-line.

How are you accessing Ubuntu machine at present ??
Are you using putty to connect with SSH or using WinSCP ??

---

### Post by sarahfoxnz on 2010-10-15
Ps..

is there a way I can "copy" a file via SSH ? 

Small files / minor editing, I can easily do sudo nano  & create/edit the file on the Ubuntu machine..

but what if I've got a larger text / (non-text) file ? 

Can I just 'copy' my Windows files over to Ubuntu - over SSH ?


Goodnight, I'll try again tomorow... - Googles

---

### Post by yankysunny on 2010-10-15
U can use sftp service but for that you have to run that service on your ubuntu.
Then use
sftp://username@ipaddress

---

### Post by luvshines on 2010-10-15
> **sarahfoxnz said:**
> Ps..

is there a way I can "copy" a file via SSH ? 

Small files / minor editing, I can easily do sudo nano  & create/edit the file on the Ubuntu machine..

but what if I've got a larger text / (non-text) file ? 

Can I just 'copy' my Windows files over to Ubuntu - over SSH ?


Goodnight, I'll try again tomorow... - Googles

Yeah you can using SCP protocol. Use WinSCP to connect to your Linux machine from Windows and copy/move the files from here to there. But this will work only if you are working from Windows machine. I think it allows editing them too but copies them first to some temporary location in windows and then uploads them. I don't think you should modify scripts like this since windows may enter some unknown characters to the end of line which are not known to Ubuntu and script fails to run

If you are on Ubuntu and want to transfer something over to Windows, you can access the Windows shared drives from nautilus and copy/edit/move files

---

### Post by sarahfoxnz on 2010-10-15
> **luvshines said:**
> How are you accessing Ubuntu machine at present ??
Are you using putty to connect with SSH or using WinSCP ??

in my win box..

I go START >> Command Prompt  (Windows version of 'terminal')..

then I just put "ssh linuxbox"  (Ive adjusted my windows box 'hosts' file to have the IP address recorded as 'linuxbox'..

I just contact the SSH on ubuntu - Enter my password & I guess everything from then on, is normal SSH

---

### Post by luvshines on 2010-10-15
> **sarahfoxnz said:**
> in my win box..

I go START >> Command Prompt  (Windows version of 'terminal')..

then I just put "ssh linuxbox"  (Ive adjusted my windows box 'hosts' file to have the IP address recorded as 'linuxbox'..

I just contact the SSH on ubuntu - Enter my password & I guess everything from then on, is normal SSH

Well I know Windows CMD, I am a 70% Ubuntu 30% Windows user :D
What I don't get is that ssh will not work from Windows unless you have installed some SSH client

---

