---
title: "Cannot Burn multissesion dvd's or cd's in K3b"
date: 2011-03-07
forum: General Help
---

### Post by gryphoninc on 2011-03-07
**Cannot Burn multissesion dvd in K3b** 			
 			 			 		   		 		 		[SIZE=3]hi 

Newbie at this.
Installed Ubuntu, had some problems at first but solved them.
Now I tried to burn a multisession dvd and recieved the following message:[/SIZE][I][SIZE=3]
cdrecord has no permission to open the device[/SIZE][/I]

[SIZE=3]also get this debbugging info?[/SIZE]



p, li { white-space: pre-wrap; } [FONT=Monospace]Devices[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]SONY DVD RW DRU-820A 1.0c (/dev/sr1, CD-R,  CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R  DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual  Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential,  DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO,  SAO/R96P, SAO/R96R, Restricted Overwrite, Layer Jump] [%7][/FONT]
 [FONT=Monospace]HL-DT-ST DVD-RAM GH22NP20 1.03 (/dev/sr0, CD-R,  CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R  DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual  Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential,  DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW,  SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite,  Layer Jump] [%7][/FONT]
 
 [FONT=Monospace]K3b::IsoImager[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]mkisofs print size result: 359509 (736274432 bytes)[/FONT]
 
 [FONT=Monospace]System[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]K3b Version: 2.0.1[/FONT]
 [FONT=Monospace]KDE Version: 4.5.1 (KDE 4.5.1)[/FONT]
 [FONT=Monospace]QT Version:  4.7.0[/FONT]
 [FONT=Monospace]Kernel:      2.6.35-27-generic[/FONT]
 
 [FONT=Monospace]Used versions[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]mkisofs: 1.1.10[/FONT]
 [FONT=Monospace]cdrecord: 1.1.10[/FONT]
 
 [FONT=Monospace]cdrecord[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]scsidev: '/dev/sr0'[/FONT]
 [FONT=Monospace]devname: '/dev/sr0'[/FONT]
 [FONT=Monospace]scsibus: -2 target: -2 lun: -2[/FONT]
 [FONT=Monospace]Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.[/FONT]
 [FONT=Monospace]=== last message repeated 4 times. ===[/FONT]
 [FONT=Monospace]Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.[/FONT]
 [FONT=Monospace]WARNING: /dev/sr0 seems to be mounted![/FONT]
 [FONT=Monospace]/usr/bin/wodim: Device or resource busy. [/FONT]
 [FONT=Monospace]Cannot open SCSI driver![/FONT]
 [FONT=Monospace]For possible targets try 'wodim --devices' or 'wodim -scanbus'.[/FONT]
 [FONT=Monospace]For possible transport specifiers try 'wodim dev=help'.[/FONT]
 [FONT=Monospace]For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from[/FONT]
 [FONT=Monospace]the wodim documentation.[/FONT]
 [FONT=Monospace]TOC Type: 1 = CD-ROM[/FONT]
 [FONT=Monospace]Waiting for data on stdin...[/FONT]
 
 [FONT=Monospace]cdrecord command:[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=16 -sao driveropts=burnfree -multi -waiti -data -tsize=359509s -[/FONT]
 
 [FONT=Monospace]mkisofs[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]Warning: creating filesystem that does not conform to ISO-9660.[/FONT]
 [FONT=Monospace]NO Rock Ridge present[/FONT]
 [FONT=Monospace]Disabling Rock Ridge / XA / AA[/FONT]
 [FONT=Monospace]Warning: Neither Rock Ridge (-R) nor TRANS.TBL (-T) [/FONT]
 [FONT=Monospace]name translations were found on previous session.[/FONT]
 [FONT=Monospace]ISO-9660 file names have been used instead.[/FONT]
 [FONT=Monospace]359509[/FONT]
 [FONT=Monospace]Warning: creating filesystem that does not conform to ISO-9660.[/FONT]
 [FONT=Monospace]Warning: ISO-9660 filenames longer than 31 may cause buffer overflows in the OS.[/FONT]
 [FONT=Monospace]I: -input-charset not specified, using utf-8 (detected in locale settings)[/FONT]
 [FONT=Monospace]NO Rock Ridge present[/FONT]
 [FONT=Monospace]Disabling Rock Ridge / XA / AA[/FONT]
 [FONT=Monospace]Warning: Neither Rock Ridge (-R) nor TRANS.TBL (-T) [/FONT]
 [FONT=Monospace]name translations were found on previous session.[/FONT]
 [FONT=Monospace]ISO-9660 file names have been used instead.[/FONT]
 [FONT=Monospace]Using aaf-underbelly000.files.the.man.who. for   Underbelly.Files.The.Man.Who.Got.Away/Subs/aaf-underbelly.files.the.man.who.got.away.proper.dvdri   p.xvid-subs.sfv  (aaf-underbelly.files.the.man.who.got.away.proper.dvdri   p.xvid-subs.rar)[/FONT]
 
 [FONT=Monospace]mkisofs calculate size command:[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]/usr/bin/genisoimage -cdrecord-params  1149344,1519456 -prev-session /dev/sr0 -gui -graft-points -print-size  -quiet -volid 2011_02_20_ -volset  -appid K3B  THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK  -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort  /tmp/kde-gryphon/k3bDS5969.tmp -rational-rock -hide-list  /tmp/kde-gryphon/k3bNa5969.tmp -joliet -joliet-long -hide-joliet-list  /tmp/kde-gryphon/k3bnX5969.tmp -no-cache-inodes -udf  -untranslated-filenames -max-iso9660-filenames -translation-table  -hide-joliet-trans-tbl -iso-level 3 -path-list  /tmp/kde-gryphon/k3byx5969.tmp[/FONT]
 
 [FONT=Monospace]mkisofs command:[/FONT]
 [FONT=Monospace]-----------------------[/FONT]
 [FONT=Monospace]/usr/bin/genisoimage -cdrecord-params  1149344,1519456 -prev-session /dev/sr0 -gui -graft-points -volid  2011_02_20_ -volset  -appid K3B THE CD  KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher   -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort  /tmp/kde-gryphon/k3bZm5969.tmp -rational-rock -hide-list  /tmp/kde-gryphon/k3bLe5969.tmp -joliet -joliet-long -hide-joliet-list  /tmp/kde-gryphon/k3bjk5969.tmp -no-cache-inodes -udf  -untranslated-filenames -max-iso9660-filenames -translation-table  -hide-joliet-trans-tbl -iso-level 3 -path-list  /tmp/kde-gryphon/k3boB5969.tmp[/FONT]




[FONT=Monospace]And I took a sceen shot of what I get when I load the DVD and what happens when it doesn't burn.[/FONT]


[FONT=Monospace][IMG]http://i21.photobucket.com/albums/b274/rapiertoledana/p1.png[/IMG]
[/FONT]
 


and this one when it fails to burn.

[IMG]http://i21.photobucket.com/albums/b274/rapiertoledana/Workspace1_002-1.png[/IMG]


[SIZE=3]Could someone give me a solution. I just cannot burn my DVD's or CD's[/SIZE]

Thanks:sad:
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10531292") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10531292")

---

