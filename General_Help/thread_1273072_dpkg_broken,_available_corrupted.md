---
title: "dpkg broken, available corrupted"
date: 2009-09-23
forum: General Help
---

### Post by bugritall on 2009-09-23
Update Manager and Synaptic have both been having similar problems on my Jaunty installation recently.

For example, when Update Manager tried to install
> Important security updates

libneon27
An HTTP and WebDAV client library

libneon27-gnutls
 ditto  (GnuTLS enabled)
It failed with the following message: 
> dpkg: failed in buffer_read(fd): copy info file '/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned and error code (2)
A package failed to install. Trying to recover:
dpkg: failed in buffer_read(fd): copy info file '/var/lib/dpkg/available': Input/output errorI also encountered similar errors when I tried to use Synaptic to install Acidrip and k3b, i.e. dpkg had problems accessing /var/lib/dpkg/available

Researching the problem took me to a [locked thread]("http://ubuntuforums.org/showthread.php?t=382146") on this forum and I tried the advice I found there:
```
sudo dpkg --clear-avail
```After that, I tried Update Manager again but it got *very* upset, reporting:
> Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Could not open file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_i18n_Translation-en%5fGB - open (2 No such file or directory), E:Could not open file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_i18n_Translation-en%5fGB - open (2 No such file or directory), E:Could not open file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_i18n_Translation-en%5fGB - open (2 No such file or directory), E:Could not open file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_i18n_Translation-en%5fGB - open (2 No such file or directory)'Undeterred, I tried again and this time Update Manager seemed perfectly happy. I told it to "Check" and all seemed well again. Furthermore, Synaptic has now successfully installed acidrip and k3b, the packages that it failed with previously.

Am I in the clear now?

Do I still need to report the "bug" that update manager got so upset about and, if so, how/where?

---

