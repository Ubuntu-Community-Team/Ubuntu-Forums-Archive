---
title: "broken package manager"
date: 2011-04-29
forum: General Help
---

### Post by bjje on 2011-04-29
After Upgrade to natty everything went well except my package manager is now broken and I keep going around in circles;


Update manager gives me a list of six updates that are downloaded but not installed. When I try to install, It returns;
 > "the package system is broken" window.  details;

  The following packages have unmet dependencies:

ca-certificates-java: Depends: java6-runtime-headless but it is a virtual package
icedtea-6-jre-cacao: Depends: openjdk-6-jre-headless (= 6b22-1.10.1-0ubuntu1) but it is not installed
                     Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is installed
                     Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is installed
icedtea-6-jre-jamvm: Depends: openjdk-6-jre-headless (= 6b22-1.10.1-0ubuntu1) but it is not installed
                     Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is installed
openjdk-6-jre: Depends: openjdk-6-jre-headless (>= 6b22-1.10.1-0ubuntu1) but it is not installed
               Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is installed
openjdk-6-jre-lib: Depends: openjdk-6-jre-headless (>= 6b17) but it is not installed
ubuntustudio-video: Depends: openshot but it is not installed
Tells me to use the broken filter to locate them gives me;

> E: /var/cache/apt/archives/openjdk-6-jre-headless_6b22-1.10.1-0ubuntu1_i386.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
E: /var/cache/apt/archives/openshot_1.3.0-1_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
E: /var/cache/apt/archives/openshot-doc_1.3.0-1_all.deb: subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Tells me to do apt-get install -f; 
returns;
> 
   ading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic libx264-98
  libkprintutils4 libkrossui4 docbook-xsl-doc-html autopano-sift libpano13-1
  libxdot4 smartdimmer esound-clients libebml2 libmatroska2 libkutils4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openjdk-6-jre-headless openshot openshot-doc
Suggested packages:
  sun-java6-fonts ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts
The following NEW packages will be installed:
  openjdk-6-jre-headless openshot openshot-doc
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
9 not fully installed or removed.
Need to get 0 B/47.9 MB of archives.
After this operation, 135 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 312409 files and directories currently installed.)
Unpacking openjdk-6-jre-headless (from .../openjdk-6-jre-headless_6b22-1.10.1-0ubuntu1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-headless_6b22-1.10.1-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Unpacking openshot (from .../openshot_1.3.0-1_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/openshot_1.3.0-1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Unpacking openshot-doc (from .../openshot-doc_1.3.0-1_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/openshot-doc_1.3.0-1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-headless_6b22-1.10.1-0ubuntu1_i386.deb
 /var/cache/apt/archives/openshot_1.3.0-1_all.deb
 /var/cache/apt/archives/openshot-doc_1.3.0-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
I can't use synaptic nor Software center, it just wants to be repaired but  repair  returns;

package operation failed.
etc...........
Otherwise everything's great. 

Any observations?

---

### Post by dino99 on 2011-04-29
sudo gedit /etc/apt/sources.list

be sure to only have natty repo enabled

sudo rm /var/cache/apt/archives*

then update again

---

### Post by bjje on 2011-04-29
Yee-Ha, many thankyoos

---

