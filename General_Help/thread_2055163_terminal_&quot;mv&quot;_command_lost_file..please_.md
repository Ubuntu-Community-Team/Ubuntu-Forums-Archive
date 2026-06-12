---
title: "terminal &quot;mv&quot; command lost file..please help =|"
date: 2012-09-08
forum: General Help
---

### Post by an0nym1ty on 2012-09-08
i have a directory "programs" which has two child directories "geo_heatfolow_sim" and "twamely_hall_shuffel"

i accidentally put a file in the geo heatflow folder instead of the twamely one, so i typed


```
cd geo_heatfolow_sim/ mv sim.cxx ../twamely_hall_shuffel/sim.cxx

```

to move it to the twamely folder, but it isn't in the twamely folder and "locate sim.cxx" doesnt find anything.. 

where did this go? how do i get it back? this is not good. =|

edit: i actually just found it laying in the geo folder... why did that command not move it? also why did locate sim.cxx not return anything? o.O

---

### Post by drmrgd on 2012-09-08
Did you type the exact command you entered here?  If so, then you needed to put an stop command character (I don't know the exact term for it) in there like this:

```
cd geo_heatfolow_sim/ && mv sim.cxx ../twamely_hall_shuffel/sim.cxx
```

or you could do

```
cd geo_heatfolow_sim/; mv sim.cxx ../twamely_hall_shuffel/sim.cxx
```

I'm not 100% on why you didn't get an error about the move command.  But, bash doesn't know where one command ends and the next begins unless you explicitly tell it so.  So, you can either use ';' as a separator between commands, or the boolean '&&' to say do the first command, and if that's successful, then do the second command.  You could also use a boolean or, '||', if you prefer.

As to the locate command, the file probably had not yet been indexed by the system.  I think that happens every hour or so.  To manually update the index, you would run:

```
sudo updatedb
```

Hope that helps!

---

