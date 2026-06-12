---
title: "John The Ripper help"
date: 2009-12-29
forum: General Help
---

### Post by checkm8 on 2009-12-29
I have heard about the command

./john --incremental:all 

But when trying to increase the amount of characters that the command can use, I keep running into errors. I have tried to increase the limit before compiling john the ripper to 32 under the CHARSET_LENGTH defined under src/params.h but to no avail. 

The error I am getting now is

incorrect charset file format

I have tried generating my own charset using the command 

./john --make-charset=all.chr

but I am unable to make make it due to the error

Self test failed (pow64of32() overflow)

Any suggestions?

Edit:

The version of John The Ripper I'm using is 1.7.3.4

---

