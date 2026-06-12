---
title: "clamav update problem"
date: 2010-05-26
forum: General Help
---

### Post by jamesnewcombe on 2010-05-26
I am having a problem getting clamav to update. When I run freshclam I get the result below:
 
[FONT=Courier New][SIZE=3]ClamAV update process started at Wed May 26 12:12:40 2010[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]main.cld is up to date (version: 52, sigs: 704727, f-level: 44, builder: sven)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: getpatch: Can't download daily-11068.cdiff from 81.91.100.173[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: getpatch: Can't download daily-11068.cdiff from 81.91.100.173[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: getpatch: Can't download daily-11068.cdiff from 81.91.100.173[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: getpatch: Can't download daily-11068.cdiff from 81.91.100.173[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]ERROR: getpatch: Can't download daily-11068.cdiff from 81.91.100.173[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: Incremental update failed, trying to download daily.cvd[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]ERROR: Can't download daily.cvd from 81.91.100.173[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]Giving up on 81.91.100.173...[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]ClamAV update process started at Wed May 26 12:12:41 2010[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]main.cld is up to date (version: 52, sigs: 704727, f-level: 44, builder: sven)[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: getpatch: Can't download daily-11068.cdiff from database.clamav.net[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: getpatch: Can't download daily-11068.cdiff from database.clamav.net[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: getpatch: Can't download daily-11068.cdiff from database.clamav.net[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: getpatch: Can't download daily-11068.cdiff from database.clamav.net[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: getpatch: Can't download daily-11068.cdiff from database.clamav.net[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: Incremental update failed, trying to download daily.cvd[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]WARNING: Can't download daily.cvd from database.clamav.net[/FONT][/SIZE]
 
[FONT=Courier New][SIZE=3]However if i try to get the file manually it works! [/SIZE][/FONT]
 
[SIZE=3][FONT=Courier New]root@filter2:/var/lib/clamav# wget 81.91.100.173/daily.cvd[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]--12:29:19-- [http://81.91.100.173/[COLOR=#000000]daily.cvd[/COLOR]]("http://81.91.100.173/daily-11068.cdiff")[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]=> `daily.cvd'[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]Connecting to 81.91.100.173:80... connected.[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]HTTP request sent, awaiting response... 200 OK[/FONT][/SIZE]
[SIZE=3][FONT=Courier New]Length: 22,906,487 (22M) [text/plain][/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]100%[================================================================>] 22,906,487 146.31K/s ETA 00:00[/FONT][/SIZE]
 
[SIZE=3][FONT=Courier New]12:31:58 (140.78 KB/s) - `daily.cvd' saved [22906487/22906487][/FONT][/SIZE]
 
[FONT=Courier New]Any ideas what this could be?[/FONT]

---

