---
title: "Difference between multiple dpkg commands"
date: 2012-02-09
forum: General Help
---

### Post by jacob.david on 2012-02-09
What is the difference between dpkg and dpkg-query. Both produces the same output.

dpkg-query -l 'libc6-dev'
dpkg -l 'libc6-dev'

Why there are so many dpkg-* commands when simply dpkg is good enough to get the job done? If someone can point me to a good article that would be great.

---

### Post by uRock on 2012-02-09
From the **man dpkg-query** output```
dpkg-query - a tool to query the dpkg database
```They both have a different purpose.

---

### Post by jacob.david on 2012-02-09
Hi URock, thanks for the response. But whatever dpkg-query can do, can be done with the dpkg itself. So why there is a separate command for it. Is it only for giving say for e.g. someone only query access so you can give a sudo access to dpkg-query while the root can hold back the dpkg?

---

### Post by uRock on 2012-02-09
dpkg does not have a query option.

---

### Post by jacob.david on 2012-02-10
dpkg does have a query option. 
dpkg -l lists all the packages. (same as dpkg-query -l)
dpkg -l <package name> produces same output as dpkg-query -l <pkg name>. 
Similarly  dpkg -s <name> and dpkg-query -s  <name> produces same output.

The only option I see extra with dpkg-query that is not supported by dpkg is -W. Is this all the difference?

---

