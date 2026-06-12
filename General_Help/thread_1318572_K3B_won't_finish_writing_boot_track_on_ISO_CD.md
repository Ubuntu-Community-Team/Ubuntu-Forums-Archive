---
title: "K3B won't finish writing boot track on ISO CD"
date: 2009-11-07
forum: General Help
---

### Post by arvevans on 2009-11-07
Since installing Ubuntu (Gnome) 9.10 on my AMD Dual-Core-64 3800 computer K3B will not finish writing the boot track when making an ISO copy.

DEBUG INFO FROM K3B:
[INDENT]Devices
-----------------------
Optiarc DVD RW AD-7170A 1.02 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::DataTrackReader
-----------------------
reading sectors 0 to 340050 with sector size 2048. Length: 340051 sectors, 696424448 bytes.
using buffer size of 64 blocks.
Read a total of 340051 sectors (696424448 bytes)

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-14-generic

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Optiarc '
Identification : 'DVD RW AD-7170A '
Revision       : '1.02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) (current)
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 890880 = 870 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 8467 KB/s
Track 01: data   664 MB        
Total size:      762 MB (75:34.01) = 340051 sectors
Lout start:      763 MB (75:36/01) = 340051 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 19798
Starting to write CD/DVD at speed  48.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  664 MB written.
Track 01:    1 of  664 MB written (fifo 100%) [buf 100%]   0.7x.
Track 01:    2 of  664 MB written (fifo 100%) [buf 100%]   6.4x.
Track 01:    3 of  664 MB written (fifo 100%) [buf 100%]  22.4x.
Track 01:    4 of  664 MB written (fifo 100%) [buf 100%]  21.7x.
Track 01:    5 of  664 MB written (fifo 100%) [buf 100%]  22.5x.
Track 01:    6 of  664 MB written (fifo 100%) [buf 100%]  21.8x.
Track 01:    7 of  664 MB written (fifo 100%) [buf 100%]  22.6x.
Track 01:    8 of  664 MB written (fifo 100%) [buf 100%]  21.9x.
Track 01:    9 of  664 MB written (fifo 100%) [buf 100%]  22.6x.
Track 01:   10 of  664 MB written (fifo 100%) [buf 100%]  22.0x.
Track 01:   11 of  664 MB written (fifo 100%) [buf 100%]  22.7x.
Track 01:   12 of  664 MB written (fifo 100%) [buf 100%]  22.1x.
Track 01:   13 of  664 MB written (fifo 100%) [buf 100%]  22.9x.
Track 01:   14 of  664 MB written (fifo  99%) [buf 100%]  22.1x.
Track 01:   15 of  664 MB written (fifo 100%) [buf 100%]  22.9x.
Track 01:   16 of  664 MB written (fifo 100%) [buf 100%]  22.3x.
Track 01:   17 of  664 MB written (fifo 100%) [buf 100%]  23.0x.
Track 01:   18 of  664 MB written (fifo  99%) [buf 100%]  22.3x.
Track 01:   19 of  664 MB written (fifo 100%) [buf 100%]  23.1x.
Track 01:   20 of  664 MB written (fifo 100%) [buf 100%]  22.5x.
Track 01:   21 of  664 MB written (fifo 100%) [buf 100%]  23.1x.
Track 01:   22 of  664 MB written (fifo 100%) [buf 100%]  22.6x.
Track 01:   23 of  664 MB written (fifo 100%) [buf 100%]  23.2x.
Track 01:   24 of  664 MB written (fifo 100%) [buf 100%]  22.6x.
Track 01:   25 of  664 MB written (fifo 100%) [buf 100%]  23.4x.
Track 01:   26 of  664 MB written (fifo 100%) [buf 100%]  22.7x.
Track 01:   27 of  664 MB written (fifo 100%) [buf 100%]  23.4x.
Track 01:   28 of  664 MB written (fifo 100%) [buf 100%]  22.8x.
Track 01:   29 of  664 MB written (fifo 100%) [buf 100%]  23.4x.
Track 01:   30 of  664 MB written (fifo  99%) [buf 100%]  22.8x.
Track 01:   31 of  664 MB written (fifo 100%) [buf 100%]  23.6x.
Track 01:   32 of  664 MB written (fifo 100%) [buf 100%]  22.9x.
Track 01:   33 of  664 MB written (fifo 100%) [buf 100%]  23.4x.
Track 01:   34 of  664 MB written (fifo 100%) [buf 100%]  24.6x.
Track 01:   35 of  664 MB written (fifo 100%) [buf 100%]  23.7x.
Track 01:   36 of  664 MB written (fifo 100%) [buf 100%]  24.5x.
Track 01:   37 of  664 MB written (fifo 100%) [buf 100%]  23.7x.
Track 01:   38 of  664 MB written (fifo  99%) [buf 100%]  24.6x.
Track 01:   39 of  664 MB written (fifo 100%) [buf 100%]  23.8x.
Track 01:   40 of  664 MB written (fifo 100%) [buf 100%]  24.6x.
Track 01:   41 of  664 MB written (fifo 100%) [buf 100%]  23.9x.
Track 01:   42 of  664 MB written (fifo 100%) [buf 100%]  24.8x.
Track 01:   43 of  664 MB written (fifo 100%) [buf 100%]  24.0x.
Track 01:   44 of  664 MB written (fifo  99%) [buf 100%]  24.8x.
Track 01:   45 of  664 MB written (fifo 100%) [buf 100%]  24.1x.
Track 01:   46 of  664 MB written (fifo 100%) [buf 100%]  24.9x.
Track 01:   47 of  664 MB written (fifo 100%) [buf 100%]  24.1x.
Track 01:   48 of  664 MB written (fifo 100%) [buf 100%]  24.9x.
Track 01:   49 of  664 MB written (fifo 100%) [buf 100%]  24.2x.
Track 01:   50 of  664 MB written (fifo  99%) [buf 100%]   6.9x.
Track 01:   51 of  664 MB written (fifo  99%) [buf 100%]  24.3x.
Track 01:   52 of  664 MB written (fifo 100%) [buf 100%]  25.1x.
Track 01:   53 of  664 MB written (fifo 100%) [buf 100%]  24.4x.
Track 01:   54 of  664 MB written (fifo 100%) [buf 100%]  25.2x.
Track 01:   55 of  664 MB written (fifo 100%) [buf 100%]  24.4x.
Track 01:   56 of  664 MB written (fifo  99%) [buf 100%]  25.0x.
Track 01:   57 of  664 MB written (fifo  99%) [buf 100%]  24.7x.
Track 01:   58 of  664 MB written (fifo 100%) [buf 100%]  25.2x.
Track 01:   59 of  664 MB written (fifo 100%) [buf 100%]  24.6x.
Track 01:   60 of  664 MB written (fifo 100%) [buf 100%]  25.4x.
Track 01:   61 of  664 MB written (fifo 100%) [buf 100%]  24.6x.
Track 01:   62 of  664 MB written (fifo 100%) [buf 100%]  25.4x.
Track 01:   63 of  664 MB written (fifo 100%) [buf 100%]  24.7x.
Track 01:   64 of  664 MB written (fifo  99%) [buf 100%]  25.5x.
Track 01:   65 of  664 MB written (fifo 100%) [buf 100%]  26.3x.
Track 01:   66 of  664 MB written (fifo 100%) [buf 100%]  25.5x.
Track 01:   67 of  664 MB written (fifo 100%) [buf 100%]  26.3x.
Track 01:   68 of  664 MB written (fifo 100%) [buf 100%]  25.6x.
Track 01:   69 of  664 MB written (fifo 100%) [buf 100%]  26.4x.
Track 01:   70 of  664 MB written (fifo 100%) [buf 100%]  25.6x.
Track 01:   71 of  664 MB written (fifo 100%) [buf 100%]  26.4x.
Track 01:   72 of  664 MB written (fifo 100%) [buf 100%]  25.7x.
Track 01:   73 of  664 MB written (fifo 100%) [buf 100%]  26.6x.
Track 01:   74 of  664 MB written (fifo  99%) [buf 100%]  25.8x.
Track 01:   75 of  664 MB written (fifo 100%) [buf 100%]  26.7x.
Track 01:   76 of  664 MB written (fifo 100%) [buf 100%]  25.8x.
Track 01:   77 of  664 MB written (fifo 100%) [buf 100%]  26.7x.
Track 01:   78 of  664 MB written (fifo 100%) [buf 100%]  25.9x.
Track 01:   79 of  664 MB written (fifo  99%) [buf 100%]  26.8x.
Track 01:   80 of  664 MB written (fifo 100%) [buf 100%]  25.9x.
Track 01:   81 of  664 MB written (fifo 100%) [buf 100%]  26.8x.
Track 01:   82 of  664 MB written (fifo 100%) [buf 100%]  26.0x.
Track 01:   83 of  664 MB written (fifo 100%) [buf 100%]  26.9x.
Track 01:   84 of  664 MB written (fifo 100%) [buf 100%]  25.9x.
Track 01:   85 of  664 MB written (fifo 100%) [buf 100%]  27.1x.
Track 01:   86 of  664 MB written (fifo 100%) [buf 100%]  26.1x.
Track 01:   87 of  664 MB written (fifo 100%) [buf 100%]  27.0x.
Track 01:   88 of  664 MB written (fifo  99%) [buf 100%]  26.2x.
Track 01:   89 of  664 MB written (fifo 100%) [buf 100%]  26.9x.
Track 01:   90 of  664 MB written (fifo 100%) [buf 100%]  26.4x.
Track 01:   91 of  664 MB written (fifo 100%) [buf 100%]  27.1x.
Track 01:   92 of  664 MB written (fifo 100%) [buf 100%]  26.3x.
Track 01:   93 of  664 MB written (fifo 100%) [buf 100%]  27.1x.
Track 01:   94 of  664 MB written (fifo 100%) [buf 100%]  26.4x.
Track 01:   95 of  664 MB written (fifo 100%) [buf 100%]  27.2x.
Track 01:   96 of  664 MB written (fifo 100%) [buf 100%]  28.0x.
Track 01:   97 of  664 MB written (fifo 100%) [buf 100%]  27.2x.
Track 01:   98 of  664 MB written (fifo 100%) [buf 100%]  28.1x.
Track 01:   99 of  664 MB written (fifo 100%) [buf 100%]  27.2x.
Track 01:  100 of  664 MB written (fifo 100%) [buf 100%]  28.2x.
Track 01:  101 of  664 MB written (fifo 100%) [buf 100%]  27.4x.
Track 01:  102 of  664 MB written (fifo 100%) [buf 100%]  28.2x.
Track 01:  103 of  664 MB written (fifo 100%) [buf 100%]  27.4x.
Track 01:  104 of  664 MB written (fifo  99%) [buf 100%]  28.2x.
Track 01:  105 of  664 MB written (fifo 100%) [buf 100%]  27.5x.
Track 01:  106 of  664 MB written (fifo 100%) [buf 100%]  28.3x.
Track 01:  107 of  664 MB written (fifo 100%) [buf 100%]  27.5x.
Track 01:  108 of  664 MB written (fifo 100%) [buf 100%]  28.4x.
Track 01:  109 of  664 MB written (fifo  99%) [buf 100%]  27.6x.
Track 01:  110 of  664 MB written (fifo 100%) [buf 100%]  28.3x.
Track 01:  111 of  664 MB written (fifo  99%) [buf 100%]  27.7x.
Track 01:  112 of  664 MB written (fifo 100%) [buf 100%]  28.4x.
Track 01:  113 of  664 MB written (fifo  99%) [buf 100%]  27.7x.
Track 01:  114 of  664 MB written (fifo 100%) [buf 100%]  28.3x.
Track 01:  115 of  664 MB written (fifo 100%) [buf 100%]  27.8x.
Track 01:  116 of  664 MB written (fifo 100%) [buf 100%]  28.5x.
Track 01:  117 of  664 MB written (fifo 100%) [buf 100%]  27.8x.
Track 01:  118 of  664 MB written (fifo  99%) [buf 100%]  28.6x.
Track 01:  119 of  664 MB written (fifo 100%) [buf 100%]  27.8x.
Track 01:  120 of  664 MB written (fifo 100%) [buf 100%]  28.7x.
Track 01:  121 of  664 MB written (fifo 100%) [buf 100%]  27.8x.
Track 01:  122 of  664 MB written (fifo 100%) [buf 100%]  28.5x.
Track 01:  123 of  664 MB written (fifo 100%) [buf 100%]  28.0x.
Track 01:  124 of  664 MB written (fifo 100%) [buf 100%]  28.8x.
Track 01:  125 of  664 MB written (fifo  99%) [buf 100%]  27.9x.
Track 01:  126 of  664 MB written (fifo 100%) [buf 100%]  28.8x.
Track 01:  127 of  664 MB written (fifo  99%) [buf 100%]  29.7x.
Track 01:  128 of  664 MB written (fifo  99%) [buf 100%]  28.8x.
Track 01:  129 of  664 MB written (fifo 100%) [buf 100%]  29.7x.
Track 01:  130 of  664 MB written (fifo 100%) [buf 100%]  28.9x.
Track 01:  131 of  664 MB written (fifo 100%) [buf 100%]  29.8x.
Track 01:  132 of  664 MB written (fifo 100%) [buf 100%]  28.9x.
Track 01:  133 of  664 MB written (fifo 100%) [buf 100%]  29.8x.
Track 01:  134 of  664 MB written (fifo 100%) [buf 100%]  28.9x.
Track 01:  135 of  664 MB written (fifo 100%) [buf 100%]  29.9x.
Track 01:  136 of  664 MB written (fifo 100%) [buf 100%]  29.0x.
Track 01:  137 of  664 MB written (fifo 100%) [buf 100%]  30.0x.
Track 01:  138 of  664 MB written (fifo  99%) [buf 100%]  29.0x.
Track 01:  139 of  664 MB written (fifo  99%) [buf 100%]   8.6x.
Track 01:  140 of  664 MB written (fifo 100%) [buf 100%]  29.1x.
Track 01:  141 of  664 MB written (fifo 100%) [buf 100%]  30.0x.
Track 01:  142 of  664 MB written (fifo 100%) [buf 100%]  29.1x.
Track 01:  143 of  664 MB written (fifo 100%) [buf 100%]  30.0x.
Track 01:  144 of  664 MB written (fifo  99%) [buf 100%]  29.2x.
Track 01:  145 of  664 MB written (fifo 100%) [buf 100%]  30.2x.
Track 01:  146 of  664 MB written (fifo 100%) [buf 100%]  29.1x.
Track 01:  147 of  664 MB written (fifo  99%) [buf 100%]  30.2x.
Track 01:  148 of  664 MB written (fifo 100%) [buf 100%]  29.2x.
Track 01:  149 of  664 MB written (fifo 100%) [buf 100%]  30.1x.
Track 01:  150 of  664 MB written (fifo  99%) [buf 100%]  29.3x.
Track 01:  151 of  664 MB written (fifo 100%) [buf 100%]  30.2x.
Track 01:  152 of  664 MB written (fifo 100%) [buf 100%]  29.3x.
Track 01:  153 of  664 MB written (fifo  99%) [buf 100%]  30.3x.
Track 01:  154 of  664 MB written (fifo 100%) [buf 100%]  29.2x.
Track 01:  155 of  664 MB written (fifo  99%) [buf 100%]  30.4x.
Track 01:  156 of  664 MB written (fifo 100%) [buf 100%]  29.4x.
Track 01:  157 of  664 MB written (fifo 100%) [buf 100%]  30.2x.
Track 01:  158 of  664 MB written (fifo  99%) [buf 100%]  31.3x.
Track 01:  159 of  664 MB written (fifo 100%) [buf 100%]  30.3x.
Track 01:  160 of  664 MB written (fifo 100%) [buf 100%]  31.4x.
Track 01:  161 of  664 MB written (fifo 100%) [buf 100%]  30.3x.
Track 01:  162 of  664 MB written (fifo  99%) [buf 100%]  31.3x.
Track 01:  163 of  664 MB written (fifo  99%) [buf 100%]  30.4x.
Track 01:  164 of  664 MB written (fifo 100%) [buf 100%]  31.4x.
Track 01:  165 of  664 MB written (fifo 100%) [buf 100%]  30.4x.
Track 01:  166 of  664 MB written (fifo 100%) [buf 100%]  31.4x.
Track 01:  167 of  664 MB written (fifo 100%) [buf 100%]  30.5x.
Track 01:  168 of  664 MB written (fifo 100%) [buf 100%]  31.5x.
Track 01:  169 of  664 MB written (fifo  99%) [buf 100%]  30.5x.
Track 01:  170 of  664 MB written (fifo 100%) [buf 100%]  31.3x.
Track 01:  171 of  664 MB written (fifo 100%) [buf 100%]  30.6x.
Track 01:  172 of  664 MB written (fifo 100%) [buf 100%]  31.5x.
Track 01:  173 of  664 MB written (fifo 100%) [buf 100%]  30.6x.
Track 01:  174 of  664 MB written (fifo 100%) [buf 100%]  31.5x.
Track 01:  175 of  664 MB written (fifo  99%) [buf 100%]  30.6x.
Track 01:  176 of  664 MB written (fifo 100%) [buf 100%]  31.6x.
Track 01:  177 of  664 MB written (fifo 100%) [buf 100%]  30.7x.
Track 01:  178 of  664 MB written (fifo 100%) [buf 100%]  31.6x.
Track 01:  179 of  664 MB written (fifo 100%) [buf 100%]  30.7x.
Track 01:  180 of  664 MB written (fifo  99%) [buf 100%]  31.4x.
Track 01:  181 of  664 MB written (fifo  99%) [buf 100%]  30.9x.
Track 01:  182 of  664 MB written (fifo  99%) [buf 100%]  31.8x.
Track 01:  183 of  664 MB written (fifo  99%) [buf 100%]  30.8x.
Track 01:  184 of  664 MB written (fifo  99%) [buf 100%]  31.7x.
Track 01:  185 of  664 MB written (fifo 100%) [buf 100%]  30.8x.
Track 01:  186 of  664 MB written (fifo  99%) [buf 100%]  31.2x.
Track 01:  187 of  664 MB written (fifo 100%) [buf 100%]  31.3x.
Track 01:  188 of  664 MB written (fifo 100%) [buf 100%]  31.7x.
Track 01:  189 of  664 MB written (fifo 100%) [buf 100%]  32.7x.
Track 01:  190 of  664 MB written (fifo  99%) [buf 100%]  31.9x.
Track 01:  191 of  664 MB written (fifo  99%) [buf 100%]  32.8x.
Track 01:  192 of  664 MB written (fifo 100%) [buf 100%]  31.8x.
Track 01:  193 of  664 MB written (fifo 100%) [buf 100%]  32.8x.
Track 01:  194 of  664 MB written (fifo 100%) [buf 100%]  31.8x.
Track 01:  195 of  664 MB written (fifo 100%) [buf 100%]  32.8x.
Track 01:  196 of  664 MB written (fifo  99%) [buf 100%]  31.9x.
Track 01:  197 of  664 MB written (fifo  99%) [buf 100%]  32.9x.
Track 01:  198 of  664 MB written (fifo 100%) [buf 100%]  31.9x.
Track 01:  199 of  664 MB written (fifo 100%) [buf 100%]  32.9x.
Track 01:  200 of  664 MB written (fifo  99%) [buf 100%]  31.9x.
Track 01:  201 of  664 MB written (fifo 100%) [buf 100%]  33.0x.
Track 01:  202 of  664 MB written (fifo  99%) [buf 100%]  32.0x.
Track 01:  203 of  664 MB written (fifo 100%) [buf 100%]  32.9x.
Track 01:  204 of  664 MB written (fifo 100%) [buf 100%]  31.9x.
Track 01:  205 of  664 MB written (fifo  99%) [buf 100%]  33.1x.
Track 01:  206 of  664 MB written (fifo 100%) [buf 100%]  32.0x.
Track 01:  207 of  664 MB written (fifo  99%) [buf 100%]  33.1x.
Track 01:  208 of  664 MB written (fifo 100%) [buf 100%]  31.9x.
Track 01:  209 of  664 MB written (fifo  99%) [buf 100%]  33.2x.
Track 01:  210 of  664 MB written (fifo 100%) [buf 100%]  32.0x.
Track 01:  211 of  664 MB written (fifo  99%) [buf 100%]  33.1x.
Track 01:  212 of  664 MB written (fifo 100%) [buf 100%]  32.0x.
Track 01:  213 of  664 MB written (fifo  99%) [buf 100%]  32.5x.
Track 01:  214 of  664 MB written (fifo 100%) [buf 100%]  32.8x.
Track 01:  215 of  664 MB written (fifo  99%) [buf 100%]  33.1x.
Track 01:  216 of  664 MB written (fifo  99%) [buf 100%]  32.2x.
Track 01:  217 of  664 MB written (fifo  99%) [buf 100%]  33.1x.
Track 01:  218 of  664 MB written (fifo  99%) [buf 100%]  32.2x.
Track 01:  219 of  664 MB written (fifo 100%) [buf 100%]  33.1x.
Track 01:  220 of  664 MB written (fifo  99%) [buf 100%]  34.2x.
Track 01:  221 of  664 MB written (fifo  99%) [buf 100%]  33.2x.
Track 01:  222 of  664 MB written (fifo 100%) [buf 100%]  34.2x.
Track 01:  223 of  664 MB written (fifo 100%) [buf 100%]  33.1x.
Track 01:  224 of  664 MB written (fifo 100%) [buf 100%]  34.2x.
Track 01:  225 of  664 MB written (fifo 100%) [buf 100%]  33.3x.
Track 01:  226 of  664 MB written (fifo  99%) [buf 100%]  34.3x.
Track 01:  227 of  664 MB written (fifo 100%) [buf 100%]   9.9x.
Track 01:  228 of  664 MB written (fifo 100%) [buf 100%]  34.2x.
Track 01:  229 of  664 MB written (fifo 100%) [buf 100%]  33.1x.
Track 01:  230 of  664 MB written (fifo 100%) [buf 100%]  34.5x.
Track 01:  231 of  664 MB written (fifo 100%) [buf 100%]  33.3x.
Track 01:  232 of  664 MB written (fifo  99%) [buf 100%]  34.3x.
Track 01:  233 of  664 MB written (fifo  99%) [buf 100%]  33.3x.
Track 01:  234 of  664 MB written (fifo 100%) [buf 100%]  34.3x.
Track 01:  235 of  664 MB written (fifo 100%) [buf 100%]  33.3x.
Track 01:  236 of  664 MB written (fifo  99%) [buf 100%]  34.4x.
Track 01:  237 of  664 MB written (fifo 100%) [buf 100%]  32.0x.
Track 01:  238 of  664 MB written (fifo 100%) [buf 100%]  36.0x.
Track 01:  239 of  664 MB written (fifo 100%) [buf 100%]  33.3x.
Track 01:  240 of  664 MB written (fifo 100%) [buf 100%]  34.5x.
Track 01:  241 of  664 MB written (fifo 100%) [buf 100%]  33.3x.
Track 01:  242 of  664 MB written (fifo 100%) [buf 100%]  34.5x.
Track 01:  243 of  664 MB written (fifo 100%) [buf 100%]  33.3x.
Track 01:  244 of  664 MB written (fifo  99%) [buf 100%]  34.4x.
Track 01:  245 of  664 MB written (fifo 100%) [buf 100%]  33.5x.
Track 01:  246 of  664 MB written (fifo  99%) [buf 100%]  34.5x.
Track 01:  247 of  664 MB written (fifo 100%) [buf 100%]  33.4x.
Track 01:  248 of  664 MB written (fifo 100%) [buf 100%]  34.5x.
Track 01:  249 of  664 MB written (fifo 100%) [buf 100%]  33.5x.
Track 01:  250 of  664 MB written (fifo 100%) [buf 100%]  34.4x.
Track 01:  251 of  664 MB written (fifo  99%) [buf 100%]  35.3x.
Track 01:  252 of  664 MB written (fifo 100%) [buf 100%]  34.7x.
Track 01:  253 of  664 MB written (fifo 100%) [buf 100%]  35.6x.
Track 01:  254 of  664 MB written (fifo 100%) [buf 100%]  34.6x.
Track 01:  255 of  664 MB written (fifo 100%) [buf 100%]  35.6x.
Track 01:  256 of  664 MB written (fifo 100%) [buf 100%]  34.5x.
Track 01:  257 of  664 MB written (fifo 100%) [buf 100%]  35.6x.
Track 01:  258 of  664 MB written (fifo  99%) [buf 100%]  34.6x.
Track 01:  259 of  664 MB written (fifo  99%) [buf 100%]  35.5x.
Track 01:  260 of  664 MB written (fifo  99%) [buf 100%]  34.6x.
Track 01:  261 of  664 MB written (fifo  99%) [buf 100%]  35.6x.
Track 01:  262 of  664 MB written (fifo 100%) [buf 100%]  34.6x.
Track 01:  263 of  664 MB written (fifo 100%) [buf 100%]  35.7x.
Track 01:  264 of  664 MB written (fifo  99%) [buf 100%]  34.5x.
Track 01:  265 of  664 MB written (fifo  99%) [buf 100%]  35.7x.
Track 01:  266 of  664 MB written (fifo 100%) [buf 100%]  34.7x.
Track 01:  267 of  664 MB written (fifo 100%) [buf 100%]  35.7x.
Track 01:  268 of  664 MB written (fifo  99%) [buf 100%]  34.6x.
Track 01:  269 of  664 MB written (fifo 100%) [buf 100%]  35.7x.
Track 01:  270 of  664 MB written (fifo 100%) [buf 100%]  34.6x.
Track 01:  271 of  664 MB written (fifo  99%) [buf 100%]  35.8x.
Track 01:  272 of  664 MB written (fifo 100%) [buf 100%]  34.6x.
Track 01:  273 of  664 MB written (fifo  99%) [buf 100%]  35.7x.
Track 01:  274 of  664 MB written (fifo 100%) [buf 100%]  34.7x.
Track 01:  275 of  664 MB written (fifo 100%) [buf 100%]  35.7x.
Track 01:  276 of  664 MB written (fifo 100%) [buf 100%]  34.7x.
Track 01:  277 of  664 MB written (fifo 100%) [buf 100%]  35.8x.
Track 01:  278 of  664 MB written (fifo  99%) [buf 100%]  34.6x.
Track 01:  279 of  664 MB written (fifo 100%) [buf 100%]  35.8x.
Track 01:  280 of  664 MB written (fifo  99%) [buf 100%]  34.6x.
Track 01:  281 of  664 MB written (fifo  99%) [buf 100%]  35.8x.
Track 01:  282 of  664 MB written (fifo  99%) [buf 100%]  36.8x.
Track 01:  283 of  664 MB written (fifo 100%) [buf 100%]  35.8x.
Track 01:  284 of  664 MB written (fifo  99%) [buf 100%]  37.0x.
Track 01:  285 of  664 MB written (fifo 100%) [buf 100%]  35.7x.
Track 01:  286 of  664 MB written (fifo  99%) [buf 100%]  37.1x.
Track 01:  287 of  664 MB written (fifo 100%) [buf 100%]  35.6x.
Track 01:  288 of  664 MB written (fifo  99%) [buf 100%]  37.0x.
Track 01:  289 of  664 MB written (fifo  99%) [buf 100%]  35.8x.
Track 01:  290 of  664 MB written (fifo  99%) [buf 100%]  36.8x.
Track 01:  291 of  664 MB written (fifo  99%) [buf 100%]  35.9x.
Track 01:  292 of  664 MB written (fifo  99%) [buf 100%]  36.0x.
Track 01:  293 of  664 MB written (fifo  99%) [buf 100%]  36.7x.
Track 01:  294 of  664 MB written (fifo  99%) [buf 100%]  36.9x.
Track 01:  295 of  664 MB written (fifo 100%) [buf 100%]  35.9x.
Track 01:  296 of  664 MB written (fifo  99%) [buf 100%]  36.9x.
Track 01:  297 of  664 MB written (fifo 100%) [buf 100%]  35.8x.
Track 01:  298 of  664 MB written (fifo  99%) [buf 100%]  36.9x.
Track 01:  299 of  664 MB written (fifo  99%) [buf 100%]  36.0x.
Track 01:  300 of  664 MB written (fifo  99%) [buf 100%]  36.9x.
Track 01:  301 of  664 MB written (fifo  99%) [buf 100%]  35.9x.
Track 01:  302 of  664 MB written (fifo 100%) [buf 100%]  37.1x.
Track 01:  303 of  664 MB written (fifo 100%) [buf 100%]  35.8x.
Track 01:  304 of  664 MB written (fifo  99%) [buf 100%]  37.0x.
Track 01:  305 of  664 MB written (fifo  99%) [buf 100%]  35.9x.
Track 01:  306 of  664 MB written (fifo 100%) [buf 100%]  37.1x.
Track 01:  307 of  664 MB written (fifo 100%) [buf 100%]  35.8x.
Track 01:  308 of  664 MB written (fifo  99%) [buf 100%]  37.0x.
Track 01:  309 of  664 MB written (fifo 100%) [buf 100%]  36.0x.
Track 01:  310 of  664 MB written (fifo 100%) [buf 100%]  37.0x.
Track 01:  311 of  664 MB written (fifo 100%) [buf 100%]  35.9x.
Track 01:  312 of  664 MB written (fifo 100%) [buf 100%]  37.0x.
Track 01:  313 of  664 MB written (fifo  99%) [buf 100%]  38.0x.
Track 01:  314 of  664 MB written (fifo  99%) [buf 100%]  37.1x.
Track 01:  315 of  664 MB written (fifo 100%) [buf 100%]  38.2x.
Track 01:  316 of  664 MB written (fifo 100%) [buf 100%]  10.9x.
Track 01:  317 of  664 MB written (fifo  99%) [buf 100%]  38.3x.
Track 01:  318 of  664 MB written (fifo 100%) [buf 100%]  37.0x.
Track 01:  319 of  664 MB written (fifo  99%) [buf 100%]  38.1x.
Track 01:  320 of  664 MB written (fifo  99%) [buf 100%]  37.0x.
Track 01:  321 of  664 MB written (fifo 100%) [buf 100%]  38.3x.
Track 01:  322 of  664 MB written (fifo 100%) [buf 100%]  36.9x.
Track 01:  323 of  664 MB written (fifo  99%) [buf 100%]  38.2x.
Track 01:  324 of  664 MB written (fifo 100%) [buf 100%]  37.0x.
Track 01:  325 of  664 MB written (fifo  99%) [buf 100%]  38.2x.
Track 01:  326 of  664 MB written (fifo 100%) [buf 100%]  37.1x.
Track 01:  327 of  664 MB written (fifo  99%) [buf 100%]  38.2x.
Track 01:  328 of  664 MB written (fifo 100%) [buf 100%]  37.0x.
Track 01:  329 of  664 MB written (fifo  99%) [buf 100%]  38.2x.
Track 01:  330 of  664 MB written (fifo 100%) [buf 100%]  37.0x.
Track 01:  331 of  664 MB written (fifo  99%) [buf 100%]  38.2x.
Track 01:  332 of  664 MB written (fifo 100%) [buf 100%]  37.1x.
Track 01:  333 of  664 MB written (fifo 100%) [buf 100%]  38.2x.
Track 01:  334 of  664 MB written (fifo 100%) [buf 100%]  37.0x.
Track 01:  335 of  664 MB written (fifo 100%) [buf 100%]  38.2x.
Track 01:  336 of  664 MB written (fifo 100%) [buf 100%]  37.1x.
Track 01:  337 of  664 MB written (fifo 100%) [buf 100%]  38.3x.
Track 01:  338 of  664 MB written (fifo 100%) [buf 100%]  37.1x.
Track 01:  339 of  664 MB written (fifo 100%) [buf 100%]  38.2x.
Track 01:  340 of  664 MB written (fifo 100%) [buf 100%]  37.0x.
Track 01:  341 of  664 MB written (fifo 100%) [buf 100%]  38.2x.
Track 01:  342 of  664 MB written (fifo  99%) [buf 100%]  37.1x.
Track 01:  343 of  664 MB written (fifo 100%) [buf 100%]  38.2x.
Track 01:  344 of  664 MB written (fifo  99%) [buf 100%]  39.4x.
Track 01:  345 of  664 MB written (fifo 100%) [buf 100%]  38.1x.
Track 01:  346 of  664 MB written (fifo  99%) [buf 100%]  39.5x.
Track 01:  347 of  664 MB written (fifo 100%) [buf 100%]  38.1x.
Track 01:  348 of  664 MB written (fifo 100%) [buf 100%]  39.5x.
Track 01:  349 of  664 MB written (fifo 100%) [buf 100%]  38.2x.
Track 01:  350 of  664 MB written (fifo 100%) [buf 100%]  39.3x.
Track 01:  351 of  664 MB written (fifo  99%) [buf 100%]  38.3x.
Track 01:  352 of  664 MB written (fifo  99%) [buf 100%]  39.4x.
Track 01:  353 of  664 MB written (fifo 100%) [buf 100%]  38.1x.
Track 01:  354 of  664 MB written (fifo 100%) [buf 100%]  39.5x.
Track 01:  355 of  664 MB written (fifo  99%) [buf 100%]  38.1x.
Track 01:  356 of  664 MB written (fifo 100%) [buf 100%]  39.3x.
Track 01:  357 of  664 MB written (fifo 100%) [buf 100%]  38.4x.
Track 01:  358 of  664 MB written (fifo  99%) [buf 100%]  39.4x.
Track 01:  359 of  664 MB written (fifo 100%) [buf 100%]  38.1x.
Track 01:  360 of  664 MB written (fifo  99%) [buf 100%]  39.4x.
Track 01:  361 of  664 MB written (fifo 100%) [buf 100%]  38.3x.
Track 01:  362 of  664 MB written (fifo 100%) [buf 100%]  39.4x.
Track 01:  363 of  664 MB written (fifo 100%) [buf 100%]  38.1x.
Track 01:  364 of  664 MB written (fifo 100%) [buf 100%]  39.4x.
Track 01:  365 of  664 MB written (fifo 100%) [buf 100%]  38.3x.
Track 01:  366 of  664 MB written (fifo  99%) [buf 100%]  39.4x.
Track 01:  367 of  664 MB written (fifo 100%) [buf 100%]  38.1x.
Track 01:  368 of  664 MB written (fifo 100%) [buf 100%]  39.4x.
Track 01:  369 of  664 MB written (fifo  99%) [buf 100%]  38.3x.
Track 01:  370 of  664 MB written (fifo 100%) [buf 100%]  39.3x.
Track 01:  371 of  664 MB written (fifo 100%) [buf 100%]  38.1x.
Track 01:  372 of  664 MB written (fifo 100%) [buf 100%]  38.7x.
Track 01:  373 of  664 MB written (fifo  99%) [buf 100%]  39.1x.
Track 01:  374 of  664 MB written (fifo 100%) [buf 100%]  39.3x.
Track 01:  375 of  664 MB written (fifo 100%) [buf 100%]  40.4x.
Track 01:  376 of  664 MB written (fifo  99%) [buf 100%]  39.4x.
Track 01:  377 of  664 MB written (fifo 100%) [buf 100%]  38.5x.
Track 01:  378 of  664 MB written (fifo 100%) [buf 100%]  41.5x.
Track 01:  379 of  664 MB written (fifo 100%) [buf 100%]  40.6x.
Track 01:  380 of  664 MB written (fifo  99%) [buf 100%]  39.4x.
Track 01:  381 of  664 MB written (fifo  99%) [buf 100%]  40.5x.
Track 01:  382 of  664 MB written (fifo  99%) [buf 100%]  39.3x.
Track 01:  383 of  664 MB written (fifo  99%) [buf 100%]  39.5x.
Track 01:  384 of  664 MB written (fifo  99%) [buf 100%]  40.4x.
Track 01:  385 of  664 MB written (fifo  99%) [buf 100%]  40.7x.
Track 01:  386 of  664 MB written (fifo  99%) [buf 100%]  39.3x.
Track 01:  387 of  664 MB written (fifo  99%) [buf 100%]  40.5x.
Track 01:  388 of  664 MB written (fifo 100%) [buf 100%]  39.3x.
Track 01:  389 of  664 MB written (fifo  99%) [buf 100%]  40.6x.
Track 01:  390 of  664 MB written (fifo 100%) [buf 100%]  39.3x.
Track 01:  391 of  664 MB written (fifo  99%) [buf 100%]  40.6x.
Track 01:  392 of  664 MB written (fifo  99%) [buf 100%]  39.2x.
Track 01:  393 of  664 MB written (fifo  99%) [buf 100%]  40.7x.
Track 01:  394 of  664 MB written (fifo  99%) [buf 100%]  39.2x.
Track 01:  395 of  664 MB written (fifo  99%) [buf 100%]  40.6x.
Track 01:  396 of  664 MB written (fifo  99%) [buf 100%]  39.3x.
Track 01:  397 of  664 MB written (fifo 100%) [buf 100%]  40.5x.
Track 01:  398 of  664 MB written (fifo 100%) [buf 100%]  39.4x.
Track 01:  399 of  664 MB written (fifo 100%) [buf 100%]  40.5x.
Track 01:  400 of  664 MB written (fifo 100%) [buf 100%]  39.3x.
Track 01:  401 of  664 MB written (fifo  99%) [buf 100%]  40.3x.
Track 01:  402 of  664 MB written (fifo 100%) [buf 100%]  11.0x.
Track 01:  403 of  664 MB written (fifo  99%) [buf 100%]  40.8x.
Track 01:  404 of  664 MB written (fifo  99%) [buf 100%]  39.3x.
Track 01:  405 of  664 MB written (fifo  99%) [buf 100%]  40.5x.
Track 01:  406 of  664 MB written (fifo  99%) [buf 100%]  41.7x.
Track 01:  407 of  664 MB written (fifo 100%) [buf 100%]  40.4x.
Track 01:  408 of  664 MB written (fifo 100%) [buf 100%]  41.9x.
Track 01:  409 of  664 MB written (fifo 100%) [buf 100%]  40.4x.
Track 01:  410 of  664 MB written (fifo 100%) [buf 100%]  41.7x.
Track 01:  411 of  664 MB written (fifo  99%) [buf 100%]  40.4x.
Track 01:  412 of  664 MB written (fifo  99%) [buf 100%]  41.8x.
Track 01:  413 of  664 MB written (fifo  99%) [buf 100%]  40.4x.
Track 01:  414 of  664 MB written (fifo 100%) [buf 100%]  41.7x.
Track 01:  415 of  664 MB written (fifo  99%) [buf 100%]  40.4x.
Track 01:  416 of  664 MB written (fifo 100%) [buf 100%]  41.8x.
Track 01:  417 of  664 MB written (fifo 100%) [buf 100%]  40.4x.
Track 01:  418 of  664 MB written (fifo  98%) [buf 100%]  41.7x.
Track 01:  419 of  664 MB written (fifo  99%) [buf 100%]  40.4x.
Track 01:  420 of  664 MB written (fifo  99%) [buf 100%]  41.7x.
Track 01:  421 of  664 MB written (fifo 100%) [buf 100%]  40.3x.
Track 01:  422 of  664 MB written (fifo  99%) [buf 100%]  41.7x.
Track 01:  423 of  664 MB written (fifo  99%) [buf 100%]  40.4x.
Track 01:  424 of  664 MB written (fifo 100%) [buf 100%]  41.7x.
Track 01:  425 of  664 MB written (fifo 100%) [buf 100%]  40.5x.
Track 01:  426 of  664 MB written (fifo  99%) [buf 100%]  41.6x.
Track 01:  427 of  664 MB written (fifo  99%) [buf 100%]  40.4x.
Track 01:  428 of  664 MB written (fifo 100%) [buf 100%]  41.6x.
Track 01:  429 of  664 MB written (fifo 100%) [buf 100%]  40.0x.
Track 01:  430 of  664 MB written (fifo  99%) [buf 100%]  42.2x.
Track 01:  431 of  664 MB written (fifo  99%) [buf 100%]  40.4x.
Track 01:  432 of  664 MB written (fifo 100%) [buf 100%]  41.6x.
Track 01:  433 of  664 MB written (fifo  99%) [buf 100%]  40.2x.
Track 01:  434 of  664 MB written (fifo 100%) [buf 100%]  41.6x.
Track 01:  435 of  664 MB written (fifo 100%) [buf 100%]  40.5x.
Track 01:  436 of  664 MB written (fifo 100%) [buf 100%]  41.5x.
Track 01:  437 of  664 MB written (fifo  99%) [buf 100%]  42.9x.
Track 01:  438 of  664 MB written (fifo 100%) [buf 100%]  41.4x.
Track 01:  439 of  664 MB written (fifo  99%) [buf 100%]  43.0x.
Track 01:  440 of  664 MB written (fifo  99%) [buf 100%]  41.3x.
Track 01:  441 of  664 MB written (fifo 100%) [buf 100%]  43.1x.
Track 01:  442 of  664 MB written (fifo  99%) [buf 100%]  41.5x.
Track 01:  443 of  664 MB written (fifo 100%) [buf 100%]  42.8x.
Track 01:  444 of  664 MB written (fifo 100%) [buf 100%]  41.6x.
Track 01:  445 of  664 MB written (fifo  99%) [buf 100%]  42.8x.
Track 01:  446 of  664 MB written (fifo 100%) [buf 100%]  41.4x.
Track 01:  447 of  664 MB written (fifo  99%) [buf 100%]  42.9x.
Track 01:  448 of  664 MB written (fifo 100%) [buf 100%]  41.4x.
Track 01:  449 of  664 MB written (fifo  99%) [buf 100%]  42.8x.
Track 01:  450 of  664 MB written (fifo 100%) [buf 100%]  41.6x.
Track 01:  451 of  664 MB written (fifo  99%) [buf 100%]  42.8x.
Track 01:  452 of  664 MB written (fifo 100%) [buf 100%]  41.5x.
Track 01:  453 of  664 MB written (fifo  99%) [buf 100%]  42.7x.
Track 01:  454 of  664 MB written (fifo  99%) [buf 100%]  41.5x.
Track 01:  455 of  664 MB written (fifo  99%) [buf 100%]  42.7x.
Track 01:  456 of  664 MB written (fifo  99%) [buf 100%]  41.5x.
Track 01:  457 of  664 MB written (fifo  99%) [buf 100%]  42.8x.
Track 01:  458 of  664 MB written (fifo 100%) [buf 100%]  41.3x.
Track 01:  459 of  664 MB written (fifo  99%) [buf 100%]  42.7x.
Track 01:  460 of  664 MB written (fifo 100%) [buf 100%]  41.4x.
Track 01:  461 of  664 MB written (fifo  99%) [buf 100%]  42.8x.
Track 01:  462 of  664 MB written (fifo 100%) [buf 100%]  41.6x.
Track 01:  463 of  664 MB written (fifo 100%) [buf 100%]  42.8x.
Track 01:  464 of  664 MB written (fifo  99%) [buf 100%]  41.3x.
Track 01:  465 of  664 MB written (fifo  99%) [buf 100%]  42.8x.
Track 01:  466 of  664 MB written (fifo  99%) [buf 100%]  41.3x.
Track 01:  467 of  664 MB written (fifo  98%) [buf 100%]  42.7x.
Track 01:  468 of  664 MB written (fifo  99%) [buf 100%]  43.9x.
Track 01:  469 of  664 MB written (fifo 100%) [buf 100%]  42.6x.
Track 01:  470 of  664 MB written (fifo 100%) [buf 100%]  44.0x.
Track 01:  471 of  664 MB written (fifo 100%) [buf 100%]  42.7x.
Track 01:  472 of  664 MB written (fifo 100%) [buf 100%]  43.8x.
Track 01:  473 of  664 MB written (fifo  99%) [buf 100%]  42.6x.
Track 01:  474 of  664 MB written (fifo  98%) [buf 100%]  44.0x.
Track 01:  475 of  664 MB written (fifo 100%) [buf 100%]  42.3x.
Track 01:  476 of  664 MB written (fifo 100%) [buf 100%]  44.2x.
Track 01:  477 of  664 MB written (fifo  98%) [buf 100%]  42.6x.
Track 01:  478 of  664 MB written (fifo  99%) [buf 100%]  43.8x.
Track 01:  479 of  664 MB written (fifo 100%) [buf 100%]  42.6x.
Track 01:  480 of  664 MB written (fifo 100%) [buf 100%]  43.9x.
Track 01:  481 of  664 MB written (fifo  99%) [buf 100%]  42.4x.
Track 01:  482 of  664 MB written (fifo  99%) [buf 100%]  44.0x.
Track 01:  483 of  664 MB written (fifo 100%) [buf 100%]  42.6x.
Track 01:  484 of  664 MB written (fifo 100%) [buf 100%]  43.7x.
Track 01:  485 of  664 MB written (fifo  99%) [buf 100%]  42.5x.
Track 01:  486 of  664 MB written (fifo  98%) [buf 100%]  44.0x.
Track 01:  487 of  664 MB written (fifo 100%) [buf 100%]  42.4x.
Track 01:  488 of  664 MB written (fifo 100%) [buf 100%]  43.8x.
Track 01:  489 of  664 MB written (fifo  98%) [buf 100%]  42.5x.
Track 01:  490 of  664 MB written (fifo  99%) [buf 100%]  43.5x.
Track 01:  491 of  664 MB written (fifo  99%) [buf 100%]  12.7x.
Track 01:  492 of  664 MB written (fifo  99%) [buf 100%]  43.4x.
Track 01:  493 of  664 MB written (fifo  99%) [buf 100%]  42.7x.
Track 01:  494 of  664 MB written (fifo  99%) [buf 100%]  43.8x.
Track 01:  495 of  664 MB written (fifo  99%) [buf 100%]  42.3x.
Track 01:  496 of  664 MB written (fifo  99%) [buf 100%]  43.8x.
Track 01:  497 of  664 MB written (fifo 100%) [buf 100%]  42.5x.
Track 01:  498 of  664 MB written (fifo  99%) [buf 100%]  43.6x.
Track 01:  499 of  664 MB written (fifo  99%) [buf 100%]  45.1x.
Track 01:  500 of  664 MB written (fifo 100%) [buf 100%]  43.7x.
Track 01:  501 of  664 MB written (fifo  99%) [buf 100%]  45.1x.
Track 01:  502 of  664 MB written (fifo 100%) [buf 100%]  43.6x.
Track 01:  503 of  664 MB written (fifo  99%) [buf 100%]  45.1x.
Track 01:  504 of  664 MB written (fifo  99%) [buf 100%]  43.6x.
Track 01:  505 of  664 MB written (fifo  99%) [buf 100%]  45.0x.
Track 01:  506 of  664 MB written (fifo  99%) [buf 100%]  43.7x.
Track 01:  507 of  664 MB written (fifo  99%) [buf 100%]  44.8x.
Track 01:  508 of  664 MB written (fifo  99%) [buf 100%]  43.6x.
Track 01:  509 of  664 MB written (fifo  99%) [buf 100%]  45.0x.
Track 01:  510 of  664 MB written (fifo  99%) [buf 100%]  43.5x.
Track 01:  511 of  664 MB written (fifo 100%) [buf 100%]  44.6x.
Track 01:  512 of  664 MB written (fifo 100%) [buf 100%]  43.9x.
Track 01:  513 of  664 MB written (fifo 100%) [buf 100%]  44.9x.
Track 01:  514 of  664 MB written (fifo  99%) [buf 100%]  43.6x.
Track 01:  515 of  664 MB written (fifo  99%) [buf 100%]  45.0x.
Track 01:  516 of  664 MB written (fifo  99%) [buf 100%]  43.4x.
Track 01:  517 of  664 MB written (fifo  99%) [buf 100%]  44.8x.
Track 01:  518 of  664 MB written (fifo  99%) [buf 100%]  43.7x.
Track 01:  519 of  664 MB written (fifo  99%) [buf 100%]  44.9x.
Track 01:  520 of  664 MB written (fifo 100%) [buf 100%]  41.2x.
Track 01:  521 of  664 MB written (fifo  99%) [buf 100%]  47.6x.
Track 01:  522 of  664 MB written (fifo  99%) [buf 100%]  43.3x.
Track 01:  523 of  664 MB written (fifo  99%) [buf 100%]  44.5x.
Track 01:  524 of  664 MB written (fifo  99%) [buf 100%]  43.9x.
Track 01:  525 of  664 MB written (fifo  99%) [buf 100%]  44.6x.
Track 01:  526 of  664 MB written (fifo 100%) [buf 100%]  43.5x.
Track 01:  527 of  664 MB written (fifo  98%) [buf 100%]  45.0x.
Track 01:  528 of  664 MB written (fifo 100%) [buf 100%]  43.3x.
Track 01:  529 of  664 MB written (fifo 100%) [buf 100%]  44.8x.
Track 01:  530 of  664 MB written (fifo 100%) [buf 100%]  46.0x.
Track 01:  531 of  664 MB written (fifo 100%) [buf 100%]  44.7x.
Track 01:  532 of  664 MB written (fifo 100%) [buf 100%]  46.1x.
Track 01:  533 of  664 MB written (fifo 100%) [buf 100%]  44.6x.
Track 01:  534 of  664 MB written (fifo  99%) [buf 100%]  46.1x.
Track 01:  535 of  664 MB written (fifo  99%) [buf 100%]  44.6x.
Track 01:  536 of  664 MB written (fifo  99%) [buf 100%]  45.9x.
Track 01:  537 of  664 MB written (fifo  98%) [buf 100%]  44.5x.
Track 01:  538 of  664 MB written (fifo 100%) [buf 100%]  46.2x.
Track 01:  539 of  664 MB written (fifo  99%) [buf 100%]  44.6x.
Track 01:  540 of  664 MB written (fifo 100%) [buf 100%]  45.9x.
Track 01:  541 of  664 MB written (fifo 100%) [buf 100%]  44.7x.
Track 01:  542 of  664 MB written (fifo  98%) [buf 100%]  46.0x.
Track 01:  543 of  664 MB written (fifo 100%) [buf 100%]  44.4x.
Track 01:  544 of  664 MB written (fifo  98%) [buf 100%]  46.0x.
Track 01:  545 of  664 MB written (fifo  99%) [buf 100%]  43.2x.
Track 01:  546 of  664 MB written (fifo  99%) [buf 100%]  47.5x.
Track 01:  547 of  664 MB written (fifo 100%) [buf 100%]  44.5x.
Track 01:  548 of  664 MB written (fifo  98%) [buf 100%]  45.9x.
Track 01:  549 of  664 MB written (fifo 100%) [buf 100%]  44.3x.
Track 01:  550 of  664 MB written (fifo  99%) [buf 100%]  46.2x.
Track 01:  551 of  664 MB written (fifo  99%) [buf 100%]  44.3x.
Track 01:  552 of  664 MB written (fifo 100%) [buf 100%]  45.6x.
Track 01:  553 of  664 MB written (fifo  99%) [buf 100%]  44.9x.
Track 01:  554 of  664 MB written (fifo 100%) [buf 100%]  45.8x.
Track 01:  555 of  664 MB written (fifo 100%) [buf 100%]  44.3x.
Track 01:  556 of  664 MB written (fifo  98%) [buf 100%]  45.9x.
Track 01:  557 of  664 MB written (fifo  99%) [buf 100%]  44.3x.
Track 01:  558 of  664 MB written (fifo 100%) [buf 100%]  45.8x.
Track 01:  559 of  664 MB written (fifo 100%) [buf 100%]  44.3x.
Track 01:  560 of  664 MB written (fifo 100%) [buf 100%]  45.8x.
Track 01:  561 of  664 MB written (fifo 100%) [buf 100%]  47.0x.
Track 01:  562 of  664 MB written (fifo  99%) [buf 100%]  45.8x.
Track 01:  563 of  664 MB written (fifo 100%) [buf 100%]  47.0x.
Track 01:  564 of  664 MB written (fifo 100%) [buf 100%]  45.7x.
Track 01:  565 of  664 MB written (fifo  99%) [buf 100%]  47.0x.
Track 01:  566 of  664 MB written (fifo 100%) [buf 100%]  45.6x.
Track 01:  567 of  664 MB written (fifo  98%) [buf 100%]  47.0x.
Track 01:  568 of  664 MB written (fifo  98%) [buf 100%]  45.8x.
Track 01:  569 of  664 MB written (fifo 100%) [buf 100%]  47.0x.
Track 01:  570 of  664 MB written (fifo 100%) [buf 100%]  45.4x.
Track 01:  571 of  664 MB written (fifo  98%) [buf 100%]  47.2x.
Track 01:  572 of  664 MB written (fifo  99%) [buf 100%]  45.4x.
Track 01:  573 of  664 MB written (fifo  99%) [buf 100%]  47.0x.
Track 01:  574 of  664 MB written (fifo  99%) [buf 100%]  45.6x.
Track 01:  575 of  664 MB written (fifo 100%) [buf 100%]  46.5x.
Track 01:  576 of  664 MB written (fifo  98%) [buf 100%]  45.8x.
Track 01:  577 of  664 MB written (fifo 100%) [buf 100%]  46.9x.
Track 01:  578 of  664 MB written (fifo 100%) [buf 100%]  45.5x.
Track 01:  579 of  664 MB written (fifo  99%) [buf 100%]  46.9x.
Track 01:  580 of  664 MB written (fifo  99%) [buf 100%]  45.4x.
Track 01:  581 of  664 MB written (fifo  99%) [buf 100%]  13.3x.
Track 01:  582 of  664 MB written (fifo 100%) [buf 100%]  45.4x.
Track 01:  583 of  664 MB written (fifo  99%) [buf 100%]  46.6x.
Track 01:  584 of  664 MB written (fifo  99%) [buf 100%]  45.5x.
Track 01:  585 of  664 MB written (fifo  99%) [buf 100%]  46.7x.
Track 01:  586 of  664 MB written (fifo  99%) [buf 100%]  45.4x.
Track 01:  587 of  664 MB written (fifo 100%) [buf 100%]  47.0x.
Track 01:  588 of  664 MB written (fifo 100%) [buf 100%]  45.4x.
Track 01:  589 of  664 MB written (fifo  99%) [buf 100%]  46.6x.
Track 01:  590 of  664 MB written (fifo  99%) [buf 100%]  45.0x.
Track 01:  591 of  664 MB written (fifo  99%) [buf 100%]  46.8x.
Track 01:  592 of  664 MB written (fifo 100%) [buf 100%]  48.0x.
Track 01:  593 of  664 MB written (fifo  99%) [buf 100%]  46.9x.
Track 01:  594 of  664 MB written (fifo 100%) [buf  99%]  44.5x.
Track 01:  595 of  664 MB written (fifo 100%) [buf 100%]  49.9x.
Track 01:  596 of  664 MB written (fifo 100%) [buf 100%]  48.5x.
Track 01:  597 of  664 MB written (fifo 100%) [buf 100%]  46.5x.
Track 01:  598 of  664 MB written (fifo  98%) [buf 100%]  48.0x.
Track 01:  599 of  664 MB written (fifo 100%) [buf 100%]  46.8x.
Track 01:  600 of  664 MB written (fifo  99%) [buf 100%]  48.0x.
Track 01:  601 of  664 MB written (fifo  99%) [buf 100%]  46.4x.
Track 01:  602 of  664 MB written (fifo  98%) [buf 100%]  48.2x.
Track 01:  603 of  664 MB written (fifo  99%) [buf 100%]  46.3x.
Track 01:  604 of  664 MB written (fifo  99%) [buf 100%]  48.0x.
Track 01:  605 of  664 MB written (fifo  99%) [buf 100%]  46.5x.
Track 01:  606 of  664 MB written (fifo 100%) [buf 100%]  48.0x.
Track 01:  607 of  664 MB written (fifo  98%) [buf 100%]  46.4x.
Track 01:  608 of  664 MB written (fifo  98%) [buf 100%]  47.9x.
Track 01:  609 of  664 MB written (fifo  99%) [buf 100%]  46.5x.
Track 01:  610 of  664 MB written (fifo  98%) [buf 100%]  47.7x.
Track 01:  611 of  664 MB written (fifo  98%) [buf 100%]  46.6x.
Track 01:  612 of  664 MB written (fifo 100%) [buf 100%]  47.7x.
Track 01:  613 of  664 MB written (fifo  99%) [buf 100%]  46.0x.
Track 01:  614 of  664 MB written (fifo 100%) [buf 100%]  47.9x.
Track 01:  615 of  664 MB written (fifo  98%) [buf 100%]  46.4x.
Track 01:  616 of  664 MB written (fifo 100%) [buf 100%]  47.8x.
Track 01:  617 of  664 MB written (fifo  99%) [buf 100%]  44.3x.
Track 01:  618 of  664 MB written (fifo  99%) [buf 100%]  50.4x.
Track 01:  619 of  664 MB written (fifo 100%) [buf 100%]  46.3x.
Track 01:  620 of  664 MB written (fifo  99%) [buf 100%]  47.5x.
Track 01:  621 of  664 MB written (fifo 100%) [buf 100%]  46.2x.
Track 01:  622 of  664 MB written (fifo  98%) [buf 100%]  47.8x.
Track 01:  623 of  664 MB written (fifo 100%) [buf 100%]  49.2x.
Track 01:  624 of  664 MB written (fifo  98%) [buf 100%]  47.5x.
Track 01:  625 of  664 MB written (fifo 100%) [buf 100%]  48.9x.
Track 01:  626 of  664 MB written (fifo  99%) [buf 100%]  47.8x.
Track 01:  627 of  664 MB written (fifo  99%) [buf 100%]  48.8x.
Track 01:  628 of  664 MB written (fifo  99%) [buf 100%]  47.6x.
Track 01:  629 of  664 MB written (fifo  98%) [buf 100%]  49.1x.
Track 01:  630 of  664 MB written (fifo 100%) [buf 100%]  47.5x.
Track 01:  631 of  664 MB written (fifo  99%) [buf 100%]  48.9x.
Track 01:  632 of  664 MB written (fifo 100%) [buf 100%]  47.5x.
Track 01:  633 of  664 MB written (fifo  99%) [buf 100%]  48.9x.
Track 01:  634 of  664 MB written (fifo 100%) [buf 100%]  47.3x.
Track 01:  635 of  664 MB written (fifo 100%) [buf 100%]  49.1x.
Track 01:  636 of  664 MB written (fifo  98%) [buf 100%]  47.4x.
Track 01:  637 of  664 MB written (fifo  98%) [buf 100%]  48.8x.
Track 01:  638 of  664 MB written (fifo 100%) [buf 100%]  47.3x.
Track 01:  639 of  664 MB written (fifo  99%) [buf 100%]  49.0x.
Track 01:  640 of  664 MB written (fifo  99%) [buf 100%]  47.1x.
Track 01:  641 of  664 MB written (fifo  99%) [buf 100%]  48.2x.
Track 01:  642 of  664 MB written (fifo 100%) [buf 100%]  48.1x.
Track 01:  643 of  664 MB written (fifo 100%) [buf 100%]  48.8x.
Track 01:  644 of  664 MB written (fifo  98%) [buf 100%]  47.3x.
Track 01:  645 of  664 MB written (fifo  98%) [buf 100%]  48.8x.
Track 01:  646 of  664 MB written (fifo 100%) [buf 100%]  47.3x.
Track 01:  647 of  664 MB written (fifo 100%) [buf 100%]  48.5x.
Track 01:  648 of  664 MB written (fifo  99%) [buf 100%]  47.2x.
Track 01:  649 of  664 MB written (fifo 100%) [buf 100%]  48.9x.
Track 01:  650 of  664 MB written (fifo  99%) [buf 100%]  47.0x.
Track 01:  651 of  664 MB written (fifo  98%) [buf 100%]  48.8x.
Track 01:  652 of  664 MB written (fifo  99%) [buf 100%]  47.1x.
Track 01:  653 of  664 MB written (fifo 100%) [buf 100%]  48.4x.
Track 01:  654 of  664 MB written (fifo 100%) [buf 100%]  50.1x.
Track 01:  655 of  664 MB written (fifo 100%) [buf 100%]  47.0x.
Track 01:  656 of  664 MB written (fifo 100%) [buf 100%]  51.7x.
Track 01:  657 of  664 MB written (fifo 100%) [buf 100%]  48.6x.
Track 01:  658 of  664 MB written (fifo 100%) [buf 100%]  50.0x.
Track 01:  659 of  664 MB written (fifo 100%) [buf 100%]  48.5x.
Track 01:  660 of  664 MB written (fifo 100%) [buf 100%]  49.9x.
Track 01:  661 of  664 MB written (fifo 100%) [buf 100%]  48.5x.
Track 01:  662 of  664 MB written (fifo 100%) [buf 100%]  50.0x.
Track 01:  663 of  664 MB written (fifo 100%) [buf 100%]  48.2x.
Track 01:  664 of  664 MB written (fifo 100%) [buf 100%]  50.1x.
Track 01: Total bytes read/written: 696424448/696424448 (340051 sectors).
Writing  time:  162.253s
Average write speed  31.0x.
Min drive buffer fill was 99%
Fixating...
Fixating time:   14.164s
/usr/bin/wodim: fifo had 10970 puts and 10970 gets.
/usr/bin/wodim: fifo was 0 times empty and 6045 times full, min fill was 95%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=48 -sao driveropts=burnfree -data -tsize=340051s -
[/INDENT]

At this point it just hangs forever waiting to finish the boot track.  .iso CD's made this way will not boot.

Yes, I have tried writing at slower speeds...same result.

This appears to be new with the recent upgrade to Ubuntu 9.10.

Any ideas, or should I submit this as a Bug Report?

---

### Post by arvevans on 2009-11-11
I installed today's updates, including an upgrade for CDRecord.
Now it doesn't even get as far as it did a few days ago.  Writes the disk, apparently OK, then hangs for a very long time before starting to do the verify.  Verify fails on track-0...always.

I'm fast running out of blank CD's just trying this CD writing process.

---

