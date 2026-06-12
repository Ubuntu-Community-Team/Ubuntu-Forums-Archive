---
title: "Trouble getting my dvd to install mint 9"
date: 2010-07-18
forum: General Help
---

### Post by steve509 on 2010-07-18
Ok, heres my delema, I'm now running ubuntu 9.10 and dual booting with 10.04. i want to check out Mint 9 (all 64 bit btw). I have downloaded Mint 9 64 and burned the iso at the slowest speed and i've reburned it on many dvd's. When I put the dvd in and restart I can't get it to go to the dvd writer. It is set to be first in the bios and when i put in something else like GParted it works just fine. I'm not sure what the problem could be, perhaps a bad download? When i put in the dvd and go to Computer, the dvd shows up and i can see the Mint 9 iso file...Any help would be greatly appreciated

Thanks

steve509

---

### Post by willjammn on 2010-07-18
Did you check the md5sum of the Mint Linux iso?

---

### Post by steve509 on 2010-07-18
willjammn, thanks so much for the response. How do i go about doing that, should it just be there as a second file or do i have to do something to the iso to check...please excuse my ignorance, i am still a newbie

steve509

---

### Post by steve509 on 2010-07-18
willjammn, I extracted the iso and here is the md5sum.txt:

a4b29b43f9757c3a69528db02c8e6dd4  ./preseed/ltsp.seed
d007768a1066ab1419d93daea54c4844  ./preseed/mint.seed
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
2e00bbc97aa398fea542dde339e0fb4c  ./isolinux/memtest
e1a88df9419de2803d2e3d588273b77a  ./isolinux/isolinux.cfg
ed4604e47167175515efa84c847d33b2  ./isolinux/vesamenu.c32
e27aa83c46ed8d0e4c3a54f9eb018b81  ./isolinux/splash.jpg
0b631486f45023d97837bada4d881ae7  ./autorun.inf
ca3f0ff4ed43446b2c17a2bd1e4d7f5a  ./.disk/info
7042b54a6d499aac321d523bfe42f4c5  ./.disk/mint4win
e39c965a2e93ce2955fcad47530f21fc  ./.disk/release_notes_url
db883a5aa4b32fc3e3c724a2cd9cc922  ./.disk/casper-uuid-generic
d41d8cd98f00b204e9800998ecf8427e  ./.disk/base_installable
728cb968a88534e0c50a9d99621f13eb  ./.disk/cd_type
3749f783ec858943d147ed68b3d03e11  ./mint4win.exe
8575590542fc98558aab1a7c2c7fb97c  ./casper/filesystem.manifest
e815e512b4ee345d97e869d6440c6278  ./casper/filesystem.squashfs
2113380959635a723d13bb6816902e8a  ./casper/filesystem.manifest-desktop
700def97af2518a8b8247705b4c0df45  ./casper/filesystem.size
135737a6c8608631a2cde5a8aad7995c  ./casper/vmlinuz
f095ab591124d5011f2f47621b21f949  ./casper/initrd.lz

I have no clue...lol

thanks for your help

---

### Post by TLUL on 2011-01-13
[SIZE="1"][COLOR="Gray"](I don't generally like to dig up old topics on forums, but this was on top of a fairly general Google search and I hate to see something unresolved as the top result on a potentially-common Google search.)[/COLOR][/SIZE]

> **steve509 said:**
> When i put in the dvd and go to Computer, the dvd shows up and i can see the Mint 9 iso file

You shouldn't see the ISO file on the disc. You need to use a proper DVD burning program to burn the contents of the ISO file, not the file itself. If you don't have one, you might be able to extract the contents of the ISO file with an archiver (such as 7-zip) and burn those directly.

---

