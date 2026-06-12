---
title: "Problem upgrading ubuntu"
date: 2012-04-16
forum: General Help
---

### Post by gvillaran on 2012-04-16
hi, im trying to run apt-get upgrade and im getting the following error :

After this operation, 8487kB of additional disk space will be used.
Get:1 [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) lucid-updates/main libapache2-mod-php5 5.3.2-1ubuntu4.14 [2990kB]
Fetched 2990kB in 2min 19s (21.4kB/s)
(Reading database ... 209358 files and directories currently installed.)
Preparing to replace procps 1:3.2.8-1ubuntu4 (using .../procps_1%3a3.2.8-1ubuntu4_amd64.deb) ...
Unpacking replacement procps ...
dpkg: error processing /var/cache/apt/archives/procps_1%3a3.2.8-1ubuntu4_amd64.deb (--unpack):
 unable to make backup link of `./bin/ps' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.3.2-1ubuntu4.14_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/procps_1%3a3.2.8-1ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

anyone can give me some pointers on how to solve it please?

---

### Post by jadtech on 2012-04-16
what is it you are upgrading too
you could try this 

 in a term window type in update-manager -d

---

### Post by gvillaran on 2012-04-16
im still using Ubuntu Linux 10.04.2, just ran apt-get like another common day and gave me that error in the process

---

### Post by plucky on 2012-04-17
> **gvillaran said:**
> im still using Ubuntu Linux 10.04.2, just ran apt-get like another common day and gave me that error in the process

Try ```
sudo apt-get clean
sudo apt-get install -f
``` and post the whole output if any errors.

The first command will remove all the .deb files from the archive and the second command will try to fix the problem.

Good Luck.

---

### Post by gvillaran on 2012-04-18
Problem appear to be this package : rocps_1%3a3.2.8-1ubuntu4_amd64.

i did what u said and the error is the same :

Descargados 249kB en 9seg. (27.7kB/s)
(Leyendo la base de datos ...  00%
209362 ficheros y directorios instalados actualmente.)
Preparando para reemplazar procps 1:3.2.8-1ubuntu4 (usando .../procps_1%3a3.2.8-
1ubuntu4_amd64.deb) ...
Desempaquetando el reemplazo de procps ...
dpkg: error al procesar /var/cache/apt/archives/procps_1%3a3.2.8-1ubuntu4_amd64.
deb (--unpack):
 no se puede crear un enlace de seguridad de `./bin/ps' antes de instalar
la nueva versiÃ³n: OperaciÃ³n no permitida
dpkg-deb: el subproceso copiado fue terminado por la seÃ±al (TuberÃ*a rota)
dpkg: error al reorganizar:
 el subproceso script post-removal nuevo devolviÃ³ el cÃ³digo de salida de error
 1
Procesando disparadores para ureadahead ...
Se encontraron errores al procesar:
 /var/cache/apt/archives/procps_1%3a3.2.8-1ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Meneth on 2012-04-18
Since Maverick went out of support on  2012-04-10, you can no longer upgrade to it.

One wonders how to get Lucid LTS installations up to Oneiric.

Maybe you could jump-upgrade to Pangolin, but it hasn't been released yet.

---

### Post by gvillaran on 2012-04-18
Problem is that PHP is not working and now i cant install anything, some apps i had on the server stopped working.

so i cant do anything than erasing the server?

---

### Post by plucky on 2012-04-18
Try ```
sudo apt-get clean
sudo apt-get install -f
``` so it has to download another copy of the .deb file.

If that doesn't work try ```
sudo apt-get install --reinstall procps_1:3.2.8-1ubuntu4_amd64
```

Good Luck

---

### Post by gvillaran on 2012-04-18
im still gettin the same error :

Get:1 [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) lucid-updates/main procps 1:3.2.8-1ubuntu4.2 [250kB]
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin: 
Fetched 250kB in 15s (16.6kB/s)
(Reading database ... 209362 files and directories currently installed.)
Preparing to replace procps 1:3.2.8-1ubuntu4 (using .../procps_1%3a3.2.8-1ubuntu4.2_amd64.deb) ...
Unpacking replacement procps ...
dpkg: error processing /var/cache/apt/archives/procps_1%3a3.2.8-1ubuntu4.2_amd64.deb (--unpack):
 unable to make backup link of `./bin/ps' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/procps_1%3a3.2.8-1ubuntu4.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

weird that only an apt-get upgrade fails, first time that this happened to me

---

### Post by plucky on 2012-04-18
> unable to make backup link of `./bin/ps' before installing new version: Operation not permitted

I cannot find that file on my system, there is a /bin/ps file without the . in front of it.

You could try a different download server and get it to download from the new server.It could be a problem with the .deb file that is being loaded from your server.

Good Luck

---

