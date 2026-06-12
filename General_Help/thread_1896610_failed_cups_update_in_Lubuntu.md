---
title: "failed cups update in Lubuntu"
date: 2011-12-17
forum: General Help
---

### Post by tyhee88 on 2011-12-17
Running Lubuntu 11.10, Dell Optiplex GX620, Intel 945G chipset, Pentium D-2.8 GHz, 80 GB hard drive; 2GB DDR2, kernel is 3.0.0-14-generic.  Did updates last night via Update Manager, one of the packages being updated was cups-common.  The description of the change reads:  __________ Changes for the versions: Installed version: 1.5.0-8ubuntu5 Available version: 1.5.0-8ubuntu6  Version 1.5.0-8ubuntu6:     * debian/patches/ipp-patch-r8950+.patch: Revert the IPP backend to the state     of CUPS 1.4.x, as the 1.5.x versiuon has major regressions (LP: #877958,     LP: #879625, LP: #881843, LP: #883585, Closes: #638521, CUPS STR #3966,     CUPS STR #3967). This patch will get removed as soon as upstream has fixed      all these regressions. As upstream did not announce any new features for     the IPP backend in the release notes for 1.5.x, we assume that with this     step no features will get lost.   * debian/patches/dont-send-malformed-dbus-messages.patch: Do not send D-Bus     notifications with too few parameters when there are parameters which     cannot be added to the D-Bus request, especially invalid UTF-8 strings.     This made gnome-session-daemon crash (LP: #893676, CUPS STR #3984).   * debian/local/filters/cpdftocps: The cpdftocps filter (used for PostScript     printers and for drivers with PPDs which are not PDF-aware) did not     recognize the duplex setting correctly, making duplex not working on     many common printers (LP: #897723).   * debian/local/filters/cpdftocps: Cleaned up the header comments. ___________  There were other cups updates.  This one got a failure message.  After the sections about updating database (which seemed to go ok) the error message reads: ____ (Reading database ... 161810 files and directories currently installed.)  Preparing to replace cups-common 1.5.0-8ubuntu5 (using .../cups-common_1.5.0-8ubuntu6_all.deb) ...  Unpacking replacement cups-common ...  dpkg-deb (subprocess): data: internal gzip read error: ': data error'  dpkg-deb: error: subprocess  returned error exit status 2  dpkg: error processing /var/cache/apt/archives/cups-common_1.5.0-8ubuntu6_all.deb (--unpack):   subprocess dpkg-deb --fsys-tarfile returned error exit status 2  No apport report written because the error message indicates an issue on the local system Errors were encountered while processing:   /var/cache/apt/archives/cups-common_1.5.0-8ubuntu6_all.deb  Error in function:   SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)  ____________  I just tried printing a page using Libreoffice and it printed normally.  Any ideas what to do with the package that won't update?  Thanks.                   Bob C.

---

### Post by scorchgeek on 2011-12-17
Try looking at [http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/]("http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/").

Also, please post command output in \[CODE\] brackets in the future, by clicking the little hash mark (#) button on the toolbar when posting.

---

### Post by tyhee88 on 2011-12-17
> **scorchgeek said:**
> Try looking at [http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/).

Also, please post command output in \[CODE\] brackets in the future, by clicking the little hash mark (#) button on the toolbar when posting.
_____________

Thanks scorchgeek.  It's a great thread to some ideas on broken packages and trying a combination of things worked.  I tried the command line install -f with no help, so cleared the cache, purged 5 cups packages, reinstalled (which wouldn't work) and then was able to fix the broken package from Synaptic.

---

### Post by scorchgeek on 2011-12-17
Glad it worked.

Please mark this thread as solved from the "thread tools" link at the top of the page if your question has been answered.

---

