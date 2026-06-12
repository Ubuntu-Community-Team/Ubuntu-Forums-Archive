---
title: "cbrPager not showing images"
date: 2011-06-15
forum: General Help
---

### Post by Carnendil on 2011-06-15
Starting recently, when a (cbr, cbz, or cb7) file is opened, cbrPager will not show any images at all.

The file name does appear on the title bar.

Using Ubuntu 10.04, but observe the same problem with Lubuntu 11.04 (it worked fine with Lubuntu 10.04, as it did on Ubuntu 10.04 until several weeks ago).

Just to check, I've tried cbrPager both from the repository and from the tar.gz on their website, with the same results.

Thanks for any help.

N.B.: Evince shows cbr and cbz files all right.

---

### Post by Carnendil on 2011-10-03
I turns out that, for cb7 files at least, I needed p7zip installed (I have p7zip-full).

I had uninstalled p7zip since I normally use PeaZip and felt I didn't have a need for the former.

On my Ubuntu 10.04 LTS:

Despite the fact that unzip has always been installed, cbrPager still won't show any images after opening a cbz file.

With regards to cbr files (which I normally would re-format to 7zip, anyway), and with unrar-free installed, cbrPager actually *extracts* each image file, but still wouldn't show anything.

---

