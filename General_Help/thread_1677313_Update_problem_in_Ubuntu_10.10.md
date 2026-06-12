---
title: "Update problem in Ubuntu 10.10"
date: 2011-01-28
forum: General Help
---

### Post by ulriksvensson on 2011-01-28
Hi all. 

Ubuntu 10.10, x86_64

After having messed around with freenx and wine1.3 I have gotten errors on updating. I have manually removed packages that were broken. Most problems have been resolved but when I do apt-get -f install I get the following error:

```
ulrik@ulrik-desktop:/var/lib/dpkg/info$ sudo apt-get -f install
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  libva-x11-1 ttf-umefont libxcompext3 wine1.3-gecko x11vnc xvnc4viewer smbfs x11vnc-data libiso9660-7 libcddb2 tk libdvbpsi6 nx-common
  libvlc5 libsdl-image1.2 winetricks vlc-nox nxagent libxcomp3 expect libupnp3 vlc-plugin-notify libmatroska2 libxcompshad3
  libxcb-keysyms1 libvncserver0 freenx-smb linux-headers-2.6.35-24 nxlibs cifs-utils vlc-data libtar winbind libvlccore4 libvcdinfo0
  libebml2 linux-headers-2.6.35-24-generic libxcb-randr0 ttf-droid vlc-plugin-pulse ttf-symbol-replacement-wine1.3
Använd "apt-get autoremove" för att ta bort dem.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 2 att inte uppgradera.
7 är inte helt installerade eller borttagna.
Behöver hämta 0B/5 991kB arkiv.
Efter denna åtgärd kommer ytterligare 0B utrymme användas på disken.
debconf: Perl may be unconfigured (Can't locate loadable object for module Hash::Util in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/fields.pm line 122
Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Ställer in tar (1.23-2ubuntu1) ...
Can't locate loadable object for module File::Glob in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/sbin/update-mime line 54
Compilation failed in require at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: fel vid hantering av tar (--configure):
 underprocess installerade post-installation-skript gav felkod 9
Fel uppstod vid hantering:
 tar
E: Sub-process /usr/bin/dpkg returned an error code (1)
ulrik@ulrik-desktop:/var/lib/dpkg/info$ debconf -v
Can't locate loadable object for module Hash::Util in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/fields.pm line 122
Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/bin/debconf line 71.
BEGIN failed--compilation aborted at /usr/bin/debconf line 71.
ulrik@ulrik-desktop:/var/lib/dpkg/info$ debconf -h
Can't locate loadable object for module Hash::Util in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/fields.pm line 122
Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/bin/debconf line 71.
BEGIN failed--compilation aborted at /usr/bin/debconf line 71.
ulrik@ulrik-desktop:/var/lib/dpkg/info$ debconf
Can't locate loadable object for module Hash::Util in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/fields.pm line 122
Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/bin/debconf line 71.
BEGIN failed--compilation aborted at /usr/bin/debconf line 71.
ulrik@ulrik-desktop:/var/lib/dpkg/info$ man debconf
ulrik@ulrik-desktop:/var/lib/dpkg/info$ sudo apt-get reinstall perl
E: Felaktig åtgärd reinstall
ulrik@ulrik-desktop:/var/lib/dpkg/info$ sudo apt-get re-install perl
E: Felaktig åtgärd re-install
ulrik@ulrik-desktop:/var/lib/dpkg/info$ sudo apt-get -f install
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  libva-x11-1 ttf-umefont libxcompext3 wine1.3-gecko x11vnc xvnc4viewer smbfs x11vnc-data libiso9660-7 libcddb2 tk libdvbpsi6 nx-common
  libvlc5 libsdl-image1.2 winetricks vlc-nox nxagent libxcomp3 expect libupnp3 vlc-plugin-notify libmatroska2 libxcompshad3
  libxcb-keysyms1 libvncserver0 freenx-smb linux-headers-2.6.35-24 nxlibs cifs-utils vlc-data libtar winbind libvlccore4 libvcdinfo0
  libebml2 linux-headers-2.6.35-24-generic libxcb-randr0 ttf-droid vlc-plugin-pulse ttf-symbol-replacement-wine1.3
Använd "apt-get autoremove" för att ta bort dem.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 2 att inte uppgradera.
7 är inte helt installerade eller borttagna.
Behöver hämta 0B/5 991kB arkiv.
Efter denna åtgärd kommer ytterligare 0B utrymme användas på disken.
debconf: Perl may be unconfigured (Can't locate loadable object for module Hash::Util in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/fields.pm line 122
Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Ställer in tar (1.23-2ubuntu1) ...
Can't locate loadable object for module File::Glob in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/sbin/update-mime line 54
Compilation failed in require at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: fel vid hantering av tar (--configure):
 underprocess installerade post-installation-skript gav felkod 9
Fel uppstod vid hantering:
 tar
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I don't want to reinstall Ubuntu 10.10 all over even though I waas happier with 10.04. Can anyone see what I need to do?

---

### Post by ulriksvensson on 2011-01-28
Sorry about the Swedish...

---

### Post by sikander3786 on 2011-01-28
> **ulriksvensson said:**
> Sorry about the Swedish...
Can you please post those error messages in English. We'll be able to advise better and more appropriate then.

---

### Post by ulriksvensson on 2011-01-28
Ok. I'll try to translate from my best knowledge:

```

ulrik@ulrik-desktop:/var/lib/dpkg/info$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading status information... Done
The following packages have been installed automatically and are no longer nessecary:
  libva-x11-1 ttf-umefont libxcompext3 wine1.3-gecko x11vnc xvnc4viewer smbfs x11vnc-data libiso9660-7 libcddb2 tk libdvbpsi6 nx-common
  libvlc5 libsdl-image1.2 winetricks vlc-nox nxagent libxcomp3 expect libupnp3 vlc-plugin-notify libmatroska2 libxcompshad3
  libxcb-keysyms1 libvncserver0 freenx-smb linux-headers-2.6.35-24 nxlibs cifs-utils vlc-data libtar winbind libvlccore4 libvcdinfo0
  libebml2 linux-headers-2.6.35-24-generic libxcb-randr0 ttf-droid vlc-plugin-pulse ttf-symbol-replacement-wine1.3
Use "apt-get autoremove" to remove them.
0 to upgrade, 0 to install, 0to remove and 2 to not upgrade.
7 are not entirely installed or removed.
Need to get 0B/5 991kB archive.
After this action an additional 0B of space will be used on the disc.
debconf: Perl may be unconfigured (Can't locate loadable object for module Hash::Util in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/fields.pm line 122
Compilation failed in require at /usr/share/perl/5.10/fields.pm line 122.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Configuring tar (1.23-2ubuntu1) ...
Can't locate loadable object for module File::Glob in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/sbin/update-mime line 54
Compilation failed in require at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error while handling tar (--configure):
sub process installed post-installation-script returned error on exit 9
Error while handling:
 tar
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ulriksvensson on 2011-01-28
I think this one is beyond rescue. I'm going for a fresh install.

---

