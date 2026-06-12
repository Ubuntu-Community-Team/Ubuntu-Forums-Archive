---
title: "want to use Locate instead of find as it gives some faster results"
date: 2012-03-22
forum: General Help
---

### Post by technocp on 2012-03-22
I used locate command to find files and it was all going well. Then came the need of using some more parameters for finding like finding by size, finding by time & date, etc.

So I used the locate command and its database as follows
sudo find $(locate somefile) -<findoption>
it gave me good results. BUT 

everything was messed up when it was about finding files that have spaces in its name.

if filenames have spaces then find command divides the output provided by locate command

---

