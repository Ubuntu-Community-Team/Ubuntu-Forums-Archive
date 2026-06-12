---
title: "How to use filefrag"
date: 2009-12-05
forum: General Help
---

### Post by ssulaco on 2009-12-05
I know,...ext3 frags very little,but I would still like to keep an eye on it,
Ive been running the command ```
filefrag -v
```
but not having any luck
```
john@john-desktop:~$ filefrag -v Docs
Checking Docs
statfs: No such file or directory
john@john-desktop:~$ filefrag -v /Docs
Checking /Docs
statfs: No such file or directory
john@john-desktop:~$ filefrag -v pictures
Checking pictures
statfs: No such file or directory
john@john-desktop:~$ filefrag -v Pictures
Checking Pictures
Pictures: Not a regular file
john@john-desktop:~$ 

```
Ive tried sudo also but no luck,any help would be much appreciated,Id like to be able to check the whole drive ....Thanks

---

### Post by lisati on 2009-12-05
Does it work when you give it a single file name to use instead of a folder name?

---

### Post by Shazaam on 2009-12-05
How about using the full path?...
```
filefrag -v /home/john/Pictures

```

---

### Post by ssulaco on 2009-12-05
> **Shazaam said:**
> How about using the full path?...
```
filefrag -v /home/john/Pictures

``` 
same message:no such file or directory

> **lisati said:**
> Does it work when you give it a single file name to use instead of a folder name?
No,I cant seem to get it to work........would be really cool if you could run:  filefrag -v /  and check the whole drive.
when i was running jaunty,and in the Grub menu,under recovery mode,there was an option for FSCK,I would run it and after the check was done it gave in percentage "non-contiguous files"
In hardy,there is no option FSCK under recovery mode,is there a way I could add the FSCK in recovery mode in Hardy Heron?
I can run the command: sudo touch /forcefsck  and the file sys check runs fine,but wont list the amount of  non-contiguous files,course Jaunty wouldnt either if you forced a fsck.
Thanks

---

### Post by NoaHall on 2009-12-05
Try```
 sudo filefrag -v /*
```

Also, there's no need at all to "defrag" your system as it uses a journalling file system.

---

### Post by ibuclaw on 2009-12-05
> **NoaHall said:**
> Try```
 sudo filefrag -v /*
```

Also, there's no need at all to "defrag" your system as it uses a journalling file system.

NTFS is Journaling File System - but apparently you need to defrag that every once in a while...

The OP made no intent on defragging his file system. He is just curious on how to monitor it.


ssulaco, you can't run that on a directory - as it will only stat the directory, and none of the *contents*.
The command "find" should suffice.
```
sudo find ~ -exec filefrag "{}" \; | grep -v "[012345] extent"
```
The "grep" command makes it so that only files with more than 5 extents are printed in the terminal.

