---
title: "ls_colors for doc xls odt ods"
date: 2010-07-03
forum: General Help
---

### Post by AlphaLexman on 2010-07-03
I want to modify my $LS_COLORS variable to colorize documents on a ls command.
 What color would be standard or most logical to the average user?

The files I want to colorize are: *.doc *.xls *.ppt *.odt *.ods *.txt *.csv *.html ...

I think these files should stand out in a terminal ls output. mp3's and jpg's do, why not business files (documents, spreadsheets, presentations, etc.)

What color would most fit with the *nix standards (if any)?

---

### Post by gzarkadas on 2010-07-04
IMO it is sufficient to not clash with standard colors for other items. One possibility is `07;01' which is essentially reverse video. From what I have seen so far, the use of `07' for background is not used by any standard file, so you can add subgroups to your list of files by simply changing the foreground color (the second number in the value).

---

