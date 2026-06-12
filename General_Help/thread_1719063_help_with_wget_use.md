---
title: "help with wget use"
date: 2011-04-01
forum: General Help
---

### Post by slimage on 2011-04-01
hi,

I am trying to download all the Heroes graphic novels off the nbc site. Originally I was downloading them via the provided links but with ~170 pdfs to download it was going to take a while

I used wget to start downloading them a bit faster, I tried the command

$wget -N -r -l inf -p -np -k -A '.pdf' [http://www.nbc.com/heroes/novels/downloads/](http://www.nbc.com/heroes/novels/downloads/)

in an attempt to download all the pdfs at once, I got an error message 


--2011-04-01 13:17:14--  [http://www.nbc.com/heroes/novels/downloads/](http://www.nbc.com/heroes/novels/downloads/)
Resolving [www.nbc.com](www.nbc.com)... 92.122.49.98, 92.122.49.235
Connecting to [www.nbc.com|92.122.49.98|:80](www.nbc.com|92.122.49.98|:80)... connected.
HTTP request sent, awaiting response... 403 Forbidden
2011-04-01 13:17:15 ERROR 403: Forbidden.

Is this something I've done wring or something nbc have done to stop the use of wget?

Cheers

---

### Post by gmargo on 2011-04-01
That directory is not readable directly (the web server can control this).  So wget cannot read in the index of files.

However, wget works fine on an individual PDF:
```

wget http://www.nbc.com/heroes/novels/images/Heroes_novel_172.pdf

```With only a little imagination, you can put that in a shell script loop to get all the files, one by one.

The first and last PDFs are:
```

http://www.nbc.com/heroes/novels/downloads/Heroes_novel_001.pdf
http://www.nbc.com/heroes/novels/images/Heroes_novel_173.pdf

```So it looks like the directory changed somewhere in the sequence; your challenge is to figure out where.

---

### Post by dingodog on 2011-04-01
Woof Woof

use this script (copy and paste ina file and making executable (**chmod a+x**)

```
#!/bin/sh
printf "wget --wait=1 -O %03d.pdf\n" {1..173} > 1.txt
printf "http://www.nbc.com/heroes/novels/downloads/Heroes_novel_%03d.pdf \n" {1..173} > 2.txt
paste 1.txt 2.txt >3.txt
sed -e '1i\#!/bin/sh' 3.txt >pdfdown
chmod a+x pdfdown
```and you will have:
```
#!/bin/sh
wget --wait=1 -O 001.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_001.pdf 
wget --wait=1 -O 002.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_002.pdf 
wget --wait=1 -O 003.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_003.pdf 
wget --wait=1 -O 004.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_004.pdf 
wget --wait=1 -O 005.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_005.pdf 
wget --wait=1 -O 006.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_006.pdf 
wget --wait=1 -O 007.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_007.pdf 
wget --wait=1 -O 008.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_008.pdf 
wget --wait=1 -O 009.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_009.pdf 
wget --wait=1 -O 010.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_010.pdf 
wget --wait=1 -O 011.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_011.pdf 
wget --wait=1 -O 012.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_012.pdf 
wget --wait=1 -O 013.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_013.pdf 
wget --wait=1 -O 014.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_014.pdf 
wget --wait=1 -O 015.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_015.pdf 
wget --wait=1 -O 016.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_016.pdf 
wget --wait=1 -O 017.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_017.pdf 
wget --wait=1 -O 018.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_018.pdf 
wget --wait=1 -O 019.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_019.pdf 
wget --wait=1 -O 020.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_020.pdf 
wget --wait=1 -O 021.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_021.pdf 
wget --wait=1 -O 022.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_022.pdf 
wget --wait=1 -O 023.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_023.pdf 
wget --wait=1 -O 024.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_024.pdf 
wget --wait=1 -O 025.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_025.pdf 
wget --wait=1 -O 026.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_026.pdf 
wget --wait=1 -O 027.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_027.pdf 
wget --wait=1 -O 028.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_028.pdf 
wget --wait=1 -O 029.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_029.pdf 
wget --wait=1 -O 030.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_030.pdf 
wget --wait=1 -O 031.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_031.pdf 
wget --wait=1 -O 032.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_032.pdf 
wget --wait=1 -O 033.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_033.pdf 
wget --wait=1 -O 034.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_034.pdf 
wget --wait=1 -O 035.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_035.pdf 
wget --wait=1 -O 036.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_036.pdf 
wget --wait=1 -O 037.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_037.pdf 
wget --wait=1 -O 038.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_038.pdf 
wget --wait=1 -O 039.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_039.pdf 
wget --wait=1 -O 040.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_040.pdf 
wget --wait=1 -O 041.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_041.pdf 
wget --wait=1 -O 042.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_042.pdf 
wget --wait=1 -O 043.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_043.pdf 
wget --wait=1 -O 044.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_044.pdf 
wget --wait=1 -O 045.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_045.pdf 
wget --wait=1 -O 046.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_046.pdf 
wget --wait=1 -O 047.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_047.pdf 
wget --wait=1 -O 048.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_048.pdf 
wget --wait=1 -O 049.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_049.pdf 
wget --wait=1 -O 050.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_050.pdf 
wget --wait=1 -O 051.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_051.pdf 
wget --wait=1 -O 052.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_052.pdf 
wget --wait=1 -O 053.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_053.pdf 
wget --wait=1 -O 054.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_054.pdf 
wget --wait=1 -O 055.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_055.pdf 
wget --wait=1 -O 056.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_056.pdf 
wget --wait=1 -O 057.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_057.pdf 
wget --wait=1 -O 058.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_058.pdf 
wget --wait=1 -O 059.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_059.pdf 
wget --wait=1 -O 060.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_060.pdf 
wget --wait=1 -O 061.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_061.pdf 
wget --wait=1 -O 062.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_062.pdf 
wget --wait=1 -O 063.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_063.pdf 
wget --wait=1 -O 064.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_064.pdf 
wget --wait=1 -O 065.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_065.pdf 
wget --wait=1 -O 066.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_066.pdf 
wget --wait=1 -O 067.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_067.pdf 
wget --wait=1 -O 068.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_068.pdf 
wget --wait=1 -O 069.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_069.pdf 
wget --wait=1 -O 070.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_070.pdf 
wget --wait=1 -O 071.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_071.pdf 
wget --wait=1 -O 072.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_072.pdf 
wget --wait=1 -O 073.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_073.pdf 
wget --wait=1 -O 074.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_074.pdf 
wget --wait=1 -O 075.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_075.pdf 
wget --wait=1 -O 076.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_076.pdf 
wget --wait=1 -O 077.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_077.pdf 
wget --wait=1 -O 078.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_078.pdf 
wget --wait=1 -O 079.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_079.pdf 
wget --wait=1 -O 080.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_080.pdf 
wget --wait=1 -O 081.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_081.pdf 
wget --wait=1 -O 082.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_082.pdf 
wget --wait=1 -O 083.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_083.pdf 
wget --wait=1 -O 084.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_084.pdf 
wget --wait=1 -O 085.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_085.pdf 
wget --wait=1 -O 086.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_086.pdf 
wget --wait=1 -O 087.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_087.pdf 
wget --wait=1 -O 088.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_088.pdf 
wget --wait=1 -O 089.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_089.pdf 
wget --wait=1 -O 090.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_090.pdf 
wget --wait=1 -O 091.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_091.pdf 
wget --wait=1 -O 092.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_092.pdf 
wget --wait=1 -O 093.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_093.pdf 
wget --wait=1 -O 094.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_094.pdf 
wget --wait=1 -O 095.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_095.pdf 
wget --wait=1 -O 096.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_096.pdf 
wget --wait=1 -O 097.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_097.pdf 
wget --wait=1 -O 098.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_098.pdf 
wget --wait=1 -O 099.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_099.pdf 
wget --wait=1 -O 100.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_100.pdf 
wget --wait=1 -O 101.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_101.pdf 
wget --wait=1 -O 102.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_102.pdf 
wget --wait=1 -O 103.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_103.pdf 
wget --wait=1 -O 104.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_104.pdf 
wget --wait=1 -O 105.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_105.pdf 
wget --wait=1 -O 106.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_106.pdf 
wget --wait=1 -O 107.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_107.pdf 
wget --wait=1 -O 108.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_108.pdf 
wget --wait=1 -O 109.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_109.pdf 
wget --wait=1 -O 110.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_110.pdf 
wget --wait=1 -O 111.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_111.pdf 
wget --wait=1 -O 112.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_112.pdf 
wget --wait=1 -O 113.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_113.pdf 
wget --wait=1 -O 114.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_114.pdf 
wget --wait=1 -O 115.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_115.pdf 
wget --wait=1 -O 116.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_116.pdf 
wget --wait=1 -O 117.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_117.pdf 
wget --wait=1 -O 118.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_118.pdf 
wget --wait=1 -O 119.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_119.pdf 
wget --wait=1 -O 120.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_120.pdf 
wget --wait=1 -O 121.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_121.pdf 
wget --wait=1 -O 122.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_122.pdf 
wget --wait=1 -O 123.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_123.pdf 
wget --wait=1 -O 124.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_124.pdf 
wget --wait=1 -O 125.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_125.pdf 
wget --wait=1 -O 126.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_126.pdf 
wget --wait=1 -O 127.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_127.pdf 
wget --wait=1 -O 128.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_128.pdf 
wget --wait=1 -O 129.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_129.pdf 
wget --wait=1 -O 130.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_130.pdf 
wget --wait=1 -O 131.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_131.pdf 
wget --wait=1 -O 132.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_132.pdf 
wget --wait=1 -O 133.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_133.pdf 
wget --wait=1 -O 134.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_134.pdf 
wget --wait=1 -O 135.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_135.pdf 
wget --wait=1 -O 136.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_136.pdf 
wget --wait=1 -O 137.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_137.pdf 
wget --wait=1 -O 138.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_138.pdf 
wget --wait=1 -O 139.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_139.pdf 
wget --wait=1 -O 140.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_140.pdf 
wget --wait=1 -O 141.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_141.pdf 
wget --wait=1 -O 142.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_142.pdf 
wget --wait=1 -O 143.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_143.pdf 
wget --wait=1 -O 144.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_144.pdf 
wget --wait=1 -O 145.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_145.pdf 
wget --wait=1 -O 146.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_146.pdf 
wget --wait=1 -O 147.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_147.pdf 
wget --wait=1 -O 148.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_148.pdf 
wget --wait=1 -O 149.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_149.pdf 
wget --wait=1 -O 150.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_150.pdf 
wget --wait=1 -O 151.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_151.pdf 
wget --wait=1 -O 152.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_152.pdf 
wget --wait=1 -O 153.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_153.pdf 
wget --wait=1 -O 154.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_154.pdf 
wget --wait=1 -O 155.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_155.pdf 
wget --wait=1 -O 156.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_156.pdf 
wget --wait=1 -O 157.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_157.pdf 
wget --wait=1 -O 158.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_158.pdf 
wget --wait=1 -O 159.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_159.pdf 
wget --wait=1 -O 160.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_160.pdf 
wget --wait=1 -O 161.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_161.pdf 
wget --wait=1 -O 162.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_162.pdf 
wget --wait=1 -O 163.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_163.pdf 
wget --wait=1 -O 164.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_164.pdf 
wget --wait=1 -O 165.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_165.pdf 
wget --wait=1 -O 166.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_166.pdf 
wget --wait=1 -O 167.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_167.pdf 
wget --wait=1 -O 168.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_168.pdf 
wget --wait=1 -O 169.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_169.pdf 
wget --wait=1 -O 170.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_170.pdf 
wget --wait=1 -O 171.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_171.pdf 
wget --wait=1 -O 172.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_172.pdf 
wget --wait=1 -O 173.pdf    http://www.nbc.com/heroes/novels/downloads/Heroes_novel_173.pdf 

```

---

### Post by slimage on 2011-04-02
thanks for the help guys, I've successfully downloaded the files and learnt some useful stuff about shell scripting.

I appreciate your help

---