From there, you can monitor those individual files.
ie:
```
**sudo filefrag -v Downloads/jolicloud-robby-alpha2c-live.iso**
[I]Filesystem type is: ef53
File size of Downloads/jolicloud-robby-alpha2c-live.iso is 629145600 (153600 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0    51200            2048 
   1    2048   237441    53247    384 
   2    2432    76160   237824    512 
   3    3072    76800    76671   1152 
   4    4224    53376    77951   2048 
   5    6272    77952    55423   1920 
   6    8192    67456    79871    128 
   7    8320    55424    67583   1028 
   8    9348   230981    56451    380 
   9    9728    56832   231360    160 
  10    9888    34424    56991     92 
  11    9980    57084    34515    300 
  12   10280   231361    57383    472 
  13   10752    57856   231832   1840 
  14   12592   230401    59695    336 
  15   12928    60032   230736   2560 
  16   15488   234821    62591    408 
  17   15896    63000   235228    488 
  18   16384    67716    63487    136 
  19   16520    63624    67851    760 
  20   17280   231833    64383    384 
  21   17664    64768   232216     16 
  22   17680    35113    64783    112 
  23   17792    64896    35224    384 
  24   18176    35968    65279    128 
  25   18304    65408    36095    128 
  26   18432   237825    65535    768 
  27   19200    66304   238592    144 
  28   19344   232217    66447    828 
  29   20172    67276   233044    180 
  30   20352    67584    67455    128 
  31   20480    79872    67711   2176 
  32   22656    67712    82047      4 
  33   22660    71424    67715    252 
  34   22912    67968    71675    256 
  35   23168   234093    68223    396 
  36   23564    68620   234488    536 
  37   24100   235229    69155    476 
  38   24576    69632   235704     20 
  39   24596   235981    69651    236 
  40   24832    69888   236216   1536 
  41   26368    68352    71423    256 
  42   26624    69376    68607    256 
  43   26880    71936    69631    640 
  44   27520    69652    72575    160 
  45   27680    72736    69811     12 
  46   27692    67872    72747     80 
  47   27772    72828    67951    132 
  48   27904    67852    72959     20 
  49   27924    72980    67871    748 
  50   28672    83968    73727    964 
  51   29636   233045    84931    316 
  52   29952    85248   233360    128 
  53   30080    66048    85375    132 
  54   30212    85508    66179     20 
  55   30232   246912    85527    360 
  56   30592    85888   247271    128 
  57   30720    86144    86015    256 
  58   30976   233361    86399    384 
  59   31360    86784   233744   1408 
  60   32768    90112    88191    632 
  61   33400    67232    90743     36 
  62   33436    90780    67267    920 
  63   34356   234489    91699    332 
  64   34688    92032   234820    128 
  65   34816    94208    92159    224 
  66   35040    67072    94431    160 
  67   35200    94592    67231    384 
  68   35584    69156    94975    196 
  69   35780    95172    69351    448 
  70   36228    66180    95619     28 
  71   36256    95648    66207      8 
  72   36264    66448    95655    104 
  73   36368    95760    66551    660 
  74   37028   233745    96419    348 
  75   37376    96768   234092   1536 
  76   38912   100352    98303    256 
  77   39168   106752   100607    256 
  78   39424   100864   107007    128 
  79   39552   100608   100991    256 
  80   39808   101248   100863   1792 
  81   41600    99584   103039    256 
  82   41856   103296    99839   3208 
  83   45064   108552   106503    548 
  84   45612   230737   109099    244 
  85   45856   109344   230980   1120 
  86   46976   110720   110463    128 
  87   47104   110592   110847    128 
  88   47232   235705   110719    276 
  89   47508   110996   235980    624 
  90   48132   109100   111619    168 
  91   48300   111788   109267    852 
  92   49152   103040   112639    128 
  93   49280   112768   103167   4608 
  94   53888   236217   117375    296 
  95   54184   117672   236512   1240 
  96   55424   106504   118911    208 
  97   55632   119120   106711    944 
  98   56576   110464   120063    128 
  99   56704   120192   110591    256 
 100   56960   120704   120447    384 
 101   57344    99840   121087    256 
 102   57600   121088   100095    512 
 103   58112    99456   121599    128 
 104   58240   121728    99583   1152 
 105   59392   245760   122879   1152 
 106   60544   124032   246911     96 
 107   60640    99360   124127     32 
 108   60672   124160    99391   2304 
 109   62976   100992   126463    156 
 110   63132   126620   101147   3172 
 111   66304   103168   129791    128 
 112   66432   129920   103295   1152 
 113   67584   133760   131071    128 
 114   67712   131200   133887   2304 
 115   70016   131072   133503    128 
 116   70144   133632   131199    128 
 117   70272   236513   133759    640 
 118   70912   134400   237152    768 
 119   71680   249568   135167    640 
 120   72320   135808   250207   1408 
 121   73728   137216            1664 
 122   75392   250208   138879    384 
 123   75776   139264   250591   2816 
 124   78592   237153   142079    288 
 125   78880   142368   237440    608 
 126   79488   247272   142975    384 
 127   79872   143360   247655   1920 
 128   81792   145288   145279    128 
 129   81920   133888   145415    256 
 130   82176   145664   134143   2176 
 131   84352   247656   147839    640 
 132   84992   148480   248295   1412 
 133   86404   248296   149891    284 
 134   86688   150176   248579   1376 
 135   88064   142080   151551    256 
 136   88320   151808   142335   1408 
 137   89728   134144   153215    256 
 138   89984   153472   134399    256 
 139   90240   153728             640 
 140   90880   139008   154367    256 
 141   91136   154624   139263   1024 
 142   92160   156028   155647    384 
 143   92544   248580   156411    384 
 144   92928   156796   248963    128 
 145   93056   133504   156923    128 
 146   93184   157052   133631   1024 
 147   94208   159744   158075   2304 
 148   96512   248964   162047    604 
 149   97116   162652   249567    676 
 150   97792   143104   163327    256 
 151   98048   163584   143359    256 
 152   98304   165517   163839    132 
 153   98436   166020   165648   1276 
 154   99712   164992   167295    128 
 155   99840   167424   165119   2176 
 156  102016   253436   169599    384 
 157  102400   169984   253819   1536 
 158  103936   250592   171519    288 
 159  104224   171808   250879    480 
 160  104704   172544   172287    128 
 161  104832   250880   172671    384 
 162  105216   173056   251263   1280 
 163  106496   176128   174335   5888 
 164  112384   165888   182015    128 
 165  112512   182144   166015    640 
 166  113152   183296   182783    256 
 167  113408   165120   183551    256 
 168  113664   183808   165375   1024 
 169  114688   184836   184831    128 
 170  114816   185088   184963   1280 
 171  116096   169728   186367    256 
 172  116352   186624   169983    640 
 173  116992   187520   187263   1152 
 174  118144   171520   188671    256 
 175  118400   188928   171775    384 
 176  118784   189372   189311    128 
 177  118912   189568   189499    128 
 178  119040   172288   189695    256 
 179  119296   189952   172543    128 
 180  119424   172800   190079    256 
 181  119680   190336   173055   1152 
 182  120832   191552   191487    128 
 183  120960   192640   191679   3072 
 184  124032   251264   195711    384 
 185  124416   196096   251647    596 
 186  125012   197608   196691     24 
 187  125036   196716   197631    284 
 188  125320   251648   196999    248 
 189  125568   197248   251895    360 
 190  125928   197788   197607     24 
 191  125952   197632   197811    156 
 192  126108   198432   197787     32 
 193  126140   197820   198463    584 
 194  126724   251896   198403    252 
 195  126976   198656   252147    896 
 196  127872   252532   199551    384 
 197  128256   199936   252915    256 
 198  128512   199680   200191    256 
 199  128768   200448   199935   5120 
 200  133888   252148   205567    384 
 201  134272   205952   252531    128 
 202  134400   252916   206079    520 
 203  134920   206600   253435   6136 
 204  141056   198528   212735    128 
 205  141184   212864   198655   2176 
 206  143360   215168   215039    132 
 207  143492   215304   215299   1404 
 208  144896   216836   216707    512 
 209  145408   217476   217347    768 
 210  146176   219904   218243   1280 
 211  147456   199552   221183    128 
 212  147584   221312   199679   2748 
 213  150332   196692   224059     12 
 214  150344   224072   196703     20 
 215  150364   197000   224091    164 
 216  150528   224256   197163   2688 
 217  153216   200192   226943    256 
 218  153472   227200   200447    128 eof
Downloads/jolicloud-robby-alpha2c-live.iso: 217 extents found[/I]

```

