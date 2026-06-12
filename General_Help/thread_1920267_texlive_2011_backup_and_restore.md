---
title: "texlive 2011: backup and restore?"
date: 2012-02-04
forum: General Help
---

### Post by floydian_slip on 2012-02-04
Hi,

I want to do a fresh install of Xubuntu, but I don't want to have to re-download and reinstall all of texlive 2011, which amounts to about 3 GB (which takes like 2 hours, plus it eats up a chunk of my monthly data transfer limit).

I'm wondering if there's a safe way to back up my current texlive 2011 installation. In particular, is it possible to simply copy all the relevant directories and files, and then put them in their correct spot after my fresh OS install?

The relevant directories would, I think, be:

TEXDIR: ~/texlive/2011
TEXMFLOCAL: ~/texlive/texmf-local
TEXMFSYSVAR: ~/texlive/2011/texmf-var
TEXMFSYSCONFIG: ~/texlive2011/texmf-config
TEXMFHOME: ~/texmf

(I changed the main TeX directory, TEXDIR, from the default /usr/local/... to my home directory.)

Are there any other directories/files? Or is this just a bad idea in general?

Thanks!

Brian

[Edited: I know that tlmgr has a backup/restore option for packages, but I'm not sure how helpful that is for backing up an entire texlive installation. Then there's also the option to install as "portable", but I'm not sure what that really amounts to.]

---

