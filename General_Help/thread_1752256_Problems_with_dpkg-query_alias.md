---
title: "Problems with dpkg-query alias"
date: 2011-05-07
forum: General Help
---

### Post by ianc1 on 2011-05-07
Hi,

I'm trying to set up an alias in my ~/.bash_aliases file for dpkg-query to use to find out if a package is installed and if so what version.

I inserted the line:```
alias installed="dpkg-query -W -f='${Status} ${Version}\n'"
```and restarted the terminal.

If I run```
installed ping2
``` the output is "No packages found matching ping2" which is correct as the package is not installed.

However if I use an installed package such as nautilus-actions I simply get a blank line output.  If I replace installed with the code used ie```
dpkg-query -W -f='${Status} ${Version}\n
``` I am informed that the package is installed and that its version 3.0.5-1.

Any ideas why the alias is not working for installed packages?

Cheers

---

### Post by ianc1 on 2011-05-15
In case anyone else comes across this issue I have found the solution after trawling the web.

The solution is:```
alias installed='dpkg-query -W -f='\''${Status} ${Version}\n'\'''
```with all quotes being single quotes.

At present I am lost as to why this works and am unsure why the first " ' " after "-f=" doesn't end the alias.  If anyone can help with that it would be great.

I found the solution at [http://www.gilesorr.com/code/](http://www.gilesorr.com/code/).

---

