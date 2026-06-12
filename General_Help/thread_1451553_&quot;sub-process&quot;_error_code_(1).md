---
title: "&quot;sub-process&quot; error code (1)"
date: 2010-04-10
forum: General Help
---

### Post by Scythium on 2010-04-10
clamav is already the newest version.
The following packages were automatically installed and are no longer required:
  wavpack vorbis-tools libgmp3-dev libcddb2 libffi-dev libdvbpsi5
  libgmpxx4ldbl libvlc2 vlc-nox libao2 ghc6 flac libiso9660-5 sox
  vlc-plugin-pulse vlc-data libtar libvlccore2 libvcdinfo0 libebml0
  libmatroska0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up psad (2.1.5-1) ...
Starting Port Scan Attack Detector: psad 
[*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 9566.
 * Unable to start the daemon.
invoke-rc.d: initscript psad, action "start" failed.
dpkg: error processing psad (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 psad
E: Sub-process /usr/bin/dpkg returned an error code (1)



I'm stuck and the line that says Starting Port Scan Attack Detector: has me worried.
I get the E: Sub-process error code (1) when I install new software.

---

### Post by Scythium on 2010-04-11
uninstalling psad from Synaptic Package Manager got rid of the error. I wish I had a better solution though.

---

