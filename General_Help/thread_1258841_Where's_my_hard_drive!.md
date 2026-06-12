---
title: "Where's my hard drive!"
date: 2009-09-05
forum: General Help
---

### Post by Kittylicious on 2009-09-05
I fudged up my installation of Windows beyond repair and went back to my trusty old live cd of Ubuntu 6.06 to rescue some files. But no hard drive mounting procedure I could find online worked because whenever I try to mount, I am told the device does not exist. When I go to Place>Computer, I only see my dvd drives, the live filesystem, and removeable media drives... no hard drive. The hard drive still works and has SOMETHING on it, because if I try to boot into Windows XP, I get past the loading screen. Is there something I can do? There are a couple large files I'd really like to get back.

Thanks in advance.

---

### Post by Barafu Albino Cheetah on 2009-09-05
Show us the output of ```
ls /dev
``` please

---

### Post by Kittylicious on 2009-09-05
> **Barafu Albino Cheetah said:**
> Show us the output of ```
ls /dev
``` please


```
acpi       ptya6  ptyp2  ptyte  ptyya    tty27  ttyc0  ttyqc   ttys9  ttyx4
bus        ptya7  ptyp3  ptytf  ptyyb    tty28  ttyc1  ttyqd   ttyS9  ttyx5
cdrom      ptya8  ptyp4  ptyu0  ptyyc    tty29  ttyc2  ttyqe   ttysa  ttyx6
cdrw       ptya9  ptyp5  ptyu1  ptyyd    tty3   ttyc3  ttyqf   ttysb  ttyx7
console    ptyaa  ptyp6  ptyu2  ptyye    tty30  ttyc4  ttyr0   ttysc  ttyx8
core       ptyab  ptyp7  ptyu3  ptyyf    tty31  ttyc5  ttyr1   ttysd  ttyx9
disk       ptyac  ptyp8  ptyu4  ptyz0    tty32  ttyc6  ttyr2   ttyse  ttyxa
dvd        ptyad  ptyp9  ptyu5  ptyz1    tty33  ttyc7  ttyr3   ttysf  ttyxb
evms       ptyae  ptypa  ptyu6  ptyz2    tty34  ttyc8  ttyr4   ttyt0  ttyxc
fb0        ptyaf  ptypb  ptyu7  ptyz3    tty35  ttyc9  ttyr5   ttyt1  ttyxd
fd         ptyb0  ptypc  ptyu8  ptyz4    tty36  ttyca  ttyr6   ttyt2  ttyxe
full       ptyb1  ptypd  ptyu9  ptyz5    tty37  ttycb  ttyr7   ttyt3  ttyxf
hdc        ptyb2  ptype  ptyua  ptyz6    tty38  ttycc  ttyr8   ttyt4  ttyy0
hdd        ptyb3  ptypf  ptyub  ptyz7    tty39  ttycd  ttyr9   ttyt5  ttyy1
hpet       ptyb4  ptyq0  ptyuc  ptyz8    tty4   ttyce  ttyra   ttyt6  ttyy2
initctl    ptyb5  ptyq1  ptyud  ptyz9    tty40  ttycf  ttyrb   ttyt7  ttyy3
input      ptyb6  ptyq2  ptyue  ptyza    tty41  ttyd0  ttyrc   ttyt8  ttyy4
kmem       ptyb7  ptyq3  ptyuf  ptyzb    tty42  ttyd1  ttyrd   ttyt9  ttyy5
kmsg       ptyb8  ptyq4  ptyv0  ptyzc    tty43  ttyd2  ttyre   ttyta  ttyy6
log        ptyb9  ptyq5  ptyv1  ptyzd    tty44  ttyd3  ttyrf   ttytb  ttyy7
loop       ptyba  ptyq6  ptyv2  ptyze    tty45  ttyd4  ttys0   ttytc  ttyy8
loop0      ptybb  ptyq7  ptyv3  ptyzf    tty46  ttyd5  ttyS0   ttytd  ttyy9
loop1      ptybc  ptyq8  ptyv4  radio    tty47  ttyd6  ttys1   ttyte  ttyya
loop2      ptybd  ptyq9  ptyv5  radio0   tty48  ttyd7  ttyS1   ttytf  ttyyb
loop3      ptybe  ptyqa  ptyv6  ram0     tty49  ttyd8  ttyS10  ttyu0  ttyyc
loop4      ptybf  ptyqb  ptyv7  ram1     tty5   ttyd9  ttyS11  ttyu1  ttyyd
loop5      ptyc0  ptyqc  ptyv8  ram10    tty50  ttyda  ttyS12  ttyu2  ttyye
loop6      ptyc1  ptyqd  ptyv9  ram11    tty51  ttydb  ttyS13  ttyu3  ttyyf
loop7      ptyc2  ptyqe  ptyva  ram12    tty52  ttydc  ttyS14  ttyu4  ttyz0
lp0        ptyc3  ptyqf  ptyvb  ram13    tty53  ttydd  ttyS15  ttyu5  ttyz1
lvm        ptyc4  ptyr0  ptyvc  ram14    tty54  ttyde  ttyS16  ttyu6  ttyz2
MAKEDEV    ptyc5  ptyr1  ptyvd  ram15    tty55  ttydf  ttyS17  ttyu7  ttyz3
mapper     ptyc6  ptyr2  ptyve  ram2     tty56  ttye0  ttyS18  ttyu8  ttyz4
mcelog     ptyc7  ptyr3  ptyvf  ram3     tty57  ttye1  ttyS19  ttyu9  ttyz5
md0        ptyc8  ptyr4  ptyw0  ram4     tty58  ttye2  ttys2   ttyua  ttyz6
md1        ptyc9  ptyr5  ptyw1  ram5     tty59  ttye3  ttyS2   ttyub  ttyz7
md10       ptyca  ptyr6  ptyw2  ram6     tty6   ttye4  ttyS20  ttyuc  ttyz8
md11       ptycb  ptyr7  ptyw3  ram7     tty60  ttye5  ttyS21  ttyud  ttyz9
md12       ptycc  ptyr8  ptyw4  ram8     tty61  ttye6  ttyS22  ttyue  ttyza
md13       ptycd  ptyr9  ptyw5  ram9     tty62  ttye7  ttyS23  ttyuf  ttyzb
md14       ptyce  ptyra  ptyw6  random   tty63  ttye8  ttyS24  ttyv0  ttyzc
md15       ptycf  ptyrb  ptyw7  rtc      tty7   ttye9  ttyS25  ttyv1  ttyzd
md16       ptyd0  ptyrc  ptyw8  sda      tty8   ttyea  ttyS26  ttyv2  ttyze
md17       ptyd1  ptyrd  ptyw9  sdb      tty9   ttyeb  ttyS27  ttyv3  ttyzf
md18       ptyd2  ptyre  ptywa  sdc      ttya0  ttyec  ttyS28  ttyv4  urandom
md19       ptyd3  ptyrf  ptywb  sdd      ttya1  ttyed  ttyS29  ttyv5  vbi
md2        ptyd4  ptys0  ptywc  sg0      ttya2  ttyee  ttys3   ttyv6  vbi0
md20       ptyd5  ptys1  ptywd  sg1      ttya3  ttyef  ttyS3   ttyv7  vcs
md21       ptyd6  ptys2  ptywe  sg2      ttya4  ttyp0  ttyS30  ttyv8  vcs1
md22       ptyd7  ptys3  ptywf  sg3      ttya5  ttyp1  ttyS31  ttyv9  vcs2
md23       ptyd8  ptys4  ptyx0  shm      ttya6  ttyp2  ttyS32  ttyva  vcs3
md24       ptyd9  ptys5  ptyx1  sndstat  ttya7  ttyp3  ttyS33  ttyvb  vcs4
md3        ptyda  ptys6  ptyx2  stderr   ttya8  ttyp4  ttyS34  ttyvc  vcs5
md4        ptydb  ptys7  ptyx3  stdin    ttya9  ttyp5  ttyS35  ttyvd  vcs6
md5        ptydc  ptys8  ptyx4  stdout   ttyaa  ttyp6  ttyS36  ttyve  vcs7
md6        ptydd  ptys9  ptyx5  tty      ttyab  ttyp7  ttyS37  ttyvf  vcsa
md7        ptyde  ptysa  ptyx6  tty0     ttyac  ttyp8  ttyS38  ttyw0  vcsa1
md8        ptydf  ptysb  ptyx7  tty1     ttyad  ttyp9  ttyS39  ttyw1  vcsa2
md9        ptye0  ptysc  ptyx8  tty10    ttyae  ttypa  ttys4   ttyw2  vcsa3
mem        ptye1  ptysd  ptyx9  tty11    ttyaf  ttypb  ttyS4   ttyw3  vcsa4
net        ptye2  ptyse  ptyxa  tty12    ttyb0  ttypc  ttyS40  ttyw4  vcsa5
null       ptye3  ptysf  ptyxb  tty13    ttyb1  ttypd  ttyS41  ttyw5  vcsa6
nvidia0    ptye4  ptyt0  ptyxc  tty14    ttyb2  ttype  ttyS42  ttyw6  vcsa7
nvidiactl  ptye5  ptyt1  ptyxd  tty15    ttyb3  ttypf  ttyS43  ttyw7  video
parport0   ptye6  ptyt2  ptyxe  tty16    ttyb4  ttyq0  ttyS44  ttyw8  video0
port       ptye7  ptyt3  ptyxf  tty17    ttyb5  ttyq1  ttyS45  ttyw9  video1
ppp        ptye8  ptyt4  ptyy0  tty18    ttyb6  ttyq2  ttyS46  ttywa  xconsole
psaux      ptye9  ptyt5  ptyy1  tty19    ttyb7  ttyq3  ttyS47  ttywb  zero
ptmx       ptyea  ptyt6  ptyy2  tty2     ttyb8  ttyq4  ttys5   ttywc
pts        ptyeb  ptyt7  ptyy3  tty20    ttyb9  ttyq5  ttyS5   ttywd
ptya0      ptyec  ptyt8  ptyy4  tty21    ttyba  ttyq6  ttys6   ttywe
ptya1      ptyed  ptyt9  ptyy5  tty22    ttybb  ttyq7  ttyS6   ttywf
ptya2      ptyee  ptyta  ptyy6  tty23    ttybc  ttyq8  ttys7   ttyx0
ptya3      ptyef  ptytb  ptyy7  tty24    ttybd  ttyq9  ttyS7   ttyx1
ptya4      ptyp0  ptytc  ptyy8  tty25    ttybe  ttyqa  ttys8   ttyx2
ptya5      ptyp1  ptytd  ptyy9  tty26    ttybf  ttyqb  ttyS8   ttyx3
```

---

### Post by khelben1979 on 2009-09-05
If it was me I would install Linux on a second harddrive and try to access that harddrive from there.

---

### Post by P4man on 2009-09-05
Did ubuntu 6.06 ship with ntfs drivers? I thought not.
Can't you boot from a more recent ubuntu cd (or stick) ?

---

### Post by Kittylicious on 2009-09-05
> **P4man said:**
> Did ubuntu 6.06 ship with ntfs drivers? I thought not.
Can't you boot from a more recent ubuntu cd (or stick) ?

I don't have a more recent version... I am downloading 9.04, but at 20 kbps, it will take a while, and I REALLY would like to have this done today.

---

### Post by snl2587 on 2009-09-05
> **Kittylicious said:**
> I don't have a more recent version... I am downloading 9.04, but at 20 kbps, it will take a while, and I REALLY would like to have this done today.

The other option is the Linux System Rescue CD....the iso is much smaller and all of the latest versions have full ntfs support.

---

