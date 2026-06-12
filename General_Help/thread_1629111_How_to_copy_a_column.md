---
title: "How to copy a column"
date: 2010-11-23
forum: General Help
---

### Post by satimis on 2010-11-23
Hi folks,

Ubuntu 10.10
Gnome desktop

On a text file, .txt, it is possible to high-light and copy a row on a table.  But how to high-light and copy a column.  TIA

B.R.
satimis

---

### Post by lykeion on 2010-11-23
I guess it depends on which text editor you use. In Geany (default text editor) it's not possible (maybe some plugin will enable this?). 
In OpenOffice word processor I don't think it's possible either.
However in **Geany** (install it via Ubuntu Software Center) you can do a vertical selection by holding down Ctrl-key.

Another solution is to split into columns with a delimiter (let's say all your columns is seperated with a comma). 
You can import this into OpenOffice Spreadsheet to get a column-separated file.

---

### Post by luigi_mb on 2010-11-23
NEdit can do it. It's in the repositories.

/luigi

---

### Post by satimis on 2010-11-23
> **lykeion said:**
> 
- snip -

However in **Geany** (install it via Ubuntu Software Center) you can do a vertical selection by holding down Ctrl-key.

Hi,

Thanks for your advice.

Whether you meant;

Geany
[http://www.geany.org/](http://www.geany.org/)
?

It is on repo:

$ apt-cache policy geany```

geany:
  Installed: (none)
  Candidate: 0.19.1-1
  Version table:
     0.19.1-1 0
        500 http://hk.archive.ubuntu.com/ubuntu/ maverick/universe amd64 Packages

```


> 
Another solution is to split into columns with a delimiter (let's say all your columns is seperated with a comma). 
You can import this into OpenOffice Spreadsheet to get a column-separated file.

cut command can do it, if columns separated with a comma or space.  But if the file looks as follow;```

  Year Yield Rainfall Temperature
1 1963	  60        8          56
2 1964    50       10          47
3 1965    70       11          53
4 1966    70       10          53
5 1967    80        9          56
6 1968    50        9          47
7 1969    60       12          44
8 1970    40       11          44

```

How can I do it with "cut"?  Thanks


B.R.
satimis

---

### Post by junapp on 2010-11-23
> **satimis said:**
> Hi folks,
On a text file, .txt, it is possible to high-light and copy a row on a table.  But how to high-light and copy a column.  TIA


If you are a vi person, you can use visual selection. Position the cursor at the top left of your selection, ctrl-v, then use arrow keys or hjlk to navigate to the bottom right of your selection. y to copy (yank). p to paste. Note if you need to jump to the other corner of the selection, use o.

I used to use vi all the time for this, but then found Geany could do it as well, and haven't used vi for this in a very long time, but quite useful to know in the case you are stuck in a ssh session sometime.

---

### Post by junapp on 2010-11-23
if you are looking for a script to handle it take a look at:
[http://iheartcomputer.com/bash-scripting/column-manipulation/](http://iheartcomputer.com/bash-scripting/column-manipulation/)

Which column are you trying to extract?

---

### Post by AlphaLexman on 2010-11-23
Sometimes you only need a one-time solution, or maybe you are giving us sample data for a recurring script... 

I can copy and paste your data/code to gnumeric and shift the header row one column right, and get a nice clean spreadsheet, which can be saved as *.csv and manipulated accordingly.

If you are trying to decode a script to extract more info, we need to know!

---

### Post by satimis on 2010-11-23
> **junapp said:**
> If you are a vi person, you can use visual selection. Position the cursor at the top left of your selection, ctrl-v, then use arrow keys or hjlk to navigate to the bottom right of your selection. y to copy (yank). p to paste. Note if you need to jump to the other corner of the selection, use o.

- snip -

Hi,

How to paste the selected content to another file?  Thanks

B.R.
satimis

---

### Post by satimis on 2010-11-23
Hi folks,

I think the most convenient way for me is:

Add a heading to the 1st column of my table.  Run:-

> cat table.txt | awk '{print $3}'```

Yield
60
50
70
70
80
50
60
40

```

$3 = column 3 etc.

Anyway lot of thanks for your advice.

B.R.
satimis

---

### Post by junapp on 2010-12-01
> **satimis said:**
> How to paste the selected content to another file?  Thanks
I know you have a solution, but for the record, while already in vi after 'y'anking the text you want type
:e newfile.txt
which should put you into a new file, then 'p'aste there.

If you have made changes to the original, you may need to do 
:e! newfile.txt

use
:ls
to list the current buffers, and type a number to switch to the one you want.

---

### Post by satimis on 2010-12-01
> **junapp said:**
> while already in vi after 'y'anking the text you want type
:e newfile.txt
which should put you into a new file, then 'p'aste 

Hi,


Thanks for your advice.

Could you please explain in more detail.

1)
If I expect to paste to another existing file which is NOT running?

2)
If I expect to paste to a new file which not created yet?

TIA

B.R.
satimis

---