Regards
Iain

---

### Post by ssulaco on 2009-12-05
> **tinivole said:**
> 
The command "find" should suffice.
```
sudo find ~ -exec filefrag "{}" \; | grep -v "[012345] extent"
```

tinivole,i ran your command and seemed to only list my /home dir,when it finished I could not scroll up to the beginning,all the files i could see listed gave the same output:  "not a regular file"

> **NoaHall said:**
> Try```
 sudo filefrag -v /*
```

Noahall the output of your command:
```
john@john-desktop:~$ sudo filefrag -v /*Checking /bin
/bin: Not a regular file
Checking /boot
/boot: Not a regular file
Checking /cdrom
/cdrom: Not a regular file
Checking /dev
/dev: Not a regular file
Checking /etc
/etc: Not a regular file
Checking /home
/home: Not a regular file
Checking /initrd
/initrd: Not a regular file
Checking /initrd.img
Filesystem type is: ef53
Filesystem cylinder groups is approximately 218
Blocksize of file /initrd.img is 4096
File size of /initrd.img is 7502569 (1832 blocks)
First block: 3909632
Last block: 3911466
/initrd.img: 1 extent found
Checking /initrd.img.old
Filesystem type is: ef53
Filesystem cylinder groups is approximately 218
Blocksize of file /initrd.img.old is 4096
File size of /initrd.img.old is 7503057 (1832 blocks)
First block: 3911680
Last block: 3913514
/initrd.img.old: 1 extent found
Checking /lib
/lib: Not a regular file
Checking /lost+found
/lost+found: Not a regular file
Checking /media
/media: Not a regular file
Checking /mnt
/mnt: Not a regular file
Checking /opt
/opt: Not a regular file
Checking /proc
/proc: Not a regular file
Checking /root
/root: Not a regular file
Checking /sbin
/sbin: Not a regular file
Checking /srv
/srv: Not a regular file
Checking /sys
/sys: Not a regular file
Checking /tmp
/tmp: Not a regular file
Checking /usr
/usr: Not a regular file
Checking /var
/var: Not a regular file
Checking /vmlinuz
Filesystem type is: ef53
Filesystem cylinder groups is approximately 218
Blocksize of file /vmlinuz is 4096
File size of /vmlinuz is 1926424 (471 blocks)
First block: 3901442
Last block: 3901913
/vmlinuz: 1 extent found
Checking /vmlinuz.old
Filesystem type is: ef53
Filesystem cylinder groups is approximately 218
Blocksize of file /vmlinuz.old is 4096
File size of /vmlinuz.old is 1926456 (471 blocks)
First block: 3928888
Last block: 3929359
/vmlinuz.old: 1 extent found
john@john-desktop:~$ 

```
not sure how to decipher this.
Thanks

