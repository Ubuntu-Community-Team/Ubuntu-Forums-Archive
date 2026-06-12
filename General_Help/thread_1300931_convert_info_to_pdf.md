---
title: "convert info to pdf"
date: 2009-10-25
forum: General Help
---

### Post by 1nooodlse on 2009-10-25
i know you can print a man page using
$man -t [page] | lpr [printer]
and convert to pdf with
$man -t [page] > itsaboy.ps && ps2pdf itsaboy.ps [pagename].pdf && rm itsaboy.ps

is it possible to so the same with an info?

---

### Post by 1nooodlse on 2009-10-27
bump

---

### Post by 1nooodlse on 2009-10-27
bump

---

### Post by Tyke91 on 2009-10-27
man -t takes the output from man and pipes it through groff...  try

 ```
info [whatever page you want] | groff > [name].ps && ps2pdf [name].ps [pagename].pdf && rm [name].ps
```

---

### Post by 1nooodlse on 2009-10-27
I ran it and I got the following error:

```
$ info nmap | groff > nmap.ps && ps2pdf nmap.ps nmap.pdf && rm nmap.ps
info: Writing node (*manpages*)nmap...
<standard input>:1481: warning: can't find font `iR'
info: Done.
<standard input>:2031: cannot use a space as a starting delimiter
<standard input>:2033: cannot use character `0' as a starting delimiter
<standard input>:2033: cannot use character `0' as a starting delimiter
<standard input>:2033: cannot use character `0' as a starting delimiter
<standard input>:2033: cannot use character `0' as a starting delimiter
<standard input>:2033: cannot use character `0' as a starting delimiter
<standard input>:2251: warning: numeric expression expected (got `c')
<standard input>:2251: warning: numeric expression expected (got `o')

```The output was also not spectacular

Out of curiosity I tried the same with man:

```
$  man nmap | groff > nmap.ps && ps2pdf nmap.ps nmap.pdf && rm nmap.ps
<standard input>:12: warning: can't find special character `u201C'
<standard input>:12: warning: can't find special character `u201D'
<standard input>:630: warning: can't find special character `u2013'
<standard input>:941: warning: can't find special character `u2014'
<standard input>:1440: warning: can't find special character `u2018'
<standard input>:1440: warning: can't find special character `u2019'
<standard input>:1470: warning [p 23, 2.8i]: cannot adjust line
<standard input>:1482: a backspace character is not allowed in an escape name
<standard input>:2032: cannot use a space as a starting delimiter
<standard input>:2034: cannot use character `0' as a starting delimiter
<standard input>:2034: cannot use character `0' as a starting delimiter
<standard input>:2034: cannot use character `0' as a starting delimiter
<standard input>:2034: cannot use character `0' as a starting delimiter
<standard input>:2034: cannot use character `0' as a starting delimiter
<standard input>:2252: warning: numeric expression expected (got `c')
<standard input>:2252: warning: numeric expression expected (got `o')

```and compared it to the output using -t:

```
$  man -t nmap > nmap.ps && ps2pdf nmap.ps nmapt.pdf && rm nmap.ps
```There was a pretty significant drop in quality using groff.

---

### Post by Tyke91 on 2009-10-28
hmm... my only suggestion is to look into the options of groff and see if you can change things (default margins, etc)

---

