---
title: "ls lists unexistent files"
date: 2009-10-05
forum: General Help
---

### Post by shankao asd on 2009-10-05
I have a problem with some files I want to delete. The filesystem is ext3 and ubuntu 9.04 with a linux kernel 2.6.22.18 but the problem persists when mounting the filesystem under the last karmic kernel.

The ls program gives me this output:

shankao@Dorothy:/media/Backup/Musica/mp3 varios$ ls -lai 
ls: cannot access Beyoncé-Dangerously in Love-03-Baby Boy (feat. Sean  Paul) (1.mp3: No such file or directory 
ls: cannot access La cabra mecánica - La lista de la compra.mp3: No such  file or directory 
ls: cannot access articolo 31 - non è un film.txt: No such file or directory 
ls: cannot access Blue Öyster Cult - (Don't Fear) The Reaper.MP3: No  such file or directory 
ls: cannot access Articolo 31 - La vita non è un film.mp3: No such file  or directory 
ls: cannot access Andrés Calamaro - Flaca.mp3: No such file or directory 
ls: cannot access La buena vida - Qué nos va a Pasar.mp3: No such file  or directory 
ls: cannot access La Casa Azul - La Revolución Sexual.mp3: No such file  or directory 
ls: cannot access José el francés - Fuera de mi.mp3: No such file or  directory 
ls: cannot access BETHOVEN - Symphonie N°9 (Extrait).mp3: No such file  or directory 
ls: cannot access El Canto del Loco - Son Sueños.mp3: No such file or  directory 
ls: cannot access télépopmusik - genetic world - 01 - breathe.mp3: No  such file or directory 
ls: cannot access Sinfonía nº 9 de Beethoven (Scherzo).wma: No such file  or directory 
ls: cannot access Neffa - Quando finisce così.mp3: No such file or directory 
ls: cannot access El Canto del Loco - La Madre de José.mp3: No such file  or directory 
ls: cannot access Articolo 31 - Cosí Com'è - 02 - Un Urlo.mp3: No such  file or directory 
ls: cannot access 07-Quítame la vida.mp3: No such file or directory 
ls: cannot access Dan Swanö - Creating Illusions.mp3: No such file or  directory 
ls: cannot access Antonio Orozco - Te esperaré.mp3: No such file or  directory 
ls: cannot access Azúcar moreno - Amén.mp3: No such file or directory 
ls: cannot access Tribalistas - Já Sei Namorar.mp3: No such file or  directory 
ls: cannot access Beyoncé-Dangerously in Love-01-Crazy in Love (feat.  Jay-z).mp3: No such file or directory 
ls: cannot access Motörhead - Ace of Spades.mp3: No such file or directory 
ls: cannot access Andrés Calamaro - Loco.mp3: No such file or directory 
ls: cannot access Alizée - Moi Lolita.mp3: No such file or directory 
ls: cannot access Nomadi - Dio è morto.mp3: No such file or directory 
total 80 
44105744 drwxrwxrwx   2 shankao shankao 65536 2009-10-05 11:41 . 
44105729 drwxr--r-- 114 shankao shankao 12288 2009-09-26 00:29 .. 
44106481 -?????????   ? ?       ?           ?                ?  07-Quítame la vida.mp3 
44106433 -?????????   ? ?       ?           ?                ? Alizée -  Moi Lolita.mp3 
44106426 -?????????   ? ?       ?           ?                ? Andrés  Calamaro - Flaca.mp3 
44106425 -?????????   ? ?       ?           ?                ? Andrés  Calamaro - Loco.mp3 
44106420 -?????????   ? ?       ?           ?                ? Antonio  Orozco - Te esperaré.mp3 
44106415 -?????????   ? ?       ?           ?                ? Articolo  31 - Cosí Com'è - 02 - Un Urlo.mp3 
44106411 -?????????   ? ?       ?           ?                ? Articolo  31 - La vita non è un film.mp3 
44105838 -?????????   ? ?       ?           ?                ? articolo  31 - non è un film.txt 
44106405 -?????????   ? ?       ?           ?                ? Azúcar  moreno - Amén.mp3 
44106403 -?????????   ? ?       ?           ?                ? BETHOVEN  - Symphonie N°9 (Extrait).mp3 
44106390 -?????????   ? ?       ?           ?                ?  Beyoncé-Dangerously in Love-01-Crazy in Love (feat. Jay-z).mp3 
44106389 -?????????   ? ?       ?           ?                ?  Beyoncé-Dangerously in Love-03-Baby Boy (feat. Sean Paul) (1.mp3 
44106383 -?????????   ? ?       ?           ?                ? Blue  Öyster Cult - (Don't Fear) The Reaper.MP3 
44106317 -?????????   ? ?       ?           ?                ? Dan Swanö  - Creating Illusions.mp3 
44106284 -?????????   ? ?       ?           ?                ? El Canto  del Loco - La Madre de José.mp3 
44106282 -?????????   ? ?       ?           ?                ? El Canto  del Loco - Son Sueños.mp3 
44106174 -?????????   ? ?       ?           ?                ? José el  francés - Fuera de mi.mp3 
44106155 -?????????   ? ?       ?           ?                ? La buena  vida - Qué nos va a Pasar.mp3 
44106153 -?????????   ? ?       ?           ?                ? La cabra  mecánica - La lista de la compra.mp3 
3596312 -?????????   ? ?       ?           ?                ? La Casa  Azul - La Revolución Sexual.mp3 
44106061 -?????????   ? ?       ?           ?                ? Motörhead  - Ace of Spades.mp3 
44106051 -?????????   ? ?       ?           ?                ? Neffa -  Quando finisce così.mp3 
44106041 -?????????   ? ?       ?           ?                ? Nomadi -  Dio è morto.mp3 
44105944 -?????????   ? ?       ?           ?                ? Sinfonía  nº 9 de Beethoven (Scherzo).wma 
44105752 -?????????   ? ?       ?           ?                ?  télépopmusik - genetic world - 01 - breathe.mp3 
44105864 -?????????   ? ?       ?           ?                ?  Tribalistas - Já Sei Namorar.mp3 
shankao@Dorothy:/media/Backup/Musica/mp3 varios$ 


Note the strange ? signs in the file flags. When I try to delete them, rm gives me an error:

shankao@Dorothy:/media/Backup/Musica/mp3 varios$ rm "Tribalistas - Já  Sei Namorar.mp3" 
rm: cannot remove `Tribalistas - Já Sei Namorar.mp3': No such file or  directory 
shankao@Dorothy:/media/Backup/Musica/mp3 varios$ 

And trying by inode number:

shankao@Dorothy:/media/Backup/Musica/mp3 varios$ rm -i 44105864 
rm: cannot remove `44105864': No such file or directory 
shankao@Dorothy:/media/Backup/Musica/mp3 varios$ 

How can I remove those files? Trying a "rm -rf" of the parent subdirectory is useless as rm gives me an error as it can't delete a not empty subdirectory.

Any clue? Is my filesystem messed up?

---

### Post by HiImTye on 2009-10-05
do you have permissions for the contained files and folders?

---

### Post by geirha on 2009-10-05
Seems like a problem with the filesystem. I'd try unmounting the filesystem and run fsck on it. You can do that from [gparted](apt://gparted) (System -> Administration -> Partition Editor). Right-click the partition and choose unmount, then right-click it again and choose Check.

If the filesystem is in use in any way, you won't be able to unmount it. (If it is /, it's impossible to unmount it). So if you are unable to close all applications that use it, boot with the Ubuntu CD and do it from there.

Or, you can do ```
sudo touch /forcefsck
``` then reboot. If a file by the name /forcefsck is found during boot, all filesystems listed and marked to be checked in /etc/fstab, will be checked.

---

### Post by Giblet5 on 2009-10-05
It looks to *me* like it's just messed-up filenames.

The ls command you posted makes that very clear. The files are there but you'll have an interesting time accessing them from a shell running in English...

This often results from creating i18n (eg, Traditional Chinese) names in a GUI file manager, then trying to access them from a shell that's running in the "C" (US English) locale.

Don't do that or this will happen again, and again, and again.

Make sure you have installed the language pack for the language you're using. Make sure your account is set up to use that locale and that you have an appropriate input method or an appropriate keyboard (traditional chinese keyboard - I've seen one - WOW!).

---