---

### Post by ibuclaw on 2009-12-06
> **ssulaco said:**
> tinivole,i ran your command and seemed to only list my /home dir,when it finished I could not scroll up to the beginning,all the files i could see listed gave the same output:  "not a regular file"


You can redirect output to a file
```
sudo find ~ -exec filefrag "{}" \; | grep -v "[012345] extent" > filefrag.txt
```
or to a buffer
```
sudo find ~ -exec filefrag "{}" \; | grep -v "[012345] extent" | less
```
Either way, both instances will allow you to see the top right down to the bottom of the list.

And yes, it will only home, because the tilda "~" means your home directory.
For anywhere else, use another location.

Regards
Iain

---

### Post by ssulaco on 2009-12-06
> **ssulaco said:**
> 
when i was running jaunty,and in the Grub menu,under recovery mode,there was an option for FSCK,I would run it and after the check was done it gave in percentage "non-contiguous files"
In hardy,there is no option FSCK under recovery mode,is there a way I could add the FSCK in recovery mode in Hardy Heron?
I can run the command: sudo touch /forcefsck  and the file sys check runs fine,but wont list the amount of  non-contiguous files,course Jaunty wouldnt either if you forced a fsck.
Thanks
tinivole,is there a way i could add the fsck option under recovery mode in Hardy?and if i could,would it display % non-contiguous files?
the fsck option in jaunty was sufficient in letting me know frag %.Thanks for your time on this.

---

### Post by ibuclaw on 2009-12-06
> **ssulaco said:**
> tinivole,is there a way i could add the fsck option under recovery mode in Hardy?and if i could,would it display % non-contiguous files?
the fsck option in jaunty was sufficient in letting me know frag %.Thanks for your time on this.

Yes, there is.
```
gksu gedit /usr/share/recovery-mode/options/fsck
```
And paste in the following:
```

#!/bin/sh

. /usr/share/recovery-mode/l10n.sh

set -e

if [ "$1" = "test" ]; then
  echo $(eval_gettext "Reboot into file system check")
  exit 0
fi

# forcefsck will trigger a fsck by mountall on the next 
# reboot
touch /forcefsck
reboot

```
And save + reboot.

Regards
Iain

---

### Post by ssulaco on 2009-12-06
I ran the command and saved the script,but after I rebooted,I still only had the four options in recovery mode:

Resume normal boot
Repair broken packages
Drop to root shell prompt
Try to fix X server

---

### Post by ibuclaw on 2009-12-07
> **ssulaco said:**
> I ran the command and saved the script,but after I rebooted,I still only had the four options in recovery mode:

Resume normal boot
Repair broken packages
Drop to root shell prompt
Try to fix X server

Oops, looks like I forgot about making it executable:
```
sudo chmod +x /usr/share/recovery-mode/options/fsck
```

Regards
Iain

---

### Post by ssulaco on 2009-12-07
tinivole,I ran the last command you gave me to make it executable,its in the "options" folder along with dpkg,root & xfix,but its still not showing up in recovery mode.

---

### Post by ibuclaw on 2009-12-08
> **ssulaco said:**
> tinivole,I ran the last command you gave me to make it executable,its in the "options" folder along with dpkg,root & xfix,but its still not showing up in recovery mode.

I see no reason why it shouldn't. It works my end both with the Karmic and Hardy menu script.

Running:
```
/usr/share/recovery-mode/recovery-menu
```
will run the recovery menu in a terminal so you can preview the change without rebooting.

Regards
Iain

---

### Post by ssulaco on 2009-12-08
tinivole,its not a big deal if it doesnt work,like i said earlier,I can always force a fsck,and I never ran over .8% non-contiguous in Jaunty.
I do appreciate your help on this,Thanks

---

### Post by ssulaco on 2009-12-24
tinivole,came across this command that works great,...boot into your live cd and run this
```
sudo fsck -f /dev/sdxx
```
where xx is drive and partition,mine was sda1
gives you % of non-contiguous files

---

