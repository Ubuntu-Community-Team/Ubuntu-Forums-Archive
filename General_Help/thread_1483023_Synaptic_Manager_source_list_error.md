---
title: "Synaptic Manager source list error"
date: 2010-05-14
forum: General Help
---

### Post by geraldinu on 2010-05-14
Dear all,
         I might be repeating this topic but I haven't found a workaround. I installed 'Playonlinux' and needed an update so I followed the instructions on their website. Unfortunately I may have typed in a mistake. And now apt-get or synaptic manager isnt working. Could you please help?

This is the error:
E: Type '--2010-05-14' is not known on line 1 in source list /etc/apt/sources.list.d/playinlinux.list

Many thanks, Aeden.

---

### Post by mhgsys on 2010-05-14
If you really want to keep that; 

open up a terminal and typ;
```
gksudo gedit /etc/apt/sources.list.d/playinlinux.list
```

post output here; 
There must be some char wrong somewhere; 

If you're done with the playinlinux and don't want it anymore, you can remove the file
```
sudo rm /etc/apt/sources.list.d/playinlinux.list
```

Also check the /etc/apt/sources.list for the playinlinux sources, and remove them or put a # in front of them.

---

