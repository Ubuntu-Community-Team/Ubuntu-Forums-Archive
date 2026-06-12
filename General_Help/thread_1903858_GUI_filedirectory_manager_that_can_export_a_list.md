---
title: "GUI file/directory manager that can export a list"
date: 2012-01-03
forum: General Help
---

### Post by 5circles on 2012-01-03
I'm looking for a file manager that can export a list of files to a spreadsheet.  I'm guessing that a tool like this is readily available, but I'm just not searching correctly.

I've tried Krusader and BeeSoft Commander, but I can't see a way to export a list from either of them.

Meanwhile I'm copying the list to the clipboard and pasting into OpenOffice.

TIA
Mike

---

### Post by SteveDee on 2012-01-03
> **5circles said:**
> ...I'm guessing that a tool like this is readily available...

I don't have a direct answer, but remember that you can open a terminal and type:-
```

ls > FileList.csv

```
...and this will create a file containing a list of files.

You can then open this as a spreadsheet using Libre/Open Calc.

---

### Post by 5circles on 2012-01-08
> **SteveDee said:**
> I don't have a direct answer, but remember that you can open a terminal and type:-
```

ls > FileList.csv

```
...and this will create a file containing a list of files.

You can then open this as a spreadsheet using Libre/Open Calc.

Thanks @SteveDee.  I can use the terminal, but I was hoping to use GUI tools because it is easier for me than remembering the options.  But in any case, I was able to do what I needed as there were fewer files that I needed to manage than I expected - most in the top level.

---

### Post by SteveDee on 2012-01-08
> **5circles said:**
> ...I was hoping to use GUI tools because it is easier for me than remembering the options...

If you are using Nautilus in Ubuntu you could make a Nautilus script which will appear in your right-click menu. Then you won't have to remember the command.

Its a long time since I've made a Nautilus script (or even used Nautilus) but I think you would make a script file (called ListFiles2csv.sh) something like this:-
```

#!/bin/sh
#---------------------------------------------------------
#Nautilus script: ListFiles2csv.sh
#Create a csv list file of files in the current directory.
#By: 5circles
#Jan 2012
#---------------------------------------------------------
ls > FileList.csv

```

Save the script file in {Home}/.gnome2/nautilus-scripts
Right-click on the script file and make it executable via the Permissions menu.

Using the script: To use the script you would navigate to a directory in Nautilus, then right click and select "Scripts"

If this is not quite right, I'm sure a Ubuntu/Nautilus user will put me right!

---

