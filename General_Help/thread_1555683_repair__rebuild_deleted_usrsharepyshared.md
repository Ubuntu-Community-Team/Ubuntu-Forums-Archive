---
title: "repair / rebuild deleted /usr/share/pyshared"
date: 2010-08-18
forum: General Help
---

### Post by sdaau on 2010-08-18
I deleted accidentally the /usr/share/pyshared folder (yes, with 'sudo rm -rf' - that's what happens when you press 'enter' instead of 'tab' :) ), and at first I thought: damn, now I have to reinstall the entire bloody OS! 

But, then I thought of this - first issue a command to remove 'python' while capturing its output:
```

sudo apt-get remove python | tee remove_python_out.txt

```

This will, of course, want to remove each and every dependency on Python you may have installed on your system. And, of course, (again), you answer 'no' when asked if you really want to remove the package - all we needed is a list of dependent packages, which we now have.

Then open 'remove_python_out.txt' and remove the linebreaks, so you have all packages listed as one (big) space-delimited string; then select this string and copy it. 

Finally, go back to the terminal and type:
```

sudo apt-get install --reinstall 

``` 

and then paste the entire list of packages you previously copied.. In my case, 166 MB of packages needed to be retrieved in total, which is not bad at all - the process takes a while, but now I have a fresh new /usr/share/pyshared, with at least 205 items in it already :D

Cheers!

---

