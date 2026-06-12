---
title: "How do I recover? :("
date: 2009-12-08
forum: General Help
---

### Post by grantbourquehelp on 2009-12-08
Ok, so I have Ubuntu installed inside Windows 7. Everything was working fine, and I messed with something (let's not get into those details) and now I can't boot into Ubuntu (brings me to grub command line, says kernel cannot be found)

Well, that's not that big of deal. Except I had a SUPER important .ppt on there (ironically, as a back up) and after I had recently reformatted my flash drive and went back to get the .ppt, I can't get in! 

I need to know how to recover files from a corrupt partition that is installed inside of windows ASAP. Anybody know how?

Edit: it's a 9.10 wubi install

---

### Post by JK3mp on 2009-12-08
Wow sounds like quite a pickle, can you force boot from the grub line? rootnoverify (hdyourpartition) hit enter, chainloader +1 hit enter, boot hit enter. your partition is usually hd0,1 or hd0,2, varys on setup.(ex. rootnoverify (hd0,1)), but the way it sounds you've really screwed it up. Had u installed on an actual partition instead of virtual one inside windows i would suggest using live cd to recover, but for this i honestly can't help much. Best of luck, if my suggestion doesn't work hopefully someone a tad more experienced with virtual installs can help.

---

### Post by Leppie on 2009-12-08
Download ext2fsd from [this page]("http://sourceforge.net/projects/ext2fsd"). Karmic uses ext4 as default filesystem, but it's backwards compatible with ext2.

Hope this helps.

---

### Post by grantbourquehelp on 2009-12-08
> **Leppie said:**
> Download ext2fsd from [this page]("http://sourceforge.net/projects/ext2fsd"). Karmic uses ext4 as default filesystem, but it's backwards compatible with ext2.

Hope this helps.

It doesn't. I don't think normal recovery programs are going to work since it's wubi.

---

### Post by Leppie on 2009-12-08
> **grantbourquehelp said:**
> It doesn't. I don't think normal recovery programs are going to work since it's wubi.

ext2fsd is a windoze app; I suggested ext2fsd since you mentioned you did a wubi install (which creates an ext4 partition within empty space of a ntfs partition). But if this app cannot access your file, the ext4 partition may be corrupt.

---

### Post by grantbourquehelp on 2009-12-08
> **Leppie said:**
> ext2fsd is a windoze app; I suggested ext2fsd since you mentioned you did a wubi install (which creates an ext4 partition within empty space of a ntfs partition). But if this app cannot access your file, the ext4 partition may be corrupt.

It doesn't detect it, and won't allow me to go into C: to fetch the location of the Ubuntu folder. 

I just finished remaking the powerpoint from some notes I still had, but needless to say this is a pretty devastating issue with 9.10 wubi. Looks like I'm not the only one with it either.

---

### Post by fluffman86 on 2009-12-08
It's not an issue with 9.10, it's an issue with Wubi.  The filesystem created in Windows is just a single, large file, and as such is rather volatile; large files are more susceptible to corruption.  I'm not sure if this is made abundantly clear during the Wubi install or not, but Wubi is really just meant to *test* Ubuntu (because the live CD is somewhat lacking), not as a full time installation.

That said, I think you can still probably recover the file if necessary using VirtualBox.  Look for a tutorial that will allow you to mount your Wubi file as a virtual disk.

---

