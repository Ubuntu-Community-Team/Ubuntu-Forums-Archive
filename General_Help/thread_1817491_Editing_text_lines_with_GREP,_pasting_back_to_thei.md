---
title: "Editing text lines with GREP, pasting back to their original position"
date: 2011-08-03
forum: General Help
---

### Post by hihihi100 on 2011-08-03
I am editing apt.dat, a data file for FlightGear. Because FGRun does differenciate between caps and no caps, if you look for an airport, only the ones written in all caps will appear. With GREP I have extracted the airport names list, edited it, and now I need to insert those lines to their original position in the original apt.dat file. See the example below:

Original apt.dat file looks like:

```
1     203 0 0 UHP1 Lenino (Closed)
10  52.910007  156.878342 09x  90.00 11154 0000.0000 0000.0000   249 111111  2 0 0 0.00 0 0300.0300
10  52.908983  156.853257 xxx 179.98   546 0.0 0.0   124 111111  2 0 0 0.00 0 
10  52.908988  156.878343 xxx 179.98   546 0.0 0.0   124 111111  2 0 0 0.00 0 
10  52.908993  156.903428 xxx 179.98   546 0.0 0.0   124 111111  2 0 0 0.00 0 
10  52.908134  156.878343 xxx  89.98 11154 0.0 0.0   124 111111  2 0 0 0.00 0 
14  52.911007  156.878342    0 0 Tower Viewpoint
19  52.911030  156.851840 1 WS
19  52.908984  156.904842 1 WS

1    3799 0 1 E46  02 Ranch
10  29.874897 -103.697127 15x 150.00  5000 0000.0000 0000.0000   100 111111  4 0 1 0.25 0 0300.0300
10  29.874897 -103.697127 05x  50.00  3499 0000.0000 0000.0000   100 111111  4 0 1 0.25 0 0300.0300
19  29.871950 -103.701915 1 WS
19  29.881279 -103.700828 1 WS
19  29.877844 -103.692339 1 WS
19  29.868515 -103.693425 1 WS

1     255 0 1 1T1  2 G Ranch
10  29.650236 -096.579416 17x 176.00  4000 0000.0000 0000.0000    50 111111  1 0 2 0.25 0 0300.0300
10  29.650236 -096.579416 08x  86.00  1670 0000.0000 0000.0000    30 111111  1 0 2 0.25 0 0300.0300
10  29.655660 -096.580090 xxx 266.00   110 0.0 0.0    25 111111  1 0 0 0.25 0 
10  29.650221 -096.579652 xxx 266.00   110 0.0 0.0    25 111111  1 0 0 0.25 0 
10  29.644783 -096.579215 xxx 266.00   110 0.0 0.0    25 111111  1 0 0 0.25 0 
10  29.650210 -096.579849 xxx 176.00  4000 0.0 0.0    25 111111  1 0 0 0.25 0 
19  29.650193 -096.582150 1 WS
19  29.655860 -096.579632 1 WS
19  29.650278 -096.576683 1 WS
19  29.644612 -096.579201 1 WS
```Just that the original file has in the order of 20,000 entries, insted of the 3 I copied above. I need to change the 20,000 lines that start like:

```

1     203 0 0 UHP1    Lenino (Closed)
1    3799 0 1 E46    02 Ranch
1     255 0 1 1T1    2 G Ranch
```Notice the common characters for these 3 lines, and for the whole 20,000 lines is a 1 followed by 4 spaces, for 20,000 lines that look like:

```
1     203 0 0 UHP1    LENINO (CLOSED)
1    3799 0 1 E46    02 RANCH
1     255 0 1 1T1    2 G RANCH
```Again, a 1 followed by 4 spaces, that never changes

Can that be done? Terminal? Libreoffice? Anything?

---

### Post by xixiLP on 2011-08-03
Hi hihihi100,

I think you should post this to flightgear devel list..

