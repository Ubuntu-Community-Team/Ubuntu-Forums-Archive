---
title: "Unable to run script of Devil's Pie"
date: 2011-07-07
forum: General Help
---

### Post by Rushyang on 2011-07-07
Hey guys,

I wanted "rhythmbox" to be on every workspace whenever I open it. I searched how to create certain rules for certain windows. & found the devil's pie as the solution.

Now, I have installed Devil's Pie succesfully. Created ~/.devilspie directory. & A script within it named "rhythmbox.ds".
So script's location is: "~/.devilspie/rhythmbox.ds"

My Problems are:
1) I didn't know the script to set a window "To be visible on every woskspace". So I tried to set it on Workspace 4. 
```
(if 
  (is (application_name) "rhythmbox") 
  (set_workspace 4)
)
```I manually invoked devilspie through terminal. But unable to get rhythmbox on workspace 4 when I start it.

2) If somehow I'm able to get 1st point working. I would like to know the code to set it visible on all workspaces.

---

### Post by Habitual on 2011-07-07
are you invoking devilspie using the -a switch (apply)?

save your ds file and run ```
devilspie -a
``` and see what happens....
or ```
devilspie -ad
``` (debug) from terminal and see what the terminal says.

sometimes (rarely) do I have to issue a ```
killall -9 devilpie && devilspie
``` to apply changes.

---

### Post by Rushyang on 2011-07-08
> **Habitual said:**
> are you invoking devilspie using the -a switch (apply)?

save your ds file and run ```
devilspie -a
``` and see what happens....
or ```
devilspie -ad
``` (debug) from terminal and see what the terminal says.

sometimes (rarely) do I have to issue a ```
killall -9 devilpie && devilspie
``` to apply changes.

Same problem which I applied -a switch. 

When I'm debugging, it displays this information on the terminal..

```
Devil's Pie 0.22 starting...
Loading /etc/devilspie
/etc/devilspie doesn't exist
Loading /home/rushyang/.devilspie
Loading /home/rushyang/.devilspie/rhythmbox.ds
Loading /home/rushyang/.devilspie/firefox-bin.ds
2 s-expressions loaded.

```

Then same problem continues! Nothing is being displayed on the terminal even if when I'm startin rhythmbox or firefox. :(

---

### Post by Habitual on 2011-07-08
please post the contents of /home/rushyang/.devilspie/rhythmbox.ds

---

### Post by Rushyang on 2011-07-11
Contents of /home/rushyang/.devilspie/rhythmbox.ds

```
(if 
  (is (application_name) "rhythmbox") 
  (set_workspace 4)
)
```

---

### Post by Habitual on 2011-07-11
try this:
```
( if
( and
( matches ( window_name ) "rhythmbox" )
)
( begin
( set_workspace 4 )
)
```

---

