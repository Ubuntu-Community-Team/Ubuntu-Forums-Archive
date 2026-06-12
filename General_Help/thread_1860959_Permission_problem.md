---
title: "Permission problem"
date: 2011-10-15
forum: General Help
---

### Post by Ogru on 2011-10-15
Hi All,

I have what I believe is trivial problem.

I have HTPC running Ubuntu and XBMC, on the same network I have Bufallo NAS running debian lenny. Hard rive on the HTPC is running out of space, so I decided to mount NAS and start downloading movies to the NAS. Managed to mount remote drive to /home/xbmc/MoviesNAS:

```

/etc/fstab:

//192.168.1.67/MediaPlayer/Mov/ /home/xbmc/MoviesNAS/ cifs username=xxx,password=xxx,dir_mode=777,file_mode=777 0 0

```

when I tried to create a file/directory as a root in /home/xbmc/MoviesNAS it works fine but as a xbmc user i have no permition.

I've added xbmc user to root group by:
```
 usermod -g root xbmc 
```

I  tried to change /home/xbmc/MoviesNAS ownership and permition by 
```
 sudo chown -R xbmc:xbmc /home/xbmc/MoviesNAS/ 

chmod -R 777 /home/xbmc/MoviesNAS/
```

Nothink helps.

Could someone kindly help me out?

The reason behind this is that I'm running transmission client under xbmc user and I want it to download stuff to /home/xbmc/MoviesNAS/.

Thanks,

Ogru - linux n00b...

---

### Post by Blaqksheep on 2011-10-15
Try this instead.

```
chmod +w /home/xbmc/MoviesNAS/
```

Then try to create a folder.

The easiest way to change permissions using chmod is to just tic or untic specific ones.

+w allows write
-w disallows write
+r allows read
-r disallows read
+x allows executing
-x disallows executing.

Hope it works for ya.

---

### Post by Ogru on 2011-10-16
Hi Blaqksheep,

Thanks for your answer but still no luck:

```

Last login: Sun Oct 16 09:52:59 2011 from xbmc-2.lan

xbmc@XBMCLive:~$ sudo chmod +w /home/xbmc/MoviesNAS/
[sudo] password for xbmc:

xbmc@XBMCLive:~$ mkdir /home/xbmc/MoviesNAS/test
mkdir: cannot create directory `/home/xbmc/MoviesNAS/test': Permission denied

xbmc@XBMCLive:~$ ls -l /home/xbmc/ | grep MoviesNAS
drwxr-xr-x  1 root root     0 2007-12-29 18:59 MoviesNAS

```

Ogru

---

### Post by Ogru on 2011-10-18
Anyone? 

Please!

---

### Post by TaTaE on 2011-11-13
I have a similar problem. Some files become inaccessible, even for root.

I can't list or remove these files.

```
root@firewall:~# ls -ls   /media/sambaa/fisiere/var/www
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-full.20111112T021708Z.vol1.difftar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-inc.20111111T181707Z.to.20111111T191708Z.vol1.difftar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-inc.20111111T191708Z.to.20111111T201708Z.vol1.difftar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-inc.20111111T201708Z.to.20111111T211709Z.vol1.difftar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-inc.20111111T211709Z.to.20111111T221709Z.vol1.difftar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-inc.20111111T221709Z.to.20111111T231710Z.vol1.difftar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-inc.20111111T231710Z.to.20111112T001709Z.vol1.difftar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-inc.20111112T001709Z.to.20111112T011709Z.vol1.difftar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-new-signatures.20111111T181707Z.to.20111111T191708Z.sigtar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-new-signatures.20111111T191708Z.to.20111111T201708Z.sigtar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-new-signatures.20111111T201708Z.to.20111111T211709Z.sigtar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-new-signatures.20111111T211709Z.to.20111111T221709Z.sigtar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-new-signatures.20111111T221709Z.to.20111111T231710Z.sigtar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-new-signatures.20111111T231710Z.to.20111112T001709Z.sigtar.gz: No such file or directory
ls: cannot access /media/sambaa/fisiere/var/www/duplicity-new-signatures.20111112T001709Z.to.20111112T011709Z.sigtar.gz: No such file or directory
total 0
? -????????? ? ? ? ?                ? duplicity-full.20111112T021708Z.vol1.difftar.gz
? -????????? ? ? ? ?                ? duplicity-inc.20111111T181707Z.to.20111111T191708Z.vol1.difftar.gz
? -????????? ? ? ? ?                ? duplicity-inc.20111111T191708Z.to.20111111T201708Z.vol1.difftar.gz
? -????????? ? ? ? ?                ? duplicity-inc.20111111T201708Z.to.20111111T211709Z.vol1.difftar.gz
? -????????? ? ? ? ?                ? duplicity-inc.20111111T211709Z.to.20111111T221709Z.vol1.difftar.gz
? -????????? ? ? ? ?                ? duplicity-inc.20111111T221709Z.to.20111111T231710Z.vol1.difftar.gz
? -????????? ? ? ? ?                ? duplicity-inc.20111111T231710Z.to.20111112T001709Z.vol1.difftar.gz
? -????????? ? ? ? ?                ? duplicity-inc.20111112T001709Z.to.20111112T011709Z.vol1.difftar.gz
? -????????? ? ? ? ?                ? duplicity-new-signatures.20111111T181707Z.to.20111111T191708Z.sigtar.gz
? -????????? ? ? ? ?                ? duplicity-new-signatures.20111111T191708Z.to.20111111T201708Z.sigtar.gz
? -????????? ? ? ? ?                ? duplicity-new-signatures.20111111T201708Z.to.20111111T211709Z.sigtar.gz
? -????????? ? ? ? ?                ? duplicity-new-signatures.20111111T211709Z.to.20111111T221709Z.sigtar.gz
? -????????? ? ? ? ?                ? duplicity-new-signatures.20111111T221709Z.to.20111111T231710Z.sigtar.gz
? -????????? ? ? ? ?                ? duplicity-new-signatures.20111111T231710Z.to.20111112T001709Z.sigtar.gz
? -????????? ? ? ? ?                ? duplicity-new-signatures.20111112T001709Z.to.20111112T011709Z.sigtar.gz


```

---

