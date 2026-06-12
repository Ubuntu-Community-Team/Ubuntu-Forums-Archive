---
title: "Backing up hidden files"
date: 2012-06-19
forum: General Help
---

### Post by Kansasguy on 2012-06-19
The short of it:  are hidden files backed up when you back up a folder?

The long of it:  I loaded LinuxMint LXCE on the partition where I had Kubuntu previously (on one partition of my Asus Netbook 1005ha, dual booted Kubuntu and XP), using an iso on a USB flash drive.  I had saved my Home Folder to an external HD previously (three times, in fact, in the last 4 months.  I had expected to find the Profiles files for Firefox and Thunderbird in the Home folder backup so I could restore my bookmarks and emails.  Either the hidden files are not there, or I can't "find"/extract them.   Any help?      TIA

---

### Post by SeijiSensei on 2012-06-19
Both cp and rsync have an "-a" switch that tells them to include hidden files and preserve things like permissions and datestamps as well.  So, for instance,

```
cd /
sudo rsync -av home /backup

```

will copy all of the contents of /home, including hidden files, to /backup. See "[man cp]("http://manpages.ubuntu.com/manpages/precise/man1/cp.1.html")" or "[man rsync]("http://manpages.ubuntu.com/manpages/precise/man1/rsync.1.html")" for details.

---

### Post by wilee-nilee on 2012-06-19
> **Kansasguy said:**
> The short of it:  are hidden files backed up when you back up a folder?

The long of it:  I loaded LinuxMint LXCE on the partition where I had Kubuntu previously (on one partition of my Asus Netbook 1005ha, dual booted Kubuntu and XP), using an iso on a USB flash drive.  I had saved my Home Folder to an external HD previously (three times, in fact, in the last 4 months.  I had expected to find the Profiles files for Firefox and Thunderbird in the Home folder backup so I could restore my bookmarks and emails.  Either the hidden files are not there, or I can't "find"/extract them.   Any help?      TIA

Crtl-h to show hidden files.

---

