---
title: "Installing 2.6 kernel on fresh 11.10 x64 install"
date: 2012-02-13
forum: General Help
---

### Post by Audiosears on 2012-02-13
Folks,

I'm looking for a way to install the 'latest' 2.6.x kernel on an Oneiric server install (x64) so I can boot with it until Backup Exec finally supports kernel 3.x.

I'm using BE 2010 R3, which as of this writing doesn't allow a RALUS linux client to work as a remote client unless you're running a 2.6 kernel or older.  No official word yet (afaik) whether BE 2012 will support the 3.x kernel, but I would assume so eventually.

I can get the BE remote services to work more or less fine using a 2.6.x kernel, which I had on my previous install b/c that was an upgrade from previous Ubuntu releases.  However, this being a fresh release it came with the 3.x kernel from the get-go.

I can't find what would be the most fool-proof way to do this so far, but I'm looking to only use an official source if possible (PPA?).  I'd like to be able to apt-get the latest 2.6 kernels I can, edit grub to default to those for booting until further notice.

Can anyone give me me some advice on the path of least resistance going forward?

---