you can register here: [https://lists.sourceforge.net/lists/listinfo/flightgear-devel/](https://lists.sourceforge.net/lists/listinfo/flightgear-devel/)

as this problem may also be of interest for flightgear scenery team. And they are familiar with such operations on apt.dat

Alexis
aka xiii on Flightgear

---

### Post by Vaphell on 2011-08-03
if all you want to do is to change from mixed case to all caps then run this on your original file:

```
sed -r '[COLOR="Navy"]/[0-9]+\s+[0-9]+\s+[0-9]+\s+[0-9]+\s+[0-9A-Z]+\s+.+/[/COLOR][COLOR="SeaGreen"]y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/[/COLOR]' apt.dat > apt_all_caps.dat 
```

blue part selects only lines that match a pattern of digit(s), space(s), digit(s), ....
green part does substitution of characters (y option) from the first part with the characters of the second part

---

### Post by hihihi100 on 2011-08-03
Hi:

```
awk '{if (/^1    /) print toupper($0); else print $0}' /home/dexter/Compiled/FlightGear/install/fgfs/fgdata/Airports/apt.dat > newfile
```

made the thing anyway, now, the second part of it: how do I do the same BUT for Standard Capitalization? for the 20,000 name lines, not LOS ANGELES, but Los Angeles.

Somebody suggested

```
sed '/^1    .*$/ s/\(\<.\)\.*/\u\1/g' /home/dexter/Compiled/FlightGear/install/fgfs/fgdata/Airports/apt.dat > newfile1

```
but that didnt work

I was also suggested to try something based on:

```
counter=0;for f in `cat replace.txt`;do replace[counter]=$f;counter=$counter+1;done;counter2=0; for ((a=0; a <= $counter-1; a=a+2)); do `sed -i "s/${replace[$a]}/${replace[$a+1]}/g" *.c` ;done;
```

But for this I need to export the 2 columns of names from libreoffice to a .txt file, and it will always paste the result no respecting the 2 columns, as seen in libreoffice, but will make a mix of both columns. Is there any way I can delimite both columns? maybe adding * before the beginning of the second column? see below:

Libreoffice calc output, pasted in here shows both columns exactly as seen in texteditor:

1     203 0 0 UHP1 [X]Lenino    1     203 0 0 UHP1    Lenino (Closed)
1    3799 0 1 E46  02 Ranch    1    3799 0 1 E46    02 Ranch
1     255 0 1 1T1  2 G Ranch    1     255 0 1 1T1    2 G Ranch
1    3360 0 1 NM47 2 X 4 Ranch    1    3360 0 1 NM47    2 X 4 Ranch
1    2695 0 1 OG00 3 Rivers Recreation Area    1    2695 0 1 OG00    3 Rivers Recreation Area
1      81 0 1 CA54 33 Strip    1      81 0 1 CA54    33 Strip
1     890 0 1 96GA 3MS    1     890 0 1 96GA    3ms
1     810 0 1 7I6  4 Winds Aerodrome    1     810 0 1 7I6    4 Winds Aerodrome
1      80 0 1 9M9  4B Ranch    1      80 0 1 9M9    4b Ranch
1     272 0 1 XS50 4G Ranch    1     272 0 1 XS50    4g Ranch
1     819 0 1 PA81 5 Lakes    1     819 0 1 PA81    5 Lakes
1    1085 0 1 1OK8 5B Ranch    1    1085 0 1 1OK8    5b Ranch
1    1190 0 1 63KS 5D Ranch    1    1190 0 1 63KS    5d Ranch
1    1580 0 1 73WA 7 Bays    1    1580 0 1 73WA    7 Bays
1    1605 0 1 PS53 7H Skeet Club Inc Field    1    1605 0 1 PS53    7h Skeet Club Inc Field
1    1300 0 1 81CA 7M Ranch    1    1300 0 1 81CA    7m Ranch
1    3176 0 1 CL25 7R Ranch    1    3176 0 1 CL25    7r Ranch
1      80 0 1 FD02 85th Avenue Airstrip    1      80 0 1 FD02    85th Avenue Airstrip
1     465 0 1 96KY A & L    1     465 0 1 96KY    A & L
1      51 1 1 RKSG A 511    1      51 1 1 RKSG    A 511
1    7880 0 1 WY11 A A RANCH    1    7880 0 1 WY11    A A Ranch
1     323 1 0 LECO A Coruna    1     323 1 0 LECO    A Coruna
1     450 0 1 61PN A G A Farms    1     450 0 1 61PN    A G A Farms
1     355 0 1 KOCH A L MANGHAM JR RGNL    1     355 0 1 KOCH    A L Mangham Jr Rgnl
1     220 0 1 KAPH A P HILL AAF    1     220 0 1 KAPH    A P Hill Aaf
1     480 0 1 TX27 A P Ranch    1     480 0 1 TX27    A P Ranch

The character that separates both columns is a one, that one has to be in the final output

---

