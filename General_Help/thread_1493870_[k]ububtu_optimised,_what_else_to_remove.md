---
title: "[k]ububtu optimised, what else to remove?"
date: 2010-05-26
forum: General Help
---

### Post by pbhj on 2010-05-26
I'm trying to optimise my system (Athlon 1.1G single core, 786MB) mainly I'm looking to stop anything running that doesn't need to be so that the system can be as stable and lean as possible.

Here's what I have installed (from "[FONT="Courier New"]aptitude search '~i'[/FONT]"), can anyone see anything else that I could/should remove? Or if you have a lean system yourself (Gnome or KDE) could you post your list using aptitude please, thanks.

```

i   acpid                           - Advanced Configuration and Power Interface
i   adduser                         - add and remove users and groups           
i   adobe-flashplugin               - Adobe Flash Player plugin version 10      
i A akonadi-server                  - Akonadi PIM storage service               
i   alsa-oss                        - ALSA wrapper for OSS applications         
i   app-install-data                - Ubuntu applications (data files)          
i   apparmor                        - User-space parser utility for AppArmor    
i   apparmor-utils                  - Utilities for controlling AppArmor        
i   apport                          - automatically generate crash reports for d
i A apport-kde                      - KDE frontend for the apport crash report s
i   apport-symptoms                 - symptom scripts for apport                
i   apt                             - Advanced front-end for dpkg               
i   apt-transport-https             - APT https transport                       
i   apt-utils                       - APT utility programs                      
i   aptitude                        - terminal-based package manager            
i   ark                             - archive utility for KDE 4                 
i   aspell                          - GNU Aspell spell-checker                  
i   aspell-en                       - English dictionary for GNU Aspell         
i   avahi-daemon                    - Avahi mDNS/DNS-SD daemon                  
i   base-files                      - Debian base system miscellaneous files    
i   base-passwd                     - Debian base system master password and gro
i   bash                            - The GNU Bourne Again SHell                
i   bash-completion                 - programmable completion for the bash shell
i   bc                              - The GNU bc arbitrary precision calculator 
i   beep                            - advanced pc-speaker beeper                
i   bind9-host                      - Version of 'host' bundled with BIND 9.X   
i   binutils                        - The GNU assembler, linker and binary utili
i   bsdmainutils                    - collection of more utilities from FreeBSD 
i   bsdutils                        - Basic utilities from 4.4BSD-Lite          
i   bum                             - graphical runlevel editor                 
i   busybox-initramfs               - Standalone shell setup for initramfs      
i   bzip2                           - high-quality block-sorting file compressor
i   ca-certificates                 - Common CA certificates                    
i A ca-certificates-java            - Common CA certificates (JKS keystore)     
i   cdparanoia                      - audio extraction tool for sampling CDs    
i   cdrdao                          - records CDs in Disk-At-Once (DAO) mode    
i   command-not-found               - Suggest installation of packages in intera
i   command-not-found-data          - Set of data files for command-not-found.  
i   console-setup                   - console font and keymap setup program     
i   console-terminus                - Fixed-width fonts for fast reading on the 
i   consolekit                      - framework for defining and tracking users,
i   coreutils                       - The GNU core utilities                    
i   cpio                            - GNU cpio -- a program to manage archives o
i   cpp                             - The GNU C preprocessor (cpp)              
i   cpp-4.4                         - The GNU C preprocessor                    
i A cpu-checker                     - tools to help evaluate certain CPU (or BIO
i   cron                            - process scheduling daemon                 
i   dash                            - POSIX-compliant shell                     
i   dbus                            - simple interprocess messaging system      
i   dbus-x11                        - simple interprocess messaging system (X11 
i   debconf                         - Debian configuration management system    
i   debconf-i18n                    - full internationalization support for debc
i   debianutils                     - Miscellaneous utilities specific to Debian
i A default-jre                     - Standard Java or Java compatible Runtime  
i A default-jre-headless            - Standard Java or Java compatible Runtime (
i   defoma                          - Debian Font Manager -- automatic font conf
i A desktop-file-utils              - Utilities for .desktop files              
i   dhcp3-client                    - DHCP client                               
i   dhcp3-common                    - common files used by all the dhcp3* packag
i   dictionaries-common             - Common utilities for spelling dictionary t
i   diff                            - dummy transitional package for diff -> dif
i A diffutils                       - File comparison utilities                 
i   dmsetup                         - The Linux Kernel Device Mapper userspace l
i   dnsmasq-base                    - A small caching DNS proxy and DHCP/TFTP se
i   dnsutils                        - Clients provided with BIND                
i   dolphin                         - file manager for KDE 4                    
i   dosfstools                      - utilities for making and checking MS-DOS F
i   dpkg                            - Debian package management system          
i   e2fslibs                        - ext2/ext3/ext4 file system libraries      
i   e2fsprogs                       - ext2/ext3/ext4 file system utilities      
i   eject                           - ejects CDs and operates CD-Changers under 
i A esound-common                   - Enlightened Sound Daemon - Common files   
i   ethtool                         - display or change Ethernet device settings
i   ffmpeg                          - multimedia player, server and encoder     
i   fglrx-modaliases                - Identifiers supported by the ATI graphics 
i   file                            - Determines file type using "magic" numbers
i   findutils                       - utilities for finding files--find, xargs  
i   firefox                         - safe and easy web browser from Mozilla    
i   firefox-3.5-branding            - dummy upgrade package for firefox-3.5 -> f
i A firefox-branding                - Package that ships the firefox branding   
i   flashplugin-nonfree-extrasound  - Adobe Flash Player platform support librar
i   fontconfig                      - generic font configuration library - suppo
i   fontconfig-config               - generic font configuration library - confi
i   friendly-recovery               - Make recovery more user-friendly          
i   fuse-utils                      - Filesystem in USErspace (utilities)       
i   gcc                             - The GNU C compiler                        
i   gcc-4.4                         - The GNU C compiler                        
i   gcc-4.4-base                    - The GNU Compiler Collection (base package)
i A gconf2                          - GNOME configuration database system (suppo
i A gconf2-common                   - GNOME configuration database system (commo
i   gdb                             - The GNU Debugger                          
i   gdebi-core                      - Simple tool to install deb files          
i   gdebi-kde                       - Simple tool to install deb files - KDE GUI
i   genisoimage                     - Creates ISO-9660 CD-ROM filesystem images 
i   gettext-base                    - GNU Internationalization utilities for the
i   ghostscript                     - The GPL Ghostscript PostScript/PDF interpr
i   ghostscript-x                   - The GPL Ghostscript PostScript/PDF interpr
i A gnome-keyring                   - GNOME keyring services (daemon and tools) 
i A gnome-mime-data                 - base MIME and Application database for GNO
i   gnupg                           - GNU privacy guard - a free PGP replacement
i A gnupg-curl                      - GNU privacy guard - a free PGP replacement
i   google-chrome-stable            - The web browser from Google               
i   gpgv                            - GNU privacy guard - signature verification
i   grep                            - GNU grep, egrep and fgrep                 
i A grub-common                     - GRand Unified Bootloader, version 2 (commo
i A grub-pc                         - GRand Unified Bootloader, version 2 (PC/BI
i   gsfonts                         - Fonts for the Ghostscript interpreter(s)  
i   gstreamer0.10-ffmpeg            - FFmpeg plugin for GStreamer               
i   gstreamer0.10-pitfdll           - GStreamer plugin for using MS Windows bina
i   gstreamer0.10-plugins-bad-multi - GStreamer plugins from the "bad" set (Mult
i   gstreamer0.10-plugins-ugly      - GStreamer plugins from the "ugly" set     
i   gstreamer0.10-plugins-ugly-mult - GStreamer plugins from the "ugly" set (Mul
i A gstreamer0.10-pulseaudio        - GStreamer plugin for PulseAudio           
i   gtk2-engines-qtcurve            - This is a set of widget styles for Gtk2 ba
i A gvfs                            - userspace virtual filesystem - server     
i   gzip                            - GNU compression utilities                 
i   hal                             - Hardware Abstraction Layer                
i   hal-info                        - Hardware Abstraction Layer - fdi files    
i   hdparm                          - tune hard disk parameters for high perform
i   hicolor-icon-theme              - default fallback theme for FreeDesktop.org
i   hostname                        - utility to set/show the host name or domai
i   icedtea6-plugin                 - web browser plugin based on OpenJDK and Ic
i   ifupdown                        - high level tools to configure network inte
i   imagemagick                     - image manipulation programs               
i A indicator-application           - Application Indicators                    
i   initramfs-tools                 - tools for generating an initramfs         
i A initramfs-tools-bin             - binaries used by initramfs-tools          
i   initscripts                     - scripts for initializing and shutting down
i   inkscape                        - vector-based drawing program              
i   insserv                         - Tool to organize boot sequence using LSB i
i   install-package                 - Install a package GUI                     
i   iproute                         - networking and traffic control tools      
i   iptables                        - administration tools for packet filtering 
i   iputils-arping                  - Tool to send ARP Requests for an IP addres
i   iputils-ping                    - Tools to test the reachability of network 
i   iso-codes                       - ISO language, territory, currency, script 
i A java-common                     - Base of all Java packages                 
i   jockey-common                   - user interface and desktop integration for
i   jockey-kde                      - KDE user interface and desktop integration
i   kate                            - KDE 4 Advanced Text Editor                
i   kbd                             - Linux console font and keytable utilities 
i   kcm-gtk                         - Configuration module for GTK+ appearance i
i   kde-icons-oxygen                - transitional package for oxygen icon theme
i   kde-style-qtcurve               - Unified widget styles for KDE and GTK+    
i   kde-window-manager              - the KDE 4 window manager (KWin)           
i   kde-zeroconf                    - zeroconf plugins and kio slaves for KDE 4 
i   kdebase-bin                     - core binaries for the KDE 4 base module   
i   kdebase-data                    - shared data files for the KDE 4 base modul
i   kdebase-plasma                  - Transitional package for plasma-widget-fol
i   kdebase-runtime                 - runtime components from the official KDE 4
i   kdebase-runtime-bin-kde4        - transitional package for kdebase-runtime  
i   kdebase-runtime-data            - shared data files for the KDE 4 base runti
i   kdebase-runtime-data-common     - transitional package for kdebase-runtime-d
i   kdebase-workspace-bin           - core binaries for the KDE 4 base workspace
i   kdebase-workspace-data          - shared scripts and data files for the KDE 
i   kdebase-workspace-kgreet-plugin - KDE greet libraries for authentication    
i   kdebase-workspace-libs4+5       - Transitional package for kdebase-workspace
i   kdelibs-bin                     - executables for all KDE 4 core application
i   kdelibs5                        - core libraries for all KDE 4 applications 
i   kdelibs5-data                   - core shared data for all KDE 4 application
i   kdemultimedia-kio-plugins       - transparent audio CD access for KDE 4 appl
i   kdepasswd                       - password changer for KDE 4                
i A kdepim-runtime                  - Runtime components for akonadi-kde        
i   kdepimlibs-data                 - core shared data for KDE PIM 4 application
i   kdepimlibs5                     - core libraries for KDE PIM 4 applications 
i   kdesudo                         - sudo frontend for KDE4                    
i   kdiff3                          - compares and merges 2 or 3 files or direct
i   kdm                             - KDE Display Manager for X11               
i   kfind                           - file search utility for KDE 4             
i   kfourinline                     - Connect Four game for KDE                 
i   kgamma                          - monitor calibration panel for KDE 4       
i   khelpcenter4                    - Help Center for KDE 4                     
i   klibc-utils                     - small utilities built with klibc for early
i   klines                          - color lines game for KDE                  
i   klipper                         - clipboard utility for KDE 4               
i   kmix                            - volume control and mixer for KDE 4        
i   kmousetool                      - KDE mouse manipulation tool for the disabl
i   konq-plugins                    - plugins for Konqueror, the KDE file/web/do
i   konqueror                       - KDE 4's advanced file manager, web browser
i   konsole                         - X terminal emulator for KDE 4             
i   kppp                            - modem dialer for KDE 4                    
i   krdc                            - Remote Desktop Connection client for KDE 4
i   krfb                            - Desktop Sharing for KDE 4                 
i A krosspython                     - Python module for Kross                   
i   krusader                        - twin-panel (commander-style) file manager 
i   ksame                           - SameGame puzzle game for KDE              
i   ksnapshot                       - screen capture tool for KDE 4             
i   kspaceduel                      - SpaceWar! arcade game for KDE             
i   ksysguard                       - System Guard for KDE 4                    
i   ksystemlog                      - system log viewer for KDE 4               
i   kteatime                        - KDE 4 utility for making a fine cup of tea
i   ktorrent                        - BitTorrent client based on the KDE platfor
i   ktorrent-data                   - KTorrent data and other architecture indep
i   kubuntu-default-settings        - Default settings and artwork for the Kubun
i A kubuntu-notification-helper     - Kubuntu system notification helper        
i   kvkbd                           - Virtual keyboard for KDE                  
i   kwalletmanager                  - secure password wallet manager for KDE 4  
i A language-pack-en                - translation updates for language English  
i A language-pack-en-base           - translations for language English         
i A language-pack-kde-en            - KDE translation updates for language Engli
i   language-pack-kde-en-base       - KDE translations for language English     
i   latex-xft-fonts                 - Xft-compatible versions of some LaTeX font
i A launchpad-integration           - launchpad integration                     
i   less                            - pager program similar to more             
i   lftp                            - Sophisticated command-line FTP/HTTP client
i A liba52-0.7.4                    - library for decoding ATSC A/52 streams    
i   libaa1                          - ascii art library                         
i A libaccess-bridge-java           - Java Access Bridge for GNOME              
i A libaccess-bridge-java-jni       - Java Access Bridge for GNOME (jni bindings
i   libacl1                         - Access control list shared library        
i   libakonadiprivate1              - libraries for the Akonadi PIM storage serv
i   libao2                          - Cross Platform Audio Output Library       
i   libapparmor-perl                - AppArmor library Perl bindings            
i   libapparmor1                    - changehat AppArmor library                
i A libappindicator0                - Application Indicators                    
i   libarchive1                     - Single library to read/write tar, cpio, pa
i A libart-2.0-2                    - Library of functions for 2D graphics - run
i   libasound2                      - shared library for ALSA applications      
i A libasound2-plugins              - ALSA library additional plugins           
i   libaspell15                     - GNU Aspell spell-checker runtime library  
i A libass4                         - library for SSA/*** subtitles rendering   
i   libatasmart4                    - ATA S.M.A.R.T. reading and parsing library
i   libatk1.0-0                     - The ATK accessibility toolkit             
i   libatm1                         - shared library for ATM (Asynchronous Trans
i A libattica0                      - a Qt library that implements the Open Coll
i   libattr1                        - Extended attribute shared library         
i   libaudio2                       - Network Audio System - shared libraries   
i A libaudiofile0                   - Open-source version of SGI's audiofile lib
i   libavahi-client3                - Avahi client library                      
i   libavahi-common-data            - Avahi common data files                   
i   libavahi-common3                - Avahi common library                      
i   libavahi-core6                  - Avahi's embeddable mDNS/DNS-SD library    
i A libavahi-glib1                  - Avahi glib integration library            
i A libavc1394-0                    - control IEEE 1394 audio/video devices     
i A libavcodec-extra-52             - ffmpeg codec library                      
i   libavcodec-unstripped-52        - ffmpeg utility library - transitional pack
i A libavdevice52                   - ffmpeg device handling library            
i A libavfilter0                    - ffmpeg video filtering library            
i A libavformat52                   - ffmpeg file format library                
i A libavutil-extra-49              - ffmpeg utility library                    
i A libbind9-60                     - BIND9 Shared Library used by BIND         
i A libblas3gf                      - Basic Linear Algebra Subroutines 3, shared
i   libblkid1                       - block device id library                   
i A libboost-program-options1.40.0  - program options library for C++           
i   libbrlapi0.5                    - braille display access via BRLTTY - shared
i   libbsd0                         - utility functions from BSD systems - share
i   libbz2-1.0                      - high-quality block-sorting file compressor
i   libc-bin                        - Embedded GNU C Library: Binaries          
i   libc6                           - Embedded GNU C Library: Shared libraries  
i   libc6-i686                      - GNU C Library: Shared libraries [i686 opti
i   libcaca0                        - colour ASCII art library                  
i A libcairo-perl                   - Perl interface to the Cairo graphics libra
i   libcairo2                       - The Cairo 2D vector graphics library      
i A libcairomm-1.0-1                - C++ wrappers for Cairo (shared libraries) 
i A libcanberra-gtk0                - Gtk+ helper for playing widget event sound
i A libcanberra0                    - a simple abstract interface for playing ev
i   libcap2                         - support for getting/setting POSIX.1e capab
i A libcddb2                        - library to access CDDB data - runtime file
i A libcdio10                       - library to read and control CD-ROM        
i   libcdparanoia0                  - audio extraction tool for sampling CDs (li
i   libck-connector0                - ConsoleKit libraries                      
i   libclass-accessor-perl          - Perl module that automatically generates a
i   libclucene0ldbl                 - library for full-featured text search engi
i   libcolamd2.7.1                  - column approximate minimum degree ordering
i   libcomerr2                      - common error description library          
i   libcompress-bzip2-perl          - Perl interface to Bzip2 compression librar
i A libcroco3                       - a generic Cascading Style Sheet (CSS) pars
i   libcups2                        - Common UNIX Printing System(tm) - Core lib
i   libcupscgi1                     - Common UNIX Printing System(tm) - CGI libr
i   libcupsdriver1                  - Common UNIX Printing System(tm) - Driver l
i   libcupsimage2                   - Common UNIX Printing System(tm) - Raster i
i   libcupsmime1                    - Common UNIX Printing System(tm) - MIME lib
i   libcupsppdc1                    - Common UNIX Printing System(tm) - PPD mani
i   libcurl3-gnutls                 - Multi-protocol file transfer library (GnuT
i   libcwidget3                     - high-level terminal interface library for 
i   libdaemon0                      - lightweight C library for daemons - runtim
i   libdatrie1                      - Double-array trie library                 
i   libdb4.7                        - Berkeley v4.7 Database Libraries [runtime]
i A libdb4.8                        - Berkeley v4.8 Database Libraries [runtime]
i   libdbus-1-3                     - simple interprocess messaging system      
i   libdbus-glib-1-2                - simple interprocess messaging system (GLib
i A libdbusmenu-glib1               - Menus over DBus shared library for glib   
i A libdbusmenu-gtk1                - Menus over DBus shared library for GTK    
i A libdbusmenu-qt2                 - a Qt library that implements the DBusMenu 
i A libdc1394-22                    - high level programming interface for IEEE1
i A libdca0                         - decoding library for DTS Coherent Acoustic
i   libdevmapper1.02.1              - The Linux Kernel Device Mapper userspace l
i A libdirac-encoder0               - open and royalty free high quality codec -
i   libdirectfb-1.2-0               - direct frame buffer graphics - shared libr
i   libdjvulibre-text               - Linguistic support files for libdjvulibre 
i   libdjvulibre21                  - Runtime support for the DjVu image format 
i A libdns64                        - DNS Shared Library used by BIND           
i   libdrm-intel1                   - Userspace interface to intel-specific kern
i A libdrm-nouveau1                 - Userspace interface to nouveau-specific ke
i   libdrm-radeon1                  - Userspace interface to radeon-specific ker
i   libdrm2                         - Userspace interface to kernel DRM services
i A libdv4                          - software library for DV format digital vid
i A libdvbpsi5                      - library for MPEG TS and DVB PSI tables dec
i   libdvdcss2                      - Simple foundation for reading DVDs - runti
i   libdvdnav4                      - DVD navigation library                    
i   libdvdread4                     - library for reading DVDs                  
i A libebml0                        - access library for the EBML format        
i   libedit2                        - BSD editline and history libraries        
i   libeggdbus-1-0                  - D-Bus bindings for GObject                
i   libelf1                         - library to read and write ELF files       
i A libenca0                        - Extremely Naive Charset Analyser - shared 
i   libenchant1c2a                  - a wrapper library for various spell checke
i   libept0                         - High-level library for managing Debian pac
i   libepub0                        - library and tools to work with the EPub fi
i A libesd0                         - Enlightened Sound Daemon - Shared librarie
i A libexempi3                      - library to parse XMP metadata (Library)   
i   libexif12                       - library to parse EXIF files               
i A libexiv2-6                      - EXIF/IPTC metadata manipulation library   
i   libexpat1                       - XML parsing C library - runtime library   
i A libfaac0                        - an AAC audio encoder - library files      
i A libfaad2                        - freeware Advanced Audio Decoder - runtime 
i A libfam0                         - Client library to control the FAM daemon  
i   libffi5                         - Foreign Function Interface library runtime
i   libfftw3-3                      - library for computing Fast Fourier Transfo
i A libfile-copy-recursive-perl     - Perl extension for recursively copying fil
i   libflac++6                      - Free Lossless Audio Codec - C++ runtime li
i   libflac8                        - Free Lossless Audio Codec - runtime C libr
i   libfont-afm-perl                - Font::AFM - Interface to Adobe Font Metric
i   libfontconfig1                  - generic font configuration library - runti
i   libfontenc1                     - X11 font encoding library                 
i   libfreetype6                    - FreeType 2 font engine, shared library fil
i   libfribidi0                     - Free Implementation of the Unicode BiDi al
i   libfs6                          - X11 Font Services library                 
i   libfuse2                        - Filesystem in USErspace library           
i   libgadu3                        - Gadu-Gadu protocol library - runtime files
i A libgail18                       - GNOME Accessibility Implementation Library
i   libgc1c2                        - conservative garbage collector for C and C
i   libgcc1                         - GCC support library                       
i A libgconf2-4                     - GNOME configuration database system (share
i A libgcr0                         - Library for Crypto UI related task - runti
i   libgcrypt11                     - LGPL Crypto library - runtime library     
i   libgd2-noxpm                    - GD Graphics Library version 2 (without XPM
i   libgdbm3                        - GNU dbm database routines (runtime version
i A libgdu0                         - GObject based Disk Utility Library        
i   libgeoip1                       - A non-DNS IP-to-country resolver library  
i A libgfortran3                    - Runtime library for GNU Fortran applicatio
i   libgif4                         - library for GIF images (library)          
i   libgl1-mesa-dri                 - A free implementation of the OpenGL API --
i   libgl1-mesa-glx                 - A free implementation of the OpenGL API --
i A libglade2-0                     - library to load .glade files at runtime   
i A libglademm-2.4-1c2a             - C++ wrappers for libglade2 (shared library
i A libglib-perl                    - Perl interface to the GLib and GObject lib
i   libglib2.0-0                    - The GLib library of C routines            
i   libglib2.0-data                 - Common files for GLib library             
i A libglibmm-2.4-1c2a              - C++ wrapper for the GLib toolkit (shared l
i   libglu1-mesa                    - The OpenGL utility library (GLU)          
i   libgmp3c2                       - Multiprecision arithmetic library         
i A libgnome-desktop-2-17           - Utility library for loading .desktop files
i A libgnome-keyring0               - GNOME keyring services library            
i A libgnomevfs2-0                  - GNOME Virtual File System (runtime librari
i A libgnomevfs2-common             - GNOME Virtual File System (common files)  
i   libgnutls26                     - the GNU TLS library - runtime library     
i   libgomp1                        - GCC OpenMP (GOMP) support library         
i A libgp11-0                       - Glib wrapper library for PKCS#11 - runtime
i   libgpg-error0                   - library for common error values and messag
i   libgpgme11                      - GPGME - GnuPG Made Easy                   
i   libgphoto2-2                    - gphoto2 digital camera library            
i   libgphoto2-port0                - gphoto2 digital camera port library       
i   libgpm2                         - General Purpose Mouse - shared library    
i A libgraphite3                    - SILGraphite - a "smart font" rendering eng
i   libgraphviz4                    - rich set of graph drawing tools           
i   libgs8                          - The Ghostscript PostScript/PDF interpreter
i A libgsf-1-114                    - Structured File Library - runtime version 
i A libgsf-1-common                 - Structured File Library - common files    
i   libgsl0ldbl                     - GNU Scientific Library (GSL) -- library pa
i A libgsm1                         - Shared libraries for GSM speech compressor
i   libgssapi-krb5-2                - MIT Kerberos runtime libraries - krb5 GSS-
i   libgstreamer-plugins-base0.10-0 - GStreamer libraries from the "base" set   
i   libgstreamer0.10-0              - Core GStreamer libraries and elements     
i A libgtk2-perl                    - Perl interface to the 2.x series of the Gi
i   libgtk2.0-0                     - The GTK+ graphical user interface library 
i   libgtk2.0-bin                   - The programs for the GTK+ graphical user i
i   libgtk2.0-common                - Common files for the GTK+ graphical user i
i A libgtkmm-2.4-1c2a               - C++ wrappers for GTK+ (shared libraries)  
i A libgtkspell0                    - a spell-checking addon for GTK's TextView 
i   libgudev-1.0-0                  - GObject-based wrapper library for libudev 
i A libgvfscommon0                  - userspace virtual filesystem - library    
i   libhal-storage1                 - Hardware Abstraction Layer - shared librar
i   libhal1                         - Hardware Abstraction Layer - shared librar
i   libhtml-format-perl             - format HTML syntax trees into text, PostSc
i   libhtml-parser-perl             - collection of modules that parse HTML text
i   libhtml-tagset-perl             - Data tables pertaining to HTML            
i   libhtml-tokeparser-simple-perl  - Perl module used to tokenize HTML document
i   libhtml-tree-perl               - represent and create HTML syntax trees    
i   libhttp-response-encoding-perl  - set of encoding() methods for HTTP::Respon
i A libhttp-server-simple-perl      - simple stand-alone HTTP server            
i   libhunspell-1.2-0               - spell checker and morphological analyzer (
i   libhyphen0                      - ALTLinux hyphenation library - shared libr
i   libical0                        - iCalendar library implementation in C (run
i   libice6                         - X11 Inter-Client Exchange library         
i A libicu42                        - International Components for Unicode      
i A libid3tag0                      - ID3 tag reading library from the MAD proje
i A libidl0                         - library for parsing CORBA IDL files       
i   libidn11                        - GNU Libidn library, implementation of IETF
i   libieee1284-3                   - cross-platform library for parallel port a
i   libijs-0.35                     - IJS raster image transport protocol: share
i   libilmbase6                     - several utility libraries from ILM used by
i   libindicate-qt0                 - Qt bindings for libindicate               
i A libindicate4                    - GNOME panel indicator applet - shared libr
i A libindicator0                   - GNOME panel indicator applet - shared libr
i   libio-string-perl               - Emulate IO::File interface for in-core str
i A libiodbc2                       - iODBC Driver Manager                      
i A libisc60                        - ISC Shared Library used by BIND           
i A libisccc60                      - Command Channel Library used by BIND      
i A libisccfg60                     - Config File Handling Library used by BIND 
i A libiso9660-7                    - library to work with ISO9660 filesystems  
i A libjack0                        - JACK Audio Connection Kit (libraries)     
i   libjasper1                      - The JasPer JPEG-2000 runtime library      
i   libjline-java                   - Java library for handling console input   
i   libjpeg-progs                   - Programs for manipulating JPEG files      
i   libjpeg62                       - The Independent JPEG Group's JPEG runtime 
i A libjson-glib-1.0-0              - GLib JSON manipulation library            
i   libk3b6                         - The KDE CD/DVD burning application library
i   libk3b6-extracodecs             - The KDE CD/DVD burning application library
i   libk5crypto3                    - MIT Kerberos runtime libraries - Crypto Li
i   libkcddb4                       - CDDB library for KDE 4 (runtime)          
i   libkdecorations4                - library used by decorations for the KDE 4 
i A libkdegames5                    - libraries and common files for KDE games  
i A libkephal4                      - API for easier handling of multihead syste
i A libkexiv2-8                     - Qt like interface for the libexiv2 library
i   libkeyutils1                    - Linux Key Management Utilities (library)  
i A libkfontinst4                   - Libraries for font installation in kcontro
i   libklibc                        - minimal libc subset for use with initramfs
i   libkonq5                        - core libraries for Konqueror              
i   libkonq5-templates              - data files for the Konqueror libraries    
i   libkonqsidebarplugin4           - Konqueror sidebar plugin library          
i   libkpgp4                        - gpg based crypto library for KDE          
i   libkrb5-3                       - MIT Kerberos runtime libraries            
i   libkrb5support0                 - MIT Kerberos runtime libraries - Support l
i A libkscreensaver5                - Library of the KDE Screensaver system     
i A libksgrd4                       - Library for the ksysguard gui             
i   libksieve4                      - KDE mail/news message filtering library   
i A libksignalplotter4              - Library for ksysguard signal views        
i   libkwineffects1                 - library used by effects for the KDE 4 wind
i A libkworkspace4                  - Library for the kdebase workspace         
i   liblancelot0                    - library that contains all UI widgets and l
i A liblapack3gf                    - library of linear algebra routines 3 - sha
i   liblastfm0                      - The Last.fm web services library          
i A liblaunchpad-integration1       - library for launchpad integration         
i   liblcms1                        - Colour management library                 
i   libldap-2.4-2                   - OpenLDAP libraries                        
i A liblircclient0                  - infra-red remote control support - client 
i   liblocale-gettext-perl          - Using libc functions for internationalizat
i   liblockfile1                    - NFS-safe locking library, includes dotlock
i   libloudmouth1-0                 - Lightweight C Jabber library              
i A liblsofui4                      - Library for ksysguard based priority sched
i   libltdl7                        - A system independent dlopen wrapper for GN
i A liblua5.1-0                     - Simple, extensible, embeddable programming
i A liblwres60                      - Lightweight Resolver Library used by BIND 
i A liblzma1                        - XZ-format compression library             
i A liblzo2-2                       - data compression library                  
i A libmad0                         - MPEG audio decoder library                
i   libmagic1                       - File type determination library using "mag
i A libmagick++2                    - object-oriented C++ interface to ImageMagi
i   libmagickcore2                  - low-level image manipulation library      
i A libmagickcore2-extra            - low-level image manipulation library - ext
i   libmagickwand2                  - image manipulation library                
i   libmailtools-perl               - Manipulate email in perl programs         
i A libmatroska0                    - extensible open standard audio/video conta
i   libmeanwhile1                   - open implementation of the Lotus Sametime 
i   libmimelib4                     - KDE mime library                          
i A libmjpegtools-1.9               - MJPEG video capture/editting/playback MPEG
i   libmng1                         - Multiple-image Network Graphics library   
i   libmodplug0c2                   - shared libraries for mod music based on Mo
i   libmp3lame0                     - An MP3 encoding library                   
i   libmp4v2-0                      - freeware Advanced Audio Decoder - runtime 
i   libmpcdec3                      - Musepack (MPC) format library             
i A libmpeg2-4                      - MPEG1 and MPEG2 video decoder library     
i   libmpfr1ldbl                    - multiple precision floating-point computat
i   libmtp8                         - Media Transfer Protocol (MTP) library     
i   libmusicbrainz4c2a              - Second generation incarnation of the CD In
i   libmysqlclient16                - MySQL database client library             
i A libnautilus-extension1          - libraries for nautilus components - runtim
i   libncurses5                     - shared libraries for terminal handling    
i   libncursesw5                    - shared libraries for terminal handling (wi
i   libneon27-gnutls                - An HTTP and WebDAV client library (GnuTLS 
i   libnewt0.52                     - Not Erik's Windowing Toolkit - text mode w
i A libnih-dbus1                    - NIH D-Bus Bindings Library                
i A libnih1                         - NIH Utility Library                       
i   libnl1                          - library for dealing with netlink sockets  
i   libnm-glib2                     - network management framework (GLib shared 
i   libnm-util1                     - network management framework (shared libra
i A libnotify1                      - sends desktop notifications to a notificat
i   libnspr4-0d                     - NetScape Portable Runtime Library         
i   libnss-mdns                     - NSS module for Multicast DNS name resoluti
i   libnss3-1d                      - Network Security Service libraries        
i   libogg0                         - Ogg bitstream library                     
i A liboil0.3                       - Library of Optimised Inner Loops          
i   libokularcore1                  - libraries for the Okular document viewer  
i A libopenal1                      - Software implementation of the OpenAL API 
i A libopencore-amrnb0              - Adaptive Multi Rate speech codec - shared 
i A libopencore-amrwb0              - Adaptive Multi-Rate - Wideband speech code
i   libopenexr6                     - runtime files for the OpenEXR image librar
i A libopenjpeg2                    - JPEG 2000 image compression/decompression 
i   libopenobex1                    - OBEX protocol library                     
i A liborbit2                       - libraries for ORBit2 - a CORBA ORB        
i   libotr2                         - Off-the-Record Messaging library          
i   libpam-ck-connector             - ConsoleKit PAM module                     
i   libpam-modules                  - Pluggable Authentication Modules for PAM  
i   libpam-runtime                  - Runtime support for the PAM library       
i   libpam0g                        - Pluggable Authentication Modules library  
i A libpango-perl                   - Perl module to layout and render internati
i   libpango1.0-0                   - Layout and rendering of internationalised 
i   libpango1.0-common              - Modules and configuration files for the Pa
i A libpangomm-1.4-1                - C++ Wrapper for pango (shared libraries)  
i   libpaper1                       - library for handling paper characteristics
i   libparse-debianchangelog-perl   - parse Debian changelogs and output them in
i A libparted0debian1               - The GNU Parted disk partitioning shared li
i   libpcap0.8                      - system interface for user-level packet cap
i   libpci3                         - Linux PCI Utilities (shared library)      
i   libpciaccess0                   - Generic PCI access library for X          
i   libpcre3                        - Perl 5 Compatible Regular Expression Libra
i   libpcsclite1                    - Middleware to access a smart card using PC
i   libperl5.10                     - shared Perl library                       
i   libphonon4                      - Qt 4 Phonon module                        
i   libpixman-1-0                   - pixel-manipulation library for X and cairo
i A libplasma-applet-system-monitor - Library for the plasma system monitor     
i A libplasma-geolocation-interface - Library for the plasma geolocation        
i   libplasma3                      - library for the KDE 4 Plasma desktop      
i A libplasmaclock4                 - Library for the plasma clock              
i A libplasmagenericshell4          - shared elements for all the plasma shells 
i A libplymouth2                    - graphical boot animation and logger - shar
i   libpng12-0                      - PNG library - runtime                     
i A libpolkit-agent-1-0             - PolicyKit Authentication Agent API        
i   libpolkit-backend-1-0           - PolicyKit backend API                     
i   libpolkit-dbus2                 - library for accessing PolicyKit via D-Bus 
i   libpolkit-gobject-1-0           - PolicyKit Authorization API               
i   libpolkit-grant2                - library for obtaining privileges via Polic
i A libpolkit-qt-1-0                - PolicyKit-qt-1 library                    
i   libpolkit2                      - library for accessing PolicyKit           
i A libpoppler-glib4                - PDF rendering library (GLib-based shared l
i   libpoppler-qt4-3                - PDF rendering library (Qt 4 based shared l
i   libpoppler5                     - PDF rendering library                     
i   libpopt0                        - lib for parsing cmdline parameters        
i A libpostproc51                   - ffmpeg video postprocessing library       
i   libpq5                          - PostgreSQL C client library               
i A libprocesscore4                 - Library for ksysguard based process view  
i A libprocessui4                   - Library for ksysguard process user interfa
i   libpth20                        - The GNU Portable Threads                  
i A libpulse-browse0                - PulseAudio client libraries (zeroconf supp
i A libpulse-mainloop-glib0         - PulseAudio client libraries (glib support)
i   libpulse0                       - PulseAudio client libraries               
i   libpython2.6                    - Shared Python runtime library (version 2.6
i   libqca2                         - libraries for the Qt Cryptographic Archite
i   libqca2-plugin-ossl             - QCA OSSL plugin for libqca2               
i   libqimageblitz4                 - QImageBlitz image effects library         
i   libqscintilla2-5                - The Qt4 port of the Scintilla source code 
i   libqt4-assistant                - Qt 4 assistant module                     
i   libqt4-dbus                     - Qt 4 D-Bus module                         
i   libqt4-designer                 - Qt 4 designer module                      
i   libqt4-help                     - Qt 4 help module                          
i A libqt4-multimedia               - Qt 4 Multimedia module                    
i   libqt4-network                  - Qt 4 network module                       
i   libqt4-opengl                   - Qt 4 OpenGL module                        
i   libqt4-phonon                   - transitional package for Qt 4 Phonon libra
i   libqt4-qt3support               - Qt 3 compatibility library for Qt 4       
i   libqt4-ruby1.8                  - Qt 4 bindings for Ruby                    
i   libqt4-script                   - Qt 4 script module                        
i   libqt4-scripttools              - Qt 4 script tools module                  
i   libqt4-sql                      - Qt 4 SQL module                           
i   libqt4-sql-mysql                - Qt 4 MySQL database driver                
i   libqt4-sql-sqlite               - Qt 4 SQLite 3 database driver             
i   libqt4-svg                      - Qt 4 SVG module                           
i   libqt4-test                     - Qt 4 test module                          
i   libqt4-webkit                   - Qt 4 WebKit module                        
i   libqt4-xml                      - Qt 4 XML module                           
i   libqt4-xmlpatterns              - Qt 4 XML patterns module                  
i   libqtcore4                      - Qt 4 core module                          
i   libqtgui4                       - Qt 4 GUI module                           
i A libqtruby4shared2               - internal library for Qt 4 Ruby bindings   
i   libqtscript4-core               - Qt Script bindings for the Qt 4 Core libra
i   libqtscript4-gui                - Qt Script bindings for the Qt 4 Gui librar
i   libqtscript4-network            - Qt Script bindings for the Qt 4 Network li
i   libqtscript4-sql                - Qt Script bindings for the Qt 4 SQL librar
i   libqtscript4-uitools            - Qt Script bindings for the Qt 4 UiTools li
i   libqtscript4-xml                - Qt Script bindings for the Qt 4 XML librar
i A libquicktime1                   - library for reading and writing Quicktime 
i   libraptor1                      - Raptor RDF parser and serialiser library  
i A librasqal2                      - Rasqal RDF query library                  
i A libraw1394-11                   - library for direct access to IEEE 1394 bus
i   librdf0                         - Redland Resource Description Framework (RD
i   libreadline6                    - GNU readline and history libraries, run-ti
i   librpc-xml-perl                 - Perl module implementation of XML-RPC     
i A librsvg2-2                      - SAX-based renderer library for SVG files (
i A librsvg2-common                 - SAX-based renderer library for SVG files (
i   libruby1.8                      - Libraries necessary to run Ruby 1.8       
i   libsamplerate0                  - Audio sample rate conversion library      
i   libsasl2-2                      - Cyrus SASL - authentication abstraction li
i   libsasl2-modules                - Cyrus SASL - pluggable authentication modu
i A libschroedinger-1.0-0           - library for encoding/decoding of Dirac vid
i   libscim8c2a                     - library for SCIM platform                 
i A libsdl-image1.2                 - image loading library for Simple DirectMed
i   libsdl1.2debian                 - Simple DirectMedia Layer                  
i   libsdl1.2debian-alsa            - Simple DirectMedia Layer (with X11 and ALS
i   libselinux1                     - SELinux runtime shared libraries          
i   libsensors3                     - library to read temperature/voltage/fan se
i   libsepol1                       - SELinux library for manipulating binary se
i A libsexy2                        - collection of additional GTK+ widgets - li
i   libsgutils2-2                   - utilities for working with generic SCSI de
i A libshout3                       - MP3/Ogg Vorbis broadcast streaming library
i A libsidplay1                     - SID (MOS 6581) emulation library          
i   libsigc++-2.0-0c2a              - type-safe Signal Framework for C++ - runti
i   libslang2                       - The S-Lang programming library - runtime v
i   libslp1                         - OpenSLP libraries                         
i   libsm6                          - X11 Session Management library            
i A libsmbclient                    - shared library for communication with SMB/
i A libsmokeqt4-3                   - Qt 4 Smoke libraries                      
i A libsmokesoprano3                - Soprano Smoke library                     
i   libsndfile1                     - Library for reading/writing audio files   
i A libsolidcontrol4                - Library for solid based network management
i A libsolidcontrolifaces4          - Library for solid based network interface 
i   libsoprano4                     - libraries for the Soprano RDF framework   
i   libspectre1                     - Library for rendering PostScript documents
i   libspeex1                       - The Speex codec runtime library           
i A libspeexdsp1                    - The Speex extended runtime library        
i   libsqlite3-0                    - SQLite 3 shared library                   
i   libss2                          - command-line interface parsing library    
i A libssh-4                        - A tiny C SSH library                      
i   libssl0.9.8                     - SSL shared libraries                      
i A libstartup-notification0        - library for program launch feedback (share
i   libstdc++6                      - The GNU Standard C++ Library v3           
i   libstlport4.6ldbl               - STLport C++ class library                 
i   libstreamanalyzer0              - streamanalyzer library for Strigi Desktop 
i   libstreams0                     - streams library for for Strigi Desktop Sea
i   libsub-name-perl                - Assigns a new name to referenced sub      
i A libsvga1                        - console SVGA display libraries            
i A libswscale0                     - ffmpeg video scaling library              
i   libsysfs2                       - interface library to sysfs                
i   libtag-extras1                  - TagLib extras library - support for more f
i   libtag1-vanilla                 - TagLib Audio Meta-Data Library (Vanilla fl
i   libtag1c2a                      - TagLib Audio Meta-Data Library            
i A libtalloc2                      - hierarchical pool based memory allocator  
i A libtar                          - C library for manipulating tar archives   
i A libtaskmanager4                 - Library which provides task management fac
i   libtasn1-3                      - Manage ASN.1 structures (runtime)         
i A libtdb1                         - Trivial Database - shared library         
i   libterm-readkey-perl            - A perl module for simple terminal control 
i   libtext-charwidth-perl          - get display widths of characters on the te
i   libtext-iconv-perl              - converts between character sets in Perl   
i   libtext-wrapi18n-perl           - internationalised substitute of Text::Wrap
i   libthai-data                    - Data files for Thai language support libra
i   libthai0                        - Thai language support library             
i   libtheora0                      - The Theora Video Compression Codec        
i   libtidy-0.99-0                  - HTML syntax checker and reformatter - libr
i   libtiff4                        - Tag Image File Format (TIFF) library      
i   libtimedate-perl                - Time and date functions for Perl          
i   libts-0.0-0                     - touch screen library                      
i A libtwolame0                     - MPEG Audio Layer 2 encoding library       
i   libudev0                        - udev library                              
i A libunique-1.0-0                 - Library for writing single instance applic
i A libupnp3                        - Portable SDK for UPnP Devices, version 1.6
i   liburi-perl                     - module to manipulate and access URI string
i   libusb-0.1-4                    - userspace USB programming library         
i A libusb-1.0-0                    - userspace USB programming library         
i   libuuid1                        - Universally Unique ID library             
i   libv4l-0                        - Collection of video4linux support librarie
i A libvcdinfo0                     - library to extract information from VideoC
i A libvlc2                         - multimedia player and streamer library    
i A libvlccore2                     - base library for VLC and its modules      
i   libvncserver0                   - API to write one's own vnc server         
i   libvorbis0a                     - The Vorbis General Audio Compression Codec
i   libvorbisenc2                   - The Vorbis General Audio Compression Codec
i   libvorbisfile3                  - The Vorbis General Audio Compression Codec
i   libwavpack1                     - an audio codec (lossy and lossless) - libr
i A libwbclient0                    - Samba winbind client library              
i A libweather-ion4                 - Library which provides an interface for we
i A libwmf-bin                      - Windows metafile conversion tools         
i   libwmf0.2-7                     - Windows metafile conversion library       
i A libwnck-common                  - Window Navigator Construction Kit - common
i A libwnck22                       - Window Navigator Construction Kit - runtim
i   libwpd8c2a                      - Library for handling WordPerfect documents
i   libwpg-0.1-1                    - WordPerfect graphics import/convert librar
i   libwps-0.1-1                    - Works text file format import filter libra
i   libwrap0                        - Wietse Venema's TCP wrappers library      
i   libwww-mechanize-perl           - module to automate interaction with websit
i   libwww-perl                     - Perl HTTP/WWW client/server library       
i   libx11-6                        - X11 client-side library                   
i   libx11-data                     - X11 client-side library                   
i A libx264-85                      - x264 video coding library                 
i   libx86-1                        - x86 real-mode library                     
i   libxapian15                     - Search engine library                     
i   libxau6                         - X11 authorisation library                 
i   libxaw7                         - X11 Athena Widget library                 
i A libxcb-atom1                    - utility libraries for X C Binding -- atom 
i A libxcb-aux0                     - utility libraries for X C Binding -- aux  
i A libxcb-event1                   - utility libraries for X C Binding -- event
i A libxcb-keysyms1                 - utility libraries for X C Binding -- keysy
i   libxcb-render-util0             - utility libraries for X C Binding -- rende
i   libxcb-render0                  - X C Binding, render extension             
i   libxcb-shape0                   - X C Binding, shape extension              
i   libxcb-shm0                     - X C Binding, shm extension                
i   libxcb-xv0                      - X C Binding, xv extension                 
i   libxcb1                         - X C Binding                               
i   libxcomposite1                  - X11 Composite extension library           
i   libxcursor1                     - X cursor management library               
i   libxdamage1                     - X11 damaged region extension library      
i   libxdmcp6                       - X11 Display Manager Control Protocol libra
i   libxext6                        - X11 miscellaneous extension library       
i   libxfixes3                      - X11 miscellaneous 'fixes' extension librar
i   libxfont1                       - X11 font rasterisation library            
i   libxft2                         - FreeType-based font drawing library for X 
i   libxi6                          - X11 Input extension library               
i   libxine1                        - the xine video/media player library, meta-
i   libxine1-bin                    - the xine video/media player library, binar
i   libxine1-console                - libaa/libcaca/framebuffer/directfb related
i   libxine1-ffmpeg                 - MPEG-related plugins for libxine1         
i   libxine1-misc-plugins           - Input, audio output and post plugins for l
i   libxine1-x                      - X desktop video output plugins for libxine
i   libxinerama1                    - X11 Xinerama extension library            
i   libxkbfile1                     - X11 keyboard file manipulation library    
i A libxklavier16                   - X Keyboard Extension high-level API       
i A libxml-libxml-perl              - Perl interface to the libxml2 library     
i A libxml-namespacesupport-perl    - Perl module for supporting simple generic 
i   libxml-parser-perl              - Perl module for parsing XML files         
i A libxml-sax-perl                 - Perl module for using and building Perl SA
i   libxml2                         - GNOME XML library                         
i   libxml2-utils                   - XML utilities                             
i   libxmu6                         - X11 miscellaneous utility library         
i   libxmuu1                        - X11 miscellaneous micro-utility library   
i   libxp6                          - X Printing Extension (Xprint) client libra
i   libxpm4                         - X11 pixmap library                        
i   libxrandr2                      - X11 RandR extension library               
i   libxrender1                     - X Rendering Extension client library      
i A libxres1                        - X11 Resource extension library            
i   libxslt1.1                      - XSLT processing library - runtime library 
i   libxss1                         - X11 Screen Saver extension library        
i   libxt6                          - X11 toolkit intrinsics library            
i   libxtst6                        - X11 Testing -- Resource extension library 
i   libxv1                          - X11 Video extension library               
i A libxvidcore4                    - An open source MPEG-4 video codec (library
i   libxvmc1                        - X11 Video extension library               
i   libxxf86dga1                    - X11 Direct Graphics Access extension libra
i   libxxf86misc1                   - X11 XFree86 miscellaneous extension librar
i   libxxf86vm1                     - X11 XFree86 video mode extension library  
i   libzip1                         - library for reading, creating, and modifyi
i   links2                          - Web browser running in both graphics and t
i   linux-firmware                  - Firmware for Linux kernel drivers         
i   linux-generic                   - Complete Generic Linux kernel             
i A linux-headers-2.6.32-22         - Header files related to Linux kernel versi
i A linux-headers-2.6.32-22-generic - Linux kernel headers for version 2.6.32 on
i   linux-headers-generic           - Generic Linux kernel headers              
i   linux-image-2.6.32-22-generic   - Linux kernel image for version 2.6.32 on x
i   linux-image-generic             - Generic Linux kernel image                
i   linux-libc-dev                  - Linux Kernel Headers for development      
i   linux-sound-base                - base package for ALSA and OSS sound system
i   locales                         - common files for locale support           
i   lockfile-progs                  - Programs for locking and unlocking files a
i   login                           - system login tools                        
i   logrotate                       - Log rotation utility                      
i   lp-solve                        - Solve (mixed integer) linear programming p
i   lsb-base                        - Linux Standard Base 4.0 init script functi
i   lsb-release                     - Linux Standard Base version reporting util
i   lshw                            - information about hardware configuration  
i   lsof                            - List open files                           
i   ltrace                          - Tracks runtime library calls in dynamicall
i   lzma                            - Compression method of 7z format in 7-Zip p
i   make                            - An utility for Directing compilation.     
i   makedev                         - creates device files in /dev              
i   mawk                            - a pattern scanning and text processing lan
i   medibuntu-keyring               - GnuPG key of the Medibuntu repository     
i A menu                            - generates programs menu for all menu-aware
i   mesa-utils                      - Miscellaneous Mesa GL utilities           
i   mime-support                    - MIME files 'mime.types' & 'mailcap', and s
i   mlocate                         - quickly find files on the filesystem based
i   modemmanager                    - D-Bus service for managing modems         
i   module-init-tools               - tools for managing Linux kernel modules   
i   mount                           - Tools for mounting and manipulating filesy
i   mountall                        - filesystem mounting tool                  
i   mountmanager                    - User-friendly management of disks and part
i   mplayer                         - movie player for Unix-like systems        
i   myspell-en-gb                   - English_british dictionary for myspell    
i A mysql-client-core-5.1           - MySQL database core client binaries       
i   mysql-common                    - MySQL database common files (e.g. /etc/mys
i A mysql-server-core-5.1           - MySQL database core server files          
i   nano                            - small, friendly text editor inspired by Pi
i A nautilus                        - file manager and graphical shell for GNOME
i A nautilus-data                   - data files for nautilus                   
i   nautilus-dropbox                - Dropbox integration for Nautilus          
i   ncurses-base                    - basic terminal type definitions           
i   ncurses-bin                     - terminal-related programs and man pages   
i   net-tools                       - The NET-3 networking toolkit              
i   netbase                         - Basic TCP/IP networking system            
i   network-manager                 - network management framework daemon       
i A network-manager-pptp            - network management framework (PPTP plugin)
i A notification-daemon             - a daemon that displays passive pop-up noti
i   okular                          - document viewer for KDE 4                 
i   okular-extra-backends           - additional document format support for Oku
i A openjdk-6-jre                   - OpenJDK Java runtime, using Hotspot JIT   
i A openjdk-6-jre-headless          - OpenJDK Java runtime, using Hotspot JIT (h
i A openjdk-6-jre-lib               - OpenJDK Java runtime (architecture indepen
i   openoffice.org-base-core        - office productivity suite -- shared librar
i   openoffice.org-calc             - office productivity suite -- spreadsheet  
i   openoffice.org-common           - office productivity suite -- arch-independ
i   openoffice.org-core             - office productivity suite -- arch-dependen
i   openoffice.org-draw             - office productivity suite -- drawing      
i   openoffice.org-emailmerge       - office productivity suite -- email mail me
i   openoffice.org-hyphenation      - Hyphenation patterns for OpenOffice.org   
i   openoffice.org-impress          - office productivity suite -- presentation 
i   openoffice.org-java-common      - office productivity suite -- arch-independ
i   openoffice.org-kde              - office productivity suite -- KDE integrati
i A openoffice.org-l10n-common      - common files for OpenOffice.org language a
i   openoffice.org-l10n-en-gb       - office productivity suite -- English_briti
i   openoffice.org-math             - office productivity suite -- equation edit
i   openoffice.org-style-oxygen     - office productivity suite -- Oxygen symbol
i   openoffice.org-writer           - office productivity suite -- word processo
i   openssl                         - Secure Socket Layer (SSL) binary and relat
i   oss-compat                      - OSS compatibility package                 
i   oxygen-cursor-theme             - Oxygen Mouse Cursor Theme                 
i A oxygen-icon-theme               - Oxygen icon theme                         
i   parted                          - The GNU Parted disk partition resizing pro
i   passwd                          - change and administer password and group d
i   pavucontrol                     - PulseAudio Volume Control                 
i   pciutils                        - Linux PCI Utilities                       
i   perl                            - Larry Wall's Practical Extraction and Repo
i   perl-base                       - minimal Perl system                       
i   perl-modules                    - Core Perl modules                         
i A perlmagick                      - Perl interface to the ImageMagick graphics
i   phonon                          - Qt 4 Phonon module metapackage            
i   phonon-backend-xine             - Phonon Xine 1.1.x backend                 
i   plasma-dataengines-addons       - addons for KDE 4 Plasma - data engines    
i   plasma-dataengines-workspace    - KDE 4 base workspace Plasma data engines  
i   plasma-desktop                  - The KDE plasma workspace for desktop and l
i A plasma-scriptengine-javascript  - javascript script engine for Plasma       
i   plasma-widget-folderview        - Folder View Plasma widget                 
i   plasma-widgets-addons           - addons for KDE 4 Plasma - widgets         
i A plasma-widgets-workspace        - KDE 4 base workspace Plasma widgets and co
i A plymouth                        - graphical boot animation and logger - main
i A plymouth-theme-ubuntu-text      - graphical boot animation and logger - ubun
i   pngcrush                        - optimizes PNG (Portable Network Graphics) 
i   policykit-1                     - framework for managing administrative poli
i A policykit-1-gnome               - GNOME authentication agent for PolicyKit-1
i A polkit-kde-1                    - KDE dialogs for PolicyKit                 
i   ppp                             - Point-to-Point Protocol (PPP) - daemon    
i   pppconfig                       - A text menu based utility for configuring 
i   pppoeconf                       - configures PPPoE/ADSL connections         
i A pptp-linux                      - Point-to-Point Tunneling Protocol (PPTP) C
i   procps                          - /proc file system utilities               
i   psmisc                          - utilities that use the proc file system   
i   pulseaudio                      - PulseAudio sound server                   
i A pulseaudio-esound-compat        - PulseAudio ESD compatibility layer        
i A pulseaudio-module-x11           - X11 module for PulseAudio sound server    
i A pulseaudio-utils                - Command line tools for the PulseAudio soun
i   python                          - An interactive high-level object-oriented 
i   python-apport                   - apport crash report handling library      
i   python-apt                      - Python interface to libapt-pkg            
i A python-cairo                    - Python bindings for the Cairo vector graph
i   python-central                  - register and build utility for Python pack
i   python-cups                     - Python bindings for CUPS                  
i   python-cupshelpers              - Python modules for printer configuration w
i   python-dbus                     - simple interprocess messaging system (Pyth
i   python-debian                   - Python modules to work with Debian-related
i   python-gdbm                     - GNU dbm database support for Python       
i   python-gnupginterface           - Python interface to GnuPG (GPG)           
i   python-gobject                  - Python bindings for the GObject library   
i A python-gtk2                     - Python bindings for the GTK+ widget set   
i   python-httplib2                 - comprehensive HTTP client library written 
i   python-imaging                  - Python Imaging Library                    
i   python-kde4                     - Python bindings for the KDE 4 libraries   
i   python-launchpadlib             - Launchpad web services client library     
i A python-lazr.restfulclient       - client for lazr.restful-based web services
i A python-lazr.uri                 - library for parsing, manipulating, and gen
i A python-lxml                     - pythonic binding for the libxml2 and libxs
i   python-minimal                  - A minimal subset of the Python language (d
i   python-newt                     - A NEWT module for Python                  
i A python-numpy                    - Numerical Python adds a fast array facilit
i   python-oauth                    - implementation of the OAuth protocol      
i   python-packagekit               - PackageKit Python bindings                
i   python-pkg-resources            - Package Discovery and Resource Access usin
i   python-problem-report           - Python library to handle problem reports  
i   python-qt4                      - Python bindings for Qt4                   
i   python-qt4-dbus                 - DBus Support for PyQt4                    
i A python-renderpm                 - python low level render interface         
i A python-reportlab                - ReportLab library to create PDF documents 
i A python-reportlab-accel          - C coded extension accelerator for the Repo
i   python-simplejson               - Simple, fast, extensible JSON encoder/deco
i A python-sip                      - Python/C++ bindings generator runtime libr
i   python-sip4                     - Python/C++ bindings generator runtime libr
i   python-smbc                     - Python bindings for Samba clients (libsmbc
i   python-support                  - automated rebuilding support for Python mo
i A python-uniconvertor             - Universal vector graphics translator      
i   python-uno                      - Python-UNO bridge                         
i   python-wadllib                  - Python library for navigating WADL files  
i   python-xapian                   - Xapian search engine interface for Python 
i   python-xdg                      - Python library to access freedesktop.org s
i   python-xkit                     - library for the manipulation of the xorg.c
i   python-zope.interface           - Interfaces for Python                     
i   python2.6                       - An interactive high-level object-oriented 
i   python2.6-minimal               - A minimal subset of the Python language (v
i   readline-common                 - GNU readline and history libraries, common
i   rsync                           - fast remote file copy program (like rcp)  
i   rsyslog                         - enhanced multi-threaded syslogd           
i A rtkit                           - Realtime Policy and Watchdog Daemon       
i   ruby                            - An interpreter of object-oriented scriptin
i   ruby1.8                         - Interpreter of object-oriented scripting l
i   sed                             - The GNU sed stream editor                 
i A sensible-utils                  - Utilities for sensible alternative selecti
i   sgml-base                       - SGML infrastructure and SGML catalog file 
i A shared-desktop-ontologies       - shared ontologies for semantic searching  
i   shared-mime-info                - FreeDesktop.org shared MIME database and s
i   softbeep                        - System bell replacement                   
i   soprano-daemon                  - daemon for the Soprano RDF framework      
i   ssl-cert                        - simple debconf wrapper for OpenSSL        
i   sudo                            - Provide limited super user privileges to s
i   systemsettings                  - KDE 4 System Settings                     
i   sysv-rc                         - System-V-like runlevel change mechanism   
i   sysvinit-utils                  - System-V-like utilities                   
i   tar                             - GNU version of the tar archiving utility  
i   tasksel                         - Tool for selecting tasks for installation 
i   tasksel-data                    - Official tasks used for installation of De
i   tcpd                            - Wietse Venema's TCP wrapper utilities     
i   tcpdump                         - A powerful tool for network monitoring and
i   telnet                          - The telnet client                         
i A thunderbird                     - mail/news client with RSS and integrated s
i   thunderbird-locale-en-gb        - Thunderbird English language/region packag
i   time                            - The GNU time program for measuring cpu res
i   tsconf                          - touch screen library common files         
i   ttf-dejavu                      - Metapackage to pull in ttf-dejavu-core and
i   ttf-dejavu-core                 - Vera font family derivate with additional 
i   ttf-dejavu-extra                - Vera font family derivate with additional 
i   ttf-freefont                    - Freefont Serif, Sans and Mono Truetype fon
i   ttf-opensymbol                  - OpenSymbol TrueType font                  
i   tzdata                          - time zone and daylight-saving time data   
i A tzdata-java                     - time zone and daylight-saving time data fo
i   ubuntu-keyring                  - GnuPG keys of the Ubuntu archive          
i   ucf                             - Update Configuration File: preserve user c
i   udev                            - rule-based device node and kernel event ma
i A udisks                          - abstraction for enumerating block devices 
i   ufw                             - program for managing a Netfilter firewall 
i   uno-libs3                       - OpenOffice.org UNO runtime environment -- 
i   unrar                           - Unarchiver for .rar files (non-free versio
i   unzip                           - De-archiver for .zip files                
i   update-inetd                    - inetd configuration file updater          
i   update-manager-core             - manage release upgrades                   
i   update-manager-kde              - Support modules for Update Notifier KDE   
i   update-notifier-common          - Files shared between update-notifier and a
i   update-notifier-kde             - Apt status applet                         
i   upstart                         - event-based init daemon                   
i   ure                             - OpenOffice.org UNO runtime environment    
i   usbutils                        - Linux USB utilities                       
i   userconfig                      - user and group setup tool for KDE         
i   util-linux                      - Miscellaneous system utilities            
i   uuid-runtime                    - runtime components for the Universally Uni
i   vlc                             - multimedia player and streamer            
i A vlc-data                        - Common data for VLC                       
i A vlc-nox                         - multimedia player and streamer (without X 
i A vlc-plugin-pulse                - PulseAudio plugin for VLC                 
i   w32codecs                       - win32 binary codecs                       
i   wbritish                        - British English dictionary words for /usr/
i   wget                            - retrieves files from the web              
i   whiptail                        - Displays user-friendly dialog boxes from s
i A wireless-crda                   - Wireless Central Regulatory Domain Agent  
i   wpasupplicant                   - client support for WPA and WPA2 (IEEE 802.
i   x-ttcidfont-conf                - TrueType and CID fonts configuration for X
i   x11-apps                        - X applications                            
i   x11-common                      - X Window System (X.Org) infrastructure    
i   x11-session-utils               - X session utilities                       
i   x11-utils                       - X11 utilities                             
i   x11-xfs-utils                   - X font server utilities                   
i   x11-xkb-utils                   - X11 XKB utilities                         
i   x11-xserver-utils               - X server utilities                        
i   xauth                           - X authentication utility                  
i   xbitmaps                        - Base X bitmaps                            
i   xcursor-themes                  - Base X cursor themes                      
i   xdg-user-dirs                   - tool to manage well known user directories
i   xdg-utils                       - desktop integration utilities from freedes
i   xfonts-100dpi                   - 100 dpi fonts for X                       
i   xfonts-75dpi                    - 75 dpi fonts for X                        
i   xfonts-base                     - standard fonts for X                      
i   xfonts-encodings                - Encodings for X.Org fonts                 
i   xfonts-mathml                   - Type1 Symbol font for MathML              
i   xfonts-scalable                 - scalable fonts for X                      
i   xfonts-utils                    - X Window System font utility programs     
i   xinit                           - X server initialisation tool              
i   xinput                          - Runtime configuration and test of XInput d
i   xkb-data                        - X Keyboard Extension (XKB) configuration d
i   xml-core                        - XML infrastructure and XML catalog file su
i   xorg                            - X.Org X Window System                     
i   xorg-docs-core                  - Core documentation for the X.org X Window 
i   xserver-common                  - common files used by various X servers    
i   xserver-xorg                    - the X.Org X server                        
i   xserver-xorg-core               - Xorg X server - core server               
i   xserver-xorg-input-evdev        - X.Org X server -- evdev input driver      
i   xserver-xorg-input-mouse        - X.Org X server -- mouse input driver      
i   xserver-xorg-input-vmmouse      - X.Org X server -- VMMouse input driver to 
i   xserver-xorg-video-fbdev        - X.Org X server -- fbdev display driver    
i   xserver-xorg-video-nouveau      - X.Org X server -- Nouveau display driver (
i   xterm                           - X terminal emulator                       
i A xulrunner-1.9.2                 - XUL + XPCOM application runner            
i   zip                             - Archiver for .zip files                   
i   zlib1g                          - compression library - runtime             


```

