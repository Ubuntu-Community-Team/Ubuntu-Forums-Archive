---
title: "matlab 2010a segmentation fault on install"
date: 2011-05-01
forum: General Help
---

### Post by wcasper4 on 2011-05-01
have a copy of MATLAB 2010a and I am running into issues installing it. I have followed the code [here]("https://help.ubuntu.com/community/MATLAB/R2010a"): and when I try and run the installer, it comes back with this:


```
walter@W:~$ sudo /home/walter/Desktop/MATLAB/install
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        Segmentation fault

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .
```

---

### Post by wcasper4 on 2011-05-01
also when modifying the code, this happens


 Sorry! Setup aborted . . .

```
walter@W:~$ sudo sh /home/walter/Desktop/MATLAB/install* -t
awk: cmd. line:2: 	BEGIN { found = 0; extra = 9; min = 24; default = 24 }
awk: cmd. line:2: 	                                        ^ syntax error
awk: cmd. line:6: 		    if (nrows < min) nrows = default
awk: cmd. line:6: 		                             ^ syntax error
awk: cmd. line:12: 	END { if (found == 0) print (default - extra) }
awk: cmd. line:12: 	                             ^ syntax error
awk: cmd. line:12: 	END { if (found == 0) print (default - extra) }
awk: cmd. line:12: 	                                              ^ syntax error
awk: cmd. line:2: (FILENAME=- FNR=1) fatal: division by zero attempted in `%'
[: 582: -le: argument expected
Segmentation fault
```

---

