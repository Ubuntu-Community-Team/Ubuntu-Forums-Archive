---
title: "Problem with Synaptic"
date: 2006-06-09
forum: General Help
---

### Post by No Whammies on 2006-06-09
E: Type ‘[http://theli.free.fr/packages/dapper/’](http://theli.free.fr/packages/dapper/’) is not known on line 36 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type ‘[http://theli.free.fr/packages/dapper/’](http://theli.free.fr/packages/dapper/’) is not known on line 36 in source list /etc/apt/sources.list
E: Unable to lock the list directory

That is the error message I got after trying to install the repository to get Listen Music Player.  Now Synaptic doesn't work at all.  That error message appears every time I log on to it.  0 packages listed.

Have I really screwed up here and need to reinstall, or can it be fixed?  ](*,)

---

### Post by aysiu on 2006-06-09
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by woedend on 2006-06-09
of course not reinstall!
Go to applications->accessories->terminal
type: sudo gedit /etc/apt/sources.list
it will ask for your password, type it then press enter.
The file will open...if you notice at the bottom youll see "Ln" then a number, thats the line number.  Find Ln 36...thats the busted one.  Erase that line and replace it with this
deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./

that will work for you :)

---

### Post by No Whammies on 2006-06-09
Thanks!  I appreciate it.  It's working now.  *whew*

---

