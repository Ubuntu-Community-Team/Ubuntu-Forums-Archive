---
title: "fsck repair with encrypted fs"
date: 2011-02-28
forum: General Help
---

### Post by X181 on 2011-02-28
Hello

I have errors on my encrypted ext3 root partition. If I try to repair it there is a warning:
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/mapper/nb181-root is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? 


:confused: I have no idea what todo now.... Unmount my root partition is not a good idea....


Thanks for Help



Errors found:
sudo fsck -n
[sudo] password for uw: 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Warning!  /dev/mapper/nb181-root is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/mapper/nb181-root contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 7242323 was part of the orphaned inode list.  IGNORED.
Inode 7244014 was part of the orphaned inode list.  IGNORED.
Deleted inode 8658980 has zero dtime.  Fix? no

Inode 8659280 was part of the orphaned inode list.  IGNORED.
Inode 8659281 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Entry 'linc-97e-0-5285d702226b' in /tmp/orbit-uw (1138701) has deleted/unused inode 1138784.  Clear? no

Entry 'saved_state' in /home/uw/.gconfd (4857885) has deleted/unused inode 4861600.  Clear? no

Entry 'lock' in /home/uw/.mozilla/firefox/d1xmnrww.default (4858061) has deleted/unused inode 4861433.  Clear? no

Entry '%gconf.xml' in /home/uw/.gconf/system/networking/connections/10/802-11-wireless (7495695) has deleted/unused inode 7496081.  Clear? no

Entry '%gconf.xml' in /home/uw/.gconf/system/networking/connections/10/802-11-wireless-security (7495706) has deleted/unused inode 4377924.  Clear? no

Entry '%gconf.xml' in /home/uw/.gconf/system/networking/connections/10/connection (7495709) has deleted/unused inode 7496080.  Clear? no

Entry 'history-time-full-Primary-88.dat' in /var/lib/upower (7636137) has deleted/unused inode 4227090.  Clear? no

Entry 'history-rate-Primary-88.dat' in /var/lib/upower (7636137) has deleted/unused inode 7634946.  Clear? no

Entry 'history-time-empty-Primary-88.dat' in /var/lib/upower (7636137) has deleted/unused inode 4227132.  Clear? no

Entry 'hsperfdata_uw' in /tmp (8314881) has deleted/unused inode 1138771.  Clear? no

Entry 'cache_2c7f8262384b62e79117f05041609ce014bf4125.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987719.  Clear? no

Entry 'cache_7bfb891425e9839a0529b9b205af674e6f8bd967.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987715.  Clear? no

Entry 'cache_5c94fcac0162b8310349587d21d4e4d4d1357c14.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987714.  Clear? no

Entry 'cache_becdb7fc667ad61956485d2a8bf476341cfe0f18.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987735.  Clear? no

Entry 'cache_e195bb783a5afc98de579f0556d2568251c2e1c9.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987778.  Clear? no

Entry 'cache_5e18993a374183f2fd8dde10bbe367614262db92.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987720.  Clear? no

Entry 'cache_ce0e7cdb689fdb12e6e5b119ebb466fbc5d8d72f.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987791.  Clear? no

Entry 'cache_d64606eb4f0a1106ea2ff20872a67eaaebeb43c0.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987718.  Clear? no

Entry 'cache_b4b182b645ede18c91911876615a7f961611b178.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987717.  Clear? no

Entry 'cache_eb26330c4a5ce340d17351adbe09c93a19d888fe.cache' in /home/uw/.cache/Zattoo/http (7987286) has deleted/unused inode 7987793.  Clear? no

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached zero-length inode 1901833.  Clear? no

Unattached inode 1901833
Connect to /lost+found? no

Unattached zero-length inode 7496068.  Clear? no

Unattached inode 7496068
Connect to /lost+found? no

Unattached zero-length inode 7496072.  Clear? no

Unattached inode 7496072
Connect to /lost+found? no

Unattached zero-length inode 7634945.  Clear? no

Unattached inode 7634945
Connect to /lost+found? no

Unattached zero-length inode 7634957.  Clear? no

