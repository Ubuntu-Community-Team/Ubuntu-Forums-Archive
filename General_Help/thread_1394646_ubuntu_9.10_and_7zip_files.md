---
title: "ubuntu 9.10 and 7zip files"
date: 2010-01-30
forum: General Help
---

### Post by rflores2323 on 2010-01-30
I have a couple of .7z files that I need to extract.  
The files are named below

Home Theater MEGA Pack v1.2.7z.004
Home Theater MEGA Pack v1.2.7z.003
Home Theater MEGA Pack v1.2.7z.002
Home Theater MEGA Pack v1.2.7z.001

I read that the fileroller can extract this using p7zip and I installed using the software center. I then try to open with the archive manager and get the following error

> 
7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Error: /home/xbmc/Downloads/Home Theater MEGA Pack v1.2.7z.004: Can not open file as archive

Errors: 1

 I however cannot even get the command of extract when right clicking on it (I believe since it does not have the .7z extention at the end).  I have tried to change the file to a shorter name and the extention to .7z and the when I right click the extract option is there however I get the below same  error


> 7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Error: /home/xbmc/Downloads/Home Theater MEGA Pack v1.2.7z: Can not open file as archive

Errors: 1

I have also installed peazip and it has a nice gui and tried and it does not even see the file when in the original format. (i.e.Home Theater MEGA Pack v1.2.7z.004)

Please help as I need these files extracted.

Thanks

---

### Post by x33a on 2010-01-30
please post the output of
```
file *
``` from the directory containing the zip files.

---

### Post by Gstv.inc on 2010-04-19
i get the same error on lucid
wen I try to extract some fonts...
I have this problem before on 8.04 or 8.10 and i'm not found the solution ,the i move the file to windows partition and use windows to extract them ,I would be happy if i could extract them in Linux, but this only happens with some files, dont know why...

---

### Post by Gstv.inc on 2010-04-19
adhesive_nr_seven.zip: Zip archive data, at least v2.0 to extract
alpha_fitness.zip:     Zip archive data, at least v2.0 to extract
alpha_woman_hair.zip:  Zip archive data, at least v2.0 to extract
blazed.zip:            Zip archive data, at least v2.0 to extract
cafeina_dig (1).zip:   PNG image, 32 x 32, 8-bit/color RGBA, non-interlaced
cheap_fire.zip:        Zip archive data, at least v0.9 to extract
cheese_and_mouse.zip:  Zip archive data, at least v2.0 to extract
chopin_script.zip:     Zip archive data, at least v2.0 to extract
circle_things_2.zip:   Zip archive data, at least v2.0 to extract
crash_test.zip:        Zip archive data, at least v2.0 to extract
cropbats.zip:          Zip archive data, at least v2.0 to extract
dingsbums_bats.zip:    Zip archive data, at least v2.0 to extract
dirty_english.zip:     Zip archive data, at least v2.0 to extract
eagleclaw.zip:         Zip archive data
eutemia_ornaments.zip: Zip archive data, at least v2.0 to extract
hypmotizin.zip:        Zip archive data, at least v2.0 to extract
im_fell_flowers.zip:   Zip archive data, at least v2.0 to extract
komika_display.zip:    Zip archive data, at least v2.0 to extract
mister_belvedere.zip:  Zip archive data, at least v2.0 to extract
raslani_tribal.zip:    Zip archive data, at least v2.0 to extract
razzle_dazzle.zip:     Zip archive data, at least v2.0 to extract
rotund_brk.zip:        Zip archive data, at least v2.0 to extract
tribalz.zip:           Zip archive data, at least v2.0 to extract
wc_fetish_bta.zip:     Zip archive data, at least v2.0 to extract
wc_rhesus_b_bta.zip:   Zip archive data, at least v2.0 to extract
wc_rhesus_bta.zip:     Zip archive data, at least v2.0 to extract
webmasters.zip:        Zip archive data, at least v2.0 to extract
zero_velocity.zip:     Zip archive data, at least v2.0 to extract

this is the output from 
file *
maybe i need install v2.0?
this ALL file fonts i can't extract.
what I need to do?

---

### Post by leonidas25 on 2011-03-08
Same problem here! please help with a link to the problem solved!

---

### Post by Gstv.inc on 2011-03-09
> **leonidas25 said:**
> Same problem here! please help with a link to the problem solved!

Why you still on 9.10??try upgrade
In my case i can't since they not work more on my videocard intel 855 ...
But i think they solve this for zip files when i try this a long time ago i move my files to the windows and then extract there BUT some of the files not extract a found they maybe be corrupted when i download,,try download again the file .....

---

