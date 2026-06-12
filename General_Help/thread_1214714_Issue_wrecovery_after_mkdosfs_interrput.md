---
title: "Issue w/recovery after mkdosfs interrput"
date: 2009-07-16
forum: General Help
---

### Post by WoodrowH on 2009-07-16
Thanks for reading, and sorry for troubling folks with my ham-fisted accident. In a stupid attempt late-night to relabel my primary media drive, I used [FONT="Courier New"]sudo mkdosfs -n MEDIA1 /dev/sdb1[/FONT] from my Jaunty install, which of course starts reformatting my drive. I realized my mistake after a minute or so, and hit CONTROL-C to kill the reformat.
Did some research, chose testdisk (6.11.3) to try and recover. Not really working well. It sees the partition fine; indeed, if I try to mount it, I can, and it shows empty. However, when I try RebuildBS, after awhile I get this:

[INDENT][I]TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

 1 P FAT16 >32M               0   1  1 78324 254 63 1258291062 [MEDIA1]
Cluster 7217973, Directory / found ?
Answer Y(es), N(o) or A(bort interactive mode). N or A if not sure.

-rwxr-xr-x     0     0   1279870543  4-Oct-2027 04:10 N_PROFIL.E
-rwxr-xr-x     0     0   1313431378  4-Feb-2021 19:00 ERROR_EX.TEN
-rwxr-xr-x     0     0   1447386948 22-Oct-2012 05:50 MPUTERNA.ME[/I][/INDENT]

Which is pretty clearly NOT my original data. Hitting N or A gets me more "files" like that. Nothing on Google on this, either.

Running "Rebuild FAT" also fails, as it tells me the FAT Table is A-OK(?)

I'm looking to try running photorec, but would vastly prefer to try to restore the original FAT table and files, if at all possible -- it's a lot of data to recover, and I'd have to scrounge up another external drive to store it properly. 

Ideas very welcome, including other sources for help -- I've been to the testrec site, including using [these instructions]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition") for the recovery process above. However, I didn't see a support forum for the app there.

Again, thanks.

---

### Post by az on 2009-07-16
> **WoodrowH said:**
> Thanks for reading, and sorry for troubling folks with my ham-fisted accident. In a stupid attempt late-night to relabel my primary media drive, I used [FONT="Courier New"]sudo mkdosfs -n MEDIA1 /dev/sdb1[/FONT] from my Jaunty install, which of course starts reformatting my drive. I realized my mistake after a minute or so, and hit CONTROL-C to kill the reformat.
Did some research, chose testdisk (6.11.3) to try and recover. Not really working well. It sees the partition fine; indeed, if I try to mount it, I can, and it shows empty. However, when I try RebuildBS, after awhile I get this:

[INDENT][I]TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

 1 P FAT16 >32M               0   1  1 78324 254 63 1258291062 [MEDIA1]
Cluster 7217973, Directory / found ?
Answer Y(es), N(o) or A(bort interactive mode). N or A if not sure.

-rwxr-xr-x     0     0   1279870543  4-Oct-2027 04:10 N_PROFIL.E
-rwxr-xr-x     0     0   1313431378  4-Feb-2021 19:00 ERROR_EX.TEN
-rwxr-xr-x     0     0   1447386948 22-Oct-2012 05:50 MPUTERNA.ME[/I][/INDENT]

Which is pretty clearly NOT my original data. Hitting N or A gets me more "files" like that. Nothing on Google on this, either.

Running "Rebuild FAT" also fails, as it tells me the FAT Table is A-OK(?)

I'm looking to try running photorec, but would vastly prefer to try to restore the original FAT table and files, if at all possible -- it's a lot of data to recover, and I'd have to scrounge up another external drive to store it properly. 

Ideas very welcome, including other sources for help -- I've been to the testrec site, including using [these instructions]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition") for the recovery process above. However, I didn't see a support forum for the app there.

Again, thanks.

If testdisk can't rebuild it, then it's gone.  You will need to use photorec or another file carver.

---

