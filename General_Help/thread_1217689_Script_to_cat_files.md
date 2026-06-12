---
title: "Script to cat files"
date: 2009-07-19
forum: General Help
---

### Post by darkshadow on 2009-07-19
I have a cousin who has lately started getting a massive of split files. I would like help making a shell script that I can associate with .001 files that will cat them together. Since he has trouble even being talked through the cat command over the phone and I am tired of ssh'ing into his computer and doing it.

I was thinking something that does the following when ran on the some filename.ext.001

#whatever it takes get filename.ext as the $basename (I saw it along time ago but forgot how then
cat $basename.* > $basename

The downloaded files may have special characters that need escape characters and many "."'s instead of spaces.

---

