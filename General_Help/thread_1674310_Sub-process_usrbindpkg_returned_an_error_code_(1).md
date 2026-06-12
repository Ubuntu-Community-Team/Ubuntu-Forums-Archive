---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-01-23
forum: General Help
---

### Post by jakupl on 2011-01-23
I can't remove the package called "tftpd-hpa".
My terminal is in partially in Danish, but you will understand most of it anyway. Here is what I get:

```

lilja@lilja-laptop:~$ sudo apt-get remove tftpd-hpa
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Følgende pakker blev installeret automatisk, og behøves ikke længere:
  libparted0
Brug 'apt-get autoremove' til at fjerne dem.
Følgende pakker vil blive AFINSTALLERET:
  tftpd-hpa
0 opgraderes, 0 nyinstalleres, 1 afinstalleres og 0 opgraderes ikke.
1 ikke fuldstændigt installerede eller afinstallerede.
After this operation, 152kB disk space will be freed.
Vil du fortsætte [J/n]? j
(Læser database... 309680 filer og mapper aktuelt installeret.)
Afinstallerer tftpd-hpa...
/etc/default/tftpd-hpa: 4: Syntax error: Unterminated quoted string
invoke-rc.d: initscript tftpd-hpa, action "stop" failed.
dpkg: fejl under behandling af tftpd-hpa (--remove):
 underproces installed pre-removal script returnerede afslutningsstatus 2
update-rc.d: warning: tftpd-hpa start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: tftpd-hpa stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 6)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
		-n: not really
		-f: force

The disable|enable API is not stable and might change in the future.
dpkg: fejl under oprydning:
 underproces installed post-installation script returnerede afslutningsstatus 1
Der opstod fejl under behandlingen:
 tftpd-hpa
E: Sub-process /usr/bin/dpkg returned an error code (1)
lilja@lilja-laptop:~$ 

```

I have tried 
apt-get clean, 
apt-get -f remove
apt-get update
dpkg --configure -a

Nothing seems to work. Any help is greatly appreaciated :)


EDIT:

LOL This is what Google translate makes of the output:

(I've never tried putting ubuntu terminal output through google translate)
```

Lilja Lilja @ laptop: ~ $ sudo apt-get remove tftpd-hpa 
Reading package lists ... Finished 
Parse 
Reading state information ... Finished 
The following packages were automatically installed and are no longer needed: 
  libparted0 
Use 'apt-get autoremove' to remove them. 
The following packages will be REMOVED: 
  tftpd-hpa 
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded. 
1 not fully installed or uninstalled. 
After this operation, 152kB disk space bliver freed. 
Do you want to continue [Y / n]? j 
(Reading database ... 309680 files and directories currently installed.) 
Uninstalling tftpd-hpa ... 
/ Etc / default / tftpd-hpa: 4: Syntax error: Unterminated quoted string 
Invoke-rc.d: initscripts tftpd-hpa, action "stop" failed. 
dpkg: error processing tftpd-hpa (- remove): 
 subprocess installeret pre-removal script returned exit status 2 
update-rc.d: warning: tftpd-hpa start runlevel argument (none) Do Not Match LSB Default-Start values (2 3 4 5) 
update-rc.d: warning: tftpd-hpa stop runlevel argument (none) Do Not Match LSB Default-Stop values (0 1 6) 
usage: update-rc.d [-n] [-f] <basename> remove 
       update-rc.d [-n] <basename> defaults [NN | SS KK] 
       update-rc.d [-n] <basename> start | stop NN runlvl [runlvl] [...]. 
       update-rc.d [-n] <basename> disable | enable [S | 2 | 3 | 4 | 5] 
-N: not really 
-F: force 

The disable | enable API er ikke stack and Might change in the future. 
dpkg: error while cleaning up: 
 subprocess installeret post-installation script returned exit status 1 
Errors occurred during processing: 
 tftpd-hpa 
E: Sub-process / usr / bin / dpkg returned an error code (1) 
Lilja Lilja @ laptop: ~ $

```

---

### Post by dabl on 2011-01-23
Try

```
sudo apt-get -f install
```

in case it is not fully installed.

Then try to remove it.

---

### Post by jakupl on 2011-01-23
I think I got kinda the same:

```

lilja@lilja-laptop:~$ sudo apt-get -f install tftpd-hpa
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Følgende pakker blev installeret automatisk, og behøves ikke længere:
  libparted0
Brug 'apt-get autoremove' til at fjerne dem.
Foreslåede pakker:
  syslinux-common
Følgende pakker vil blive opgraderet:
  tftpd-hpa
1 opgraderes, 0 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.
1 ikke fuldstændigt installerede eller afinstallerede.
44,8kB skal hentes fra arkiverne.
After this operation, 24,6kB of additional disk space will be used.
Henter:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/main tftpd-hpa 5.0-11ubuntu2.1 [44,8kB]
Hentede 44,8kB på 0s (161kB/s)   
Prækonfigurerer pakker ...
/etc/default/tftpd-hpa: 4: Syntax error: Unterminated quoted string
tftpd-hpa fejlede i prækonfigurering med afslutningsstatus 2
Vælger tidligere fravalgt pakke tftpd-hpa.
(Læser database... 309681 filer og mapper aktuelt installeret.)
Gør klar til at erstatte tftpd-hpa 0.43-1.1ubuntu1 (med .../tftpd-hpa_5.0-11ubuntu2.1_i386.deb)...
/etc/default/tftpd-hpa: 4: Syntax error: Unterminated quoted string
invoke-rc.d: initscript tftpd-hpa, action "stop" failed.
dpkg: warning: gammelt pre-removal-script returned error exit status 2
dpkg - forsøger i stedet script fra ny pakke...
stop: Unknown instance: 
dpkg: ... det ser ud til, at alt gik o.k.
/etc/default/tftpd-hpa: 4: Syntax error: Unterminated quoted string
dpkg: fejl under behandling af /var/cache/apt/archives/tftpd-hpa_5.0-11ubuntu2.1_i386.deb (--unpack):
 underproces nyt pre-installation-script returnerede afslutningsstatus 2
update-rc.d: warning: tftpd-hpa start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: tftpd-hpa stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 6)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
		-n: not really
		-f: force

The disable|enable API is not stable and might change in the future.
dpkg: fejl under oprydning:
 underproces installed post-installation script returnerede afslutningsstatus 1
Der opstod fejl under behandlingen:
 /var/cache/apt/archives/tftpd-hpa_5.0-11ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
lilja@lilja-laptop:~$ 

```

---

### Post by jakupl on 2011-01-23
IT WORKED

When I tried to remove the package after installing it. :)
thanks.

---