There are a few things like the fonts for MathML that I could manage without, also codecs for mplayer, I have nautilus and Gnome stuff only for dropbox. Mainly this machine is just for Firefox & Thunderbird.

---

### Post by acrazyplayer on 2010-05-29
You could remove openoffice to free up a lot of space, I like to do "sudo apt-get purge openoffice*" and then make sure it wont get rid of anything you don't want it to. Also I would recommend installing the newest flash player from Adobe. First uninstall your flash player you have right now and then type in "adobe flash 10.1" into your search engine of choice, download it, extract it and pop it into this directory "/home/"your user name here"/.mozilla/plugins" If "plugins" doesn't exist then simply make a folder called plugins and put the flash player file that you extracted into there. There are a few more things you could do but require more work and possibly make you regret it. 

Have you limited things from starting up when your computer boots?

---

### Post by madtownmike1 on 2010-05-29
You could also check the dpi your monitor is using for fonts and remove the font size that's not being used. Either package xfonts-100dpi or xfonts-75dpi. This will have no effect on what's running, but it will free up some disk space (about 4.5MB). Typically, 75dpi fonts are used for displays smaller than 1024x768, otherwise 100dpi is used.
  As previously mentioned, check system-->preferences-->Startup Applications and disable items that you're not using.
  Also, you could change desktop from KDE or Gnome to Xfce4, LXDE, or some other smaller/lighter environment.

