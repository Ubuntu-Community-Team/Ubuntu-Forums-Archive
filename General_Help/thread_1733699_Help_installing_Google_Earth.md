---
title: "Help installing Google Earth"
date: 2011-04-19
forum: General Help
---

### Post by carega on 2011-04-19
Hey there! I'm new to Ubuntu and I must say I like it very much.

I've had my share of problems installing google earth lately. I read several forums and did many things and it all ended like this:

```
carega@amaterasu:~$ sudo apt-get install googleearth-package
[sudo] password for carega: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes NUEVOS:
  googleearth-package
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0B/10,7kB de archivos.
Se utilizarán 69,6kB de espacio de disco adicional después de esta operación.
Seleccionando el paquete googleearth-package previamente no seleccionado.
(Leyendo la base de datos ...  00%
196532 ficheros y directorios instalados actualmente.)
Desempaquetando googleearth-package (de .../googleearth-package_0.5.7_all.deb) ...
Procesando disparadores para man-db ...
Configurando googleearth-package (0.5.7) ...
carega@amaterasu:~$ cd && make-googleearth-package --force
cat: /etc/mailname: No existe el fichero o el directorio
Google Earth for GNU/Linux 6.0.2.2074
Unrecognized Google Earth version; using anyway (because of --force).
Guessed Google Earth version: 6.0.2.2074
./
./googleearth.xpm
./desktop_icons/
./desktop_icons/pro/
./desktop_icons/pro/product_logo_128.png
./desktop_icons/pro/product_logo_22.png
./desktop_icons/pro/product_logo_64.png
./desktop_icons/pro/product_logo_16.png
./desktop_icons/pro/product_logo_256.png
./desktop_icons/pro/product_logo_32.xpm
./desktop_icons/pro/product_logo_24.png
./desktop_icons/pro/product_logo_48.png
./desktop_icons/pro/product_logo_32.png
./desktop_icons/ec/
./desktop_icons/ec/product_logo_128.png
./desktop_icons/ec/product_logo_22.png
./desktop_icons/ec/product_logo_64.png
./desktop_icons/ec/product_logo_16.png
./desktop_icons/ec/product_logo_256.png
./desktop_icons/ec/product_logo_32.xpm
./desktop_icons/ec/product_logo_24.png
./desktop_icons/ec/product_logo_48.png
./desktop_icons/ec/product_logo_32.png
./desktop_icons/consumer/
./desktop_icons/consumer/product_logo_128.png
./desktop_icons/consumer/product_logo_22.png
./desktop_icons/consumer/product_logo_64.png
./desktop_icons/consumer/product_logo_16.png
./desktop_icons/consumer/product_logo_256.png
./desktop_icons/consumer/product_logo_32.xpm
./desktop_icons/consumer/product_logo_24.png
./desktop_icons/consumer/product_logo_48.png
./desktop_icons/consumer/product_logo_32.png
./setup.sh
./googleearth-linux-x86.tar
./setup.data/
./setup.data/locale/
./setup.data/locale/es/
./setup.data/locale/es/LC_MESSAGES/
./setup.data/locale/es/LC_MESSAGES/setup.mo
./setup.data/locale/es/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/fr/
./setup.data/locale/fr/LC_MESSAGES/
./setup.data/locale/fr/LC_MESSAGES/setup.mo
./setup.data/locale/fr/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/nl/
./setup.data/locale/nl/LC_MESSAGES/
./setup.data/locale/nl/LC_MESSAGES/setup.mo
./setup.data/locale/nl/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/sv/
./setup.data/locale/sv/LC_MESSAGES/
./setup.data/locale/sv/LC_MESSAGES/setup.mo
./setup.data/locale/sv/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/ru/
./setup.data/locale/ru/LC_MESSAGES/
./setup.data/locale/ru/LC_MESSAGES/setup.mo
./setup.data/locale/ru/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/it/
./setup.data/locale/it/LC_MESSAGES/
./setup.data/locale/it/LC_MESSAGES/setup.mo
./setup.data/locale/it/LC_MESSAGES/loki-uninstall.mo
./setup.data/locale/de/
./setup.data/locale/de/LC_MESSAGES/
./setup.data/locale/de/LC_MESSAGES/setup.mo
./setup.data/locale/de/LC_MESSAGES/loki-uninstall.mo
./setup.data/setup.xml
./setup.data/setup.glade
./setup.data/splash.xpm
./setup.data/setup.gtk2.glade
./setup.data/config.sh
./setup.data/bin/
./setup.data/bin/OpenBSD
./setup.data/bin/NetBSD
./setup.data/bin/Linux/
./setup.data/bin/Linux/x86_64
./setup.data/bin/Linux/x86/
./setup.data/bin/Linux/x86/setup.gtk2
./setup.data/bin/Linux/x86/uninstall
./setup.data/bin/Linux/x86/setup.gtk
./setup.data/bin/Linux/amd64
./setup.data/bin/FreeBSD
./README.linux
./googleearth-icon.png
./linux/
./linux/xdg/
./linux/xdg/xdg-desktop-menu
./linux/xdg/xdg-desktop-icon
./linux/xdg/xdg-mime
./googleearth-data.tar
./postinstall.sh
./bin/
./bin/googleearth
./preuninstall.sh
mv: no se puede efectuar `stat' sobre «libssl.so.0.9.8»: No existe el fichero o el directorio
Checking shlib deps: liblayout.so
dpkg-shlibdeps: aviso: No se puede extraer el nombre y la versión del nombre de la biblioteca «libmath.so»
{deleted a series of warnings that looked the same. If you need to I can copy them anyway}
dpkg-shlibdeps: aviso: No se puede extraer el nombre y la versión del nombre de la biblioteca «libspatial.so»
Checking shlib deps: libIGMath.so
Checking shlib deps: libicudata.so.38
Package: googleearth
Version: 6.0.2.2074+0.5.7-1
Section: non-free/science
Priority: optional
Maintainer:  <carega@amaterasu>
Architecture: i386
Depends: ttf-dejavu | ttf-bitstream-vera | msttcorefonts, fglrx, libc6 (>= 2.0), libc6 (>= 2.1.3), libc6 (>= 2.2), libc6 (>= 2.3), libc6 (>= 2.3.2), libc6 (>= 2.3.6-6~), libc6 (>= 2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libice6 (>= 1:1.0.0), libsm6, libstdc++6 (>= 4.1.1), libx11-6, libxext6, libxrender1, zlib1g (>= 1:1.1.4) 
Description: Google Earth, a 3D map/planet viewer
 Package built with googleearth-package.
dpkg-deb: construyendo el paquete `googleearth' en `./googleearth_6.0.2.2074+0.5.7-1_i386.deb'.
Success!
You can now install the package with e.g. sudo dpkg -i <package>.deb
carega@amaterasu:~$ sudo apt-get install gdebi-core
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes NUEVOS:
  gdebi-core
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 19,5kB de archivos.
Se utilizarán 143kB de espacio de disco adicional después de esta operación.
Des:1 http://ar.archive.ubuntu.com/ubuntu/ maverick/main gdebi-core all 0.6.3ubuntu1 [19,5kB]
Descargados 19,5kB en 1seg. (12,0kB/s)
Seleccionando el paquete gdebi-core previamente no seleccionado.
(Leyendo la base de datos ...  00%
196538 ficheros y directorios instalados actualmente.)
Desempaquetando gdebi-core (de .../gdebi-core_0.6.3ubuntu1_all.deb) ...
Procesando disparadores para man-db ...
Configurando gdebi-core (0.6.3ubuntu1) ...
Procesando disparadores para python-central ...
carega@amaterasu:~$ sudo dpkg -i ./googleearth_6.0.2.2074+0.5.7-1_i386.deb 
Seleccionando el paquete googleearth previamente no seleccionado.
(Leyendo la base de datos ...  00%
196556 ficheros y directorios instalados actualmente.)
Desempaquetando googleearth (de .../googleearth_6.0.2.2074+0.5.7-1_i386.deb) ...
Configurando googleearth (6.0.2.2074+0.5.7-1) ...
Procesando disparadores para shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Procesando disparadores para desktop-file-utils ...
Procesando disparadores para python-gmenu ...
Rebuilding /usr/share/applications/desktop.es_AR.utf8.cache...
Procesando disparadores para python-support ...
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/carega/.googleearth/crashlogs/crashlog-4dadca04.txt

Please include this file if you submit a bug report to Google.
```The bug report states the following:

```
 Major Version 5
Minor Version 2
Build Number 0001
Build Date Sep  1 2010
Build Time 11:25:42
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 35
OS Patch Version 0
Crash Signal 11
Crash Time 1303238562
Up Time 0,704196

Stacktrace from glibc:
./libgoogleearth_free.so(+0xd090b)[0x1e090b]
[0xa30400]
```I already tried installing version 5 to see if being a beta was a problem. I also followed these steps [http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html](http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html) and got nowhere. Can anyone help please? I already have lsb-core:

```
 carega@amaterasu:~$ sudo apt-get install lsb-core
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
lsb-core ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
```I'm using Ubuntu 10.10 and a COMPAQ Presario CQ40-320LA. Thanks!

EDIT: One more thing! I uninstalled it but there is still a Google Earth icon on Aplications > Internet. When I click on it I get the same thing as before. Doing it on terminal gives me the same crash. When I try and remove the program using sudo apt-get remove googleearth it tells me the file cannot be found. Looking for it on synaptic brings the same result, there is, supposedly, no google earth installed. However there is the directory /usr/local/google-earth/ with a lot of files! Here's the content:

```
drivers.ini                 libevll.so              libmeasure.so
googleearth                 libflightsim.so         libmoduleframework.so
googleearth-bin             libfusioncommon.so      libnavigate.so
googleearth-icon.png        libgdal.so.1            libnss_mdns4_minimal.so.2
googleearth-mimetypes.xml   libge_net.so            libport.so
googleearth.xpm             libgeobase.so           libproj.so.0
Google-googleearth.desktop  libgeobaseutils.so      libQtCore.so.4
gpl.txt                     libGLU.so.1             libQtGui.so.4
gpsbabel                    libgoogleearth_free.so  libQtNetwork.so.4
ImporterGlobalSettings.ini  libgooglesearch.so      libQtWebKit.so.4
ImporterUISettings.ini      libgps.so               librender.so
kh20                        libicudata.so.38        libreporting.so
lang                        libicuuc.so.38          libsgutil.so
libalchemyext.so            libIGAttrs.so           libspatial.so
libapiloader.so             libIGCore.so            libviewsync.so
libauth.so                  libIGExportCommon.so    libwebbrowser.so
libbase.so                  libIGGfx.so             libwmsbase.so
libbasicingest.so           libIGMath.so            linux
libcollada.so               libIGOpt.so             PCOptimizations.ini
libcommon_gui.so            libIGSg.so              plugins
libcommon_platform.so       libIGUtils.so           qt.conf
libcommon.so                libinput_plugin.so      resources
libcommon_webbrowser.so     liblayer.so             shaders
libcomponentframework.so    liblayout.so            uninstall
libcurl.so.4                libmath.so
```

---

### Post by PCaddicted on 2011-04-19
My suggestion:I think it would be better if you did this way: download Google Earth from [http://www.google.com/earth/download/ge/agree.html]("http://www.google.com/earth/download/ge/agree.html").For this, make sure the 32 bit or 64 bit deb package(for Debian/Ubuntu) is selected.If your system is 32-bit select the first option,if it is 64-bit,select the second option(maybe you tried to install the 32-bit package on a 64-bit system or vice-versa).Once the deb file has been downloaded,navigate to it and double-click it to install Google Earth.It is easier than using the terminal,I am sure.I managed to smoothly install Google Earth on my 32-bit Ubuntu 10.10 computer this way.And the program is fully functional.Hope my advice helps.

---

### Post by CoolJohnB on 2011-04-19
In Synaptic or Software Center you need to install googleearth which adds some necessary files also you need to install lsb-core having done that you can install the downloaded .deb file and everything should work well.

---

### Post by carega on 2011-04-19
@PCAddicted: That was the first thing I did. But it never worked, the screen displaying GOOGLE EARTH would open and then nothing else happened. When trying to open it through terminal the crash I spoke earlier occurs.

@CoolJohnB.: The Software center does not find googleearth and Synaptic only finds the file used to make a debian. 

Regarding the lsb-core installation:[FONT=monospace]
[/FONT]> [FONT=monospace]c[/FONT]arega@amaterasu:~$ sudo apt-get install lsb-core
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
lsb-core ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
In english: "lsb-core is already in it's most recent version".

Thanks for your quick replies!

---

### Post by gandaran on 2011-04-19
> **carega said:**
> @PCAddicted: That was the first thing I did. But it never worked, the screen displaying GOOGLE EARTH would open and then nothing else happened. When trying to open it through terminal the crash I spoke earlier occurs.

@CoolJohnB.: The Software center does not find googleearth and Synaptic only finds the file used to make a debian. 

Regarding the lsb-core installation:[FONT=monospace]
[/FONT]
In english: "lsb-core is already in it's most recent version".

Thanks for your quick replies!
what type of google-earth package did you download and installed the .bin or .deb package? if you installed from the .bin package you need to install something more (don't remember exactly what) besides the lsb-core package to make it work and the .bin google-earth wont show in synaptic only the .deb file appears in the package manager.

---

### Post by carega on 2011-04-19
I installed Google Earth 6.0 (beta) from [http://www.google.es/intl/es_es/earth/download/ge/agree.html](http://www.google.es/intl/es_es/earth/download/ge/agree.html).
Once that didn't work I removed it and installed the 5.2 version, which didn't help either.

If by the "something more" you mean gdebi-core I installed it already and still not working. Can this, by any chance, have anything to do with my graphics card? i have the following:

```
 carega@amaterasu:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
```

---

