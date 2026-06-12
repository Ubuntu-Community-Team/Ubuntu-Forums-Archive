---
title: "Deja dup bad encryption password?"
date: 2011-07-17
forum: General Help
---

### Post by shresthanator on 2011-07-17
When I try to backup with deja dup (recently) its been giving me "Bad encryption Password" error. I searched about this online, and I went to passwords and encryption keys and made sure that the encryption key was what I set it to. Still it gives me the same error. What should I do about this?

---

### Post by David006 on 2011-11-06
I got the same error, after I upgraded to Ubuntu 11.10 (Oneiric) from Ubuntu 11.04.  Ubuntu 11.10 installs this package by default, and it is a newer version.

I was able to resolve by:

~$ **sudo apt-get purge deja-dup**
~$ **sudo apt-get install deja-dup**

But, I also needed to start a new local backup directory, as would not recognize rights to existing backup files.

---

### Post by Vertigo00 on 2012-02-29
If you have this error "Bad Encryption Password" popping up when Deja Dup tries to do a new backup, that's because the last backup made by the software is corrupt. To fix this problem, you should go in the folder where you backups are saved and delete the last file (should have .gpg file extension). Try again to run the Deja Dup backup manually. 

This worked for me. 
10.10 Maverick Meerkat
Deja Dup 16.0

---

### Post by fabio.hipolito on 2012-08-28
Hi to all,

Vertigo00 solution seems strange but worked for me.
If anyone tries to do this make sure you move the file that may be corrupt file, to avoid regreting later.

Cheers.

---

### Post by Votti on 2013-07-12
The Vertigo00 solution worked also for me. However Deja dup did never complain for me about an encryption error but just did repeating asking for my password. Strangely this issue did not only affect new backups but also the recovery of old backups.

---

### Post by elexhobby on 2013-10-06
In my case, I have used different passwords during different dates. Is there a way to provide multiple passwords while restoring to deja dup?

---