Unattached inode 7634957
Connect to /lost+found? no

Unattached zero-length inode 7634958.  Clear? no

Unattached inode 7634958
Connect to /lost+found? no

Inode 8314881 ref count is 16, should be 15.  Fix? no

Pass 5: Checking group summary information
Block bitmap differences:  -(3311702--3311703) -3311710 -3311718 -4576086 +(7616750--761675 -16718414 -(16912422--16912423) -17507032 +19441680 +(19441682--19441694) +(19441697--19441701) +19441703 +19441729 -19443713 +19443714 +19443730 -19443743 -(19443754--19443755) -19443757 -(19443759--19443770) -(19443779--19443780) -(19443786--1944378 -(19443801--19443802) -19460128 -19460173 +(19460240--19460243) +(19460249--19460252) +19460399 -19460481 -19460491 -19460533 +(19460596--19460597) +19460603 -19460605 +19460667 -(19460681--19460682) +(19460757--1946075 -19460810 -(19460841--19460842) -19460844 +(19460845--19460846) -19460857 -19460859 +(19460877--1946087 +19460885 -(19461143--19461144) -19461263 -19461268 -19461281 -(19461285--19461287) -19461346 -(19461348--19461360) -(19461364--19461367) +19461368 -(19461373--19461391) -(19461405--19461412) -(19461426--19461427) -19461437 -(19461439--19461464) -(19461467--19461490) -(19461544--19461546) -19462061 -(19462063--19462064) -(19462081--19462087) -(19462092--19462093) -19462096 -(19462102--19462103) -(19462246--19462249) -19462270 -19462281 -19462288 -19462331 -(19462370--19462374) -(19462377--1946237 -19462382 -19462406 -(19462414--19462415) -19462829 -19462845 -19462889 -19462904 -19462911 -19462913 -19462923 -(19462930--19462931) -19462960 -19462963 -19462967 -19463025 -19463769 -(19464113--19464114) -19464775 -19466449 -(19467512--19467515) -19467520 -19467588 -19467601 -19467637 -19467642 -19467644 -(19467685--19467686) -19467726 -(19467742--19467743) -(19467746--19467747) -19467767 -19468938 -19468942 -19468946 -(19468950--19468951) -19469481 -19469485 -(19470141--19470143) -19470145 -(19470148--19470149) -(19470151--19470152) -(19470154--19470155) -19470157 -(19470159--19470160) -(19470162--19470166) -19470168 -19470176 -19470238 -(19470253--1947025 -19470267 -(19470269--19470270) -19470274 -19470924 -(19470926--19470927) -(19471250--19471253) -19471255 -19471259 -(19471264--19471276) -19471282 -(19489731--19489734) -19493362 -(19493440--19493491) -(19493544--19493681) -(19493683--1949368 -(19493690--19493692) -(19493704--19493711) -(19493713--19493714) -(19493716--19493734) -(19493738--19493743) -(19493760--19493781) -(19493784--19493792) -(19493794--19493815) -29856703 -(29856707--29856710) -29856805 -29874365 -29958773 -29958834 -29965206 -(29965340--29965341) -29965343 -29965676 -29967451 -29967458 -(29967467--29967473) -29967481 -29967491 -(29967496--2996749 -(29967519--29967523) -29967526 -29967581 -29967601 -(29967603--29967615) +29991133 -29997057 -29997398 +30045444 -30554115 -30554130 -(30557978--30557980) -(30557982--30557983) -(30576725--30576726) +(30576727--30576732) -(30576733--3057674 -(30599178--30599193) -(30599195--30599200) +(30621700--30621703) +30789654 +(30789668--30789669) +(30789675--30789683) +(30819559--30819560) +(30819562--30819564) +(30840856--30840857) +30840859 +30840867 +30842928 +(30844933--30844937) +(30868442--30868452) +(30875649--30875650) +(30892067--30892070) +(30892099--30892110) +(30892156--30892157) +(30900738--30900755) -31969385 -31969389 -31969393 -(31969395--31969400) -31969402 -(31969404--3196940 -(31969410--31969411) -(31969422--31969424) -(31969436--31969447) -31969452 -(31969469--31969470) -(31969595--31969596) -(31969617--31969620) -31969635 -31969637 +(31997736--31997737) +(31997742--31997744) -(31997749--31997759) -31997775 -(31997896--3199789 +(32526404--32526405) +(32526415--3252641
Fix? no

Free blocks count wrong for group #101 (13, counted=11).
Fix? no

Free blocks count wrong for group #139 (3347, counted=3345).
Fix? no

Free blocks count wrong for group #140 (5688, counted=5687).
Fix? no

Free blocks count wrong for group #232 (29194, counted=29209).
Fix? no

Free blocks count wrong for group #510 (5154, counted=5153).
Fix? no

Free blocks count wrong for group #516 (28078, counted=28076).
Fix? no

Free blocks count wrong for group #534 (25646, counted=25645).
Fix? no

Free blocks count wrong for group #593 (842, counted=689).
Fix? no

Free blocks count wrong for group #594 (553, counted=180).
Fix? no

Free blocks count wrong for group #915 (0, counted=1).
Fix? no

Free blocks count wrong for group #932 (7, counted=0).
Fix? no

Free blocks count wrong for group #933 (40, counted=6).
Fix? no

Free blocks count wrong for group #934 (0, counted=4).
Fix? no

Free blocks count wrong for group #939 (0, counted=12).
Fix? no

Free blocks count wrong for group #940 (0, counted=5).
Fix? no

Free blocks count wrong for group #941 (0, counted=10).
Fix? no

Free blocks count wrong for group #942 (0, counted=31).
Fix? no

Free blocks count wrong for group #943 (0, counted=18).
Fix? no

Free blocks count wrong for group #975 (0, counted=29).
Fix? no

Free blocks count wrong for group #976 (62, counted=58).
Fix? no

Free blocks count wrong for group #981 (80, counted=93).
Fix? no

Free blocks count wrong for group #992 (45, counted=51).
Fix? no

Free blocks count wrong (13156295, counted=13157088).
Fix? no

Inode bitmap differences:  -1138771 -1138784 +1901833 -4227090 -4227132 -4377924 -4861433 -4861600 -7242323 -7244014 +7496068 +7496072 -(7496080--7496081) +7634945 -7634946 +(7634957--7634958) -(7987714--7987715) -(7987717--7987720) -7987735 -7987778 -7987791 -7987793 -8658980 -(8659280--8659281)
Fix? no

Free inodes count wrong for group #139 (8098, counted=8094).
Fix? no

Directories count wrong for group #139 (18, counted=19).
Fix? no

Free inodes count wrong for group #232 (5721, counted=5727).
Fix? no

Free inodes count wrong for group #516 (5839, counted=5837).
Fix? no

Free inodes count wrong for group #534 (4797, counted=4796).
Fix? no

Free inodes count wrong for group #593 (3060, counted=305.
Fix? no

Free inodes count wrong for group #915 (7480, counted=7481).
Fix? no

Free inodes count wrong for group #932 (6858, counted=6860).
Fix? no

Free inodes count wrong for group #975 (4630, counted=4676).
Fix? no

Free inodes count wrong for group #1057 (7844, counted=7843).
Fix? no

Free inodes count wrong (9006506, counted=9006516).
Fix? no


/dev/mapper/nb181-root: ********** WARNING: Filesystem still has errors **********

/dev/mapper/nb181-root: 348758/9355264 files (3.5% non-contiguous), 24258617/37414912 blocks
uw@nb181:~$

---

### Post by X181 on 2011-03-11
Source: [http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

In short:
- Get a ubuntu live cd from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
- open a terminal
- sudo apt-get update && sudo apt-get install lvm2 cryptsetup
- sudo modprobe dm-crypt
- sudo cryptsetup luksOpen /dev/sda5 crypt1
- sudo vgscan --mknodes
- sudo vgchange -ay
- sudo e2fsck /dev/dm-2 OR sudo fsck /dev/dm-2

/dev/sda5 and /dev/dm-2 is specific to your setup 

for a overview over your partions start System-->Administration-->Disk Utility or GParted Partition Editor

---

