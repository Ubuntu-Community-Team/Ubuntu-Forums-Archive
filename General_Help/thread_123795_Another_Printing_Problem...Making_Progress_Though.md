---
title: "Another Printing Problem...Making Progress Though"
date: 2006-01-31
forum: General Help
---

### Post by makisupa123 on 2006-01-31
I have a canon i960 and am using the Pixus drivers from the Canon japanese site.  I can print, in color, without issue in Abiword, Evolution, etc...lots of programs.  I cannot print in openoffice or firefox.  This seems to be a common problem as several searches brought several posts...but no real consensus as to what is causing it.  My loopback lo is running and my ppd file is not corrupt.  I checked the CUPS site trying to debug some error codes but found nothing.  Here is my cupsd error_log (the relevant portions of a failed job):

[PHP]D [31/Jan/2006:00:18:24 -0500] print_job: auto-typing file...
D [31/Jan/2006:00:18:24 -0500] print_job: request file type is application/postscript.
D [31/Jan/2006:00:18:24 -0500] check_quotas: requesting-user-name = 'makisupa'
D [31/Jan/2006:00:18:24 -0500] print_job: requesting-user-name = 'makisupa'
D [31/Jan/2006:00:18:24 -0500] Adding default job-sheets values "none,none"...
I [31/Jan/2006:00:18:24 -0500] Adding start banner page "none" to job 19.
I [31/Jan/2006:00:18:24 -0500] Adding end banner page "none" to job 19.
I [31/Jan/2006:00:18:24 -0500] Job 19 queued on 'PIXUS-950i-ver.2.2' by 'makisupa'.
D [31/Jan/2006:00:18:24 -0500] Job 19 hold_until = 0
D [31/Jan/2006:00:18:24 -0500] StartJob(19, 0x8096878)
D [31/Jan/2006:00:18:24 -0500] StartJob() id = 19, file = 0/1
D [31/Jan/2006:00:18:24 -0500] job-sheets=none,none
D [31/Jan/2006:00:18:24 -0500] banner_page = 0
D [31/Jan/2006:00:18:24 -0500] StartJob: argv = "PIXUS-950i-ver.2.2","19","makisupa","Untitled1","1","PageRegion=letter","/var/spool/cups/d00019-001"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[2]="USER=root"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[3]="CHARSET=utf-8"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[4]="LANG=en_US"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[5]="TZ=US/East-Indiana"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[6]="PPD=/etc/cups/ppd/PIXUS-950i-ver.2.2.ppd"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[11]="DEVICE_URI=usb://Canon/i960"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[12]="PRINTER=PIXUS-950i-ver.2.2"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[15]="CUPS_SERVER=localhost"
D [31/Jan/2006:00:18:24 -0500] StartJob: envp[16]="IPP_PORT=631"
D [31/Jan/2006:00:18:24 -0500] StartJob: statusfds = [ 8 9 ]
D [31/Jan/2006:00:18:24 -0500] StartJob: filterfds[1] = [ 10 -1 ]
D [31/Jan/2006:00:18:24 -0500] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [31/Jan/2006:00:18:24 -0500] StartJob: filterfds[0] = [ 11 12 ]
D [31/Jan/2006:00:18:24 -0500] start_process("/usr/lib/cups/filter/pstops", 0xbf8d1b40, 0xbf8d10b8, 10, 12, 9)
I [31/Jan/2006:00:18:24 -0500] Started filter /usr/lib/cups/filter/pstops (PID 21992) for job 19.
D [31/Jan/2006:00:18:24 -0500] StartJob: filter = "/usr/lib/cups/filter/pstocanonbj"
D [31/Jan/2006:00:18:24 -0500] StartJob: filterfds[1] = [ 10 13 ]
D [31/Jan/2006:00:18:24 -0500] start_process("/usr/lib/cups/filter/pstocanonbj", 0xbf8d1b40, 0xbf8d10b8, 11, 13, 9)
I [31/Jan/2006:00:18:24 -0500] Started filter /usr/lib/cups/filter/pstocanonbj (PID 21993) for job 19.
D [31/Jan/2006:00:18:24 -0500] StartJob: backend = "/usr/lib/cups/backend/usb"
D [31/Jan/2006:00:18:24 -0500] StartJob: filterfds[0] = [ -1 11 ]
D [31/Jan/2006:00:18:24 -0500] start_process("/usr/lib/cups/backend/usb", 0xbf8d1b40, 0xbf8d10b8, 10, 11, 9)
I [31/Jan/2006:00:18:24 -0500] Started backend /usr/lib/cups/backend/usb (PID 21994) for job 19.
D [31/Jan/2006:00:18:24 -0500] ProcessIPPRequest: 7 status_code=0
D [31/Jan/2006:00:18:24 -0500] [Job 19] Page = 612x792; 18,14 to 594,784
D [31/Jan/2006:00:18:24 -0500] [Job 19] slowcollate=0, slowduplex=0, sloworder=0
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%BoundingBox: (atend)
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%Creator: OpenOffice.org 1.9.129
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%For: makisupa
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%CreationDate: Tue Jan 31 00:18:22 2006
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%Title: Untitled1
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%LanguageLevel: 3
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%DocumentData: Clean7Bit
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%Pages: (atend)
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%PageOrder: Ascend
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%EndComments
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%BeginProlog
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%BeginResource: procset PSPrint-Prolog 1.0 0
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%EndResource
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%EndProlog
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%BeginSetup
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%EndSetup
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%Page: 1 1
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%Page: 1 1
D [31/Jan/2006:00:18:24 -0500] [Job 19] pw = 576.0, pl = 769.3
D [31/Jan/2006:00:18:24 -0500] [Job 19] PageLeft = 18.1, PageRight = 594.1
D [31/Jan/2006:00:18:24 -0500] [Job 19] PageTop = 783.5, PageBottom = 14.2
D [31/Jan/2006:00:18:24 -0500] [Job 19] PageWidth = 612.0, PageLength = 792.0
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%PageBoundingBox: 10 14 410 587
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%BeginPageSetup
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%BeginFeature: *PageRegion letter
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%EndFeature
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%EndPageSetup
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%:6Ldg@sA73J!b,L^=*)G'l.5,40p'Tr=YN'81WkJJ2Hltf'3$HMbK<<.4o+AX9Sn^s:[3trguU[cK!
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%h]')Z/C36&g%BFj8gZ*La`]E#%?L>^cF^s"pP,/8;JGj&HmVn@*fHg*s.H+TlJ`#3'\C<a<NtW#[eP
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%L.O%5gY<t-63d,`T&+dfPE8\Ns/uJ!4YEa)2Y)=iLlD\+:%s7^u,3G+p&\iJV526=G/L=NoB#L5Wj!
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%_j7Q.X#<;pAB.h'R&`6ic!&.kX!dNSU90B]<3bYGW`%5Dc).huC6in^9iP#t(+Me%*N65A1fb?FU7n
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%/@WgYQ!8cG0NFCWD@Km-`%P4"]OJ!f^K+hZ\A`n+@/sZ=Q7sV2q1>]#Wu%i@CAiakJLjl\olMop]jI
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%fkiTNbkDc&bfOu^?1.t:eaE6Z0Ajs_'&F&!Kdu'(G`me4SW+t+aa"kg.k"!4&b?P84:29iJsG9UW(D
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%dYU#*:7@Y-fh&&..5<2DcfJ)K>%W#HA^Mq@<a&XdbXsW.WE)YH.h&I7;Tq2(?&6]rf$\^%M]%hCA@%
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%L,t;@`)EMc$:M3H5`T8%&kljL4cH(*0pCh`,&mt':EimiZnhG6K3b>bl\+7,HW47H%uXu#G.tCX+.!
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%2Q5'Q\h]G-U.Um=L:PF3OD:fFC+9pkWjHM=-&skSI=1%K8fUdo'4mulTh:gA`q9C*j`J&g&iWa8M'd
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%o9k\JE\@f[O94(9b#];p8]"rQ0M54b#DckT\Cb%#(Q$!Q@/r8L)?to55iBFk+;c(,`oFn^oP#iq987
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%,X]itl]1o62CGf/DKsOd\[VN;f(59GYDfAt6Y"a&V<N<TF[F_N=RcaIYC,Hf0L!rbj\7d[aXL:1#TZ
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%WL4#P^S"-B(e-XSQS=F09R59.UC6Zf#;c>5j>%47'A^s^1Al<*E>HLsDXH^%+O(,CLR0e4'VU9-gZ>
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%aYo'WC+r0C-:-f;m<Bq-('j;VcW^A;%-l>W1'X(LZ($`-r\Q!uZ.hCpq8a85TN[khLQ#`DcZ;hssWe
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%ma`48HNTBC;^7($/=06#+"98K'8Yn1m!3B]T=Yc+s`Zcjli(p^"WlF),K("%HT+AE+mJ-F0^7S31Za
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%PageTrailer
D [31/Jan/2006:00:18:24 -0500] [Job 19] 0 %%Trailer
D [31/Jan/2006:00:18:24 -0500] [Job 19] Saw Trailer!
D [31/Jan/2006:00:18:24 -0500] [Job 19] Saw EOF!
D [31/Jan/2006:00:18:24 -0500] [Job 19] Printer using device file "/dev/usb/lp0"...
E [31/Jan/2006:00:18:24 -0500] PID 21993 stopped with status 0!
D [31/Jan/2006:00:18:24 -0500] [Job 19] LPGETSTATUS returned a port status of 18...
D [31/Jan/2006:00:18:24 -0500] UpdateJob: job 19, file 0 is complete.
D [31/Jan/2006:00:18:24 -0500] CancelJob: id = 19
D [31/Jan/2006:00:18:24 -0500] StopJob: id = 19, force = 0
D [31/Jan/2006:00:18:24 -0500] StopJob: printer state is 3
D [31/Jan/2006:00:18:26 -0500] ReadClient: 4 POST / HTTP/1.1[/PHP]

Its the LPGETSTATUS and the line before it that i think are the most telling.  Can anyone tell me what is going on here?  Thanks for the help...this is seriously driving me nuts...


/mak

---

### Post by Ocxic on 2006-01-31
turbo print for linux, works great. try getting that, even supports printing over a network

---

### Post by makisupa123 on 2006-01-31
I don't want to spend $30 on something that ought to be free.  Call me stubborn if you will....I just don't like that "solution."

/mak

---

### Post by OMRebel on 2006-03-15
Were you able to get your printer working right?  I also have a Canon i960, and I'm not gonna spend money on a third party application just to be able to print.

---

### Post by Ocxic on 2006-03-15
then don't download the thing it not hard to find, thats what i did b4 i got the $$ to pay, used it for 2 months like that, workes perfectly. don't forget u need a keyfile to activate the software

---

### Post by OMRebel on 2006-03-15
Are you able to print at photo quality with it?

---

### Post by OMRebel on 2006-03-15
I went ahead and got turboprint.  Works great!

---

### Post by Ocxic on 2006-03-15
yes it prints perfectly, with all crontrols and setting you coud use in windows 
my i560 now works perfect. even over a network to another comps printer.

---

