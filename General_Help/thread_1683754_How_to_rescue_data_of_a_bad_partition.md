---
title: "How to rescue data of a bad partition"
date: 2011-02-08
forum: General Help
---

### Post by basilwatson on 2011-02-08
Ive had a partition, I was booting from suddenly go bad 

luckily I have dual booted ubuntu 9 on another partition 

how can I rescue files of the partition that has gone bad ???//

Kind regards Stephen

---

### Post by Rhubarb on 2011-02-08
This is quite easy to do:

[LIST=1]
[*]Unmount (if it's not already mounted) the bad partition.
[*]Install the **testdisk** package from the Ubuntu repositories
[*]Run photorec as root - **sudo photorec**
[*]Then follow the prompts
[/LIST]

Photorec works best with 2 partitions, 1 partition being the one you want to recover from, the other partition is where you save the restored files to.

For some more info about photorec, see here:-
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

and a nice step by step guide here:-
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by basilwatson on 2011-02-08
> **Rhubarb said:**
> This is quite easy to do:

[LIST=1]
[*]Unmount (if it's not already mounted) the bad partition.
[*]Install the **testdisk** package from the Ubuntu repositories
[*]Run photorec as root - **sudo photorec**
[*]Then follow the prompts
[/LIST]

Photorec works best with 2 partitions, 1 partition being the one you want to recover from, the other partition is where you save the restored files to.

For some more info about photorec, see here:-
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

and a nice step by step guide here:-
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)


thank You , 

Done and Recovered 

Thank you very much 

Stephen

---