---

### Post by tiresmokindad on 2010-06-13
I suggest you should remove the findutils. It is not useful at all. :D

---

### Post by pbhj on 2010-06-25
@acrazyplayer, thanks but I'm using OOo, so can't remove it - I guess I could use koffice (smaller) but I'm linking in to a OOo base db for work purposes. WRT flashplayer I prefer to use the packaged one for easy upgrade; I know it's not much but since I moved from Slackware a couple years back I'm over doing it myself.

@madtownmike, good catch on the fonts, thanks. I don't have Gnome installed but K > System Settings > :Advanced: > Service Manager allows services to be switched under KDE and I've made use of it as much as I can.

@tiresmokindad, libc6 and initramfs dep on findutils; I do use find and xargs occassionally (but not as much as [m]locate).

So I've also removed usplash and the usplash-theme-ubuntu package along with xdg-users-dir (tells apps which dir to use for file saving AFAICT).

Looking at disabling console-kit-daemon and possibly policykit too but they're more difficult as some base packages are dependent on them. Will probably either call "exit 0" in their startup scripts or switch the executables for /bin/true.

---

### Post by pbhj on 2010-06-25
For /usr/sbin/console-kit-daemon I've done

```
sudo mv /usr/sbin/console-kit-daemon{,.backup}
sudo ln -s /bin/true /usr/sbin/console-kit-daemon
```

let's see what happens!

Edit: what happens is that one can't shutdown from the K menu but can "shutdown -h now", also there's a error message on log in, but nothing substantial when running except that windows can't be maximised (weird) but can be dragged fullscreen).

Have also removed /usr/share/doc/ and /usr/share/doc-base/ saving about 80M of disk space.

---

