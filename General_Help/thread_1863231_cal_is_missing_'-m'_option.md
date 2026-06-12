---
title: "cal is missing '-m' option"
date: 2011-10-17
forum: General Help
---

### Post by alexei_ on 2011-10-17
Not sure why, cal from Ubuntu is missing option '-m' -- means display Monday first.
In Ubuntu:
> 
usage: cal [-hjy] [[month] year]
       cal [-hj] [-m month] [year]
       ncal [-hJjpwy] [-s country_code] [[month] year]
       ncal [-hJeo] [year]

In RedHat:

> 
usage: cal [-13smjyV] [[[day] month] year]
How to get cal with '-m' option in Ubuntu?

---

### Post by 11jmb on 2011-10-17
What release are you using? 

according to the Ubuntu man pages for cal, 10.04 is the only release that does not have an option to go Monday first.

for 10.10 and onward you can use -M for ncal

---

### Post by alexei_ on 2011-10-17
I have:


> 
lsb_release -a

Distributor ID: Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:        10.04
Codename:       lucid


Strange, that 10.04 is missing this feature...
Upgrading will take some effort... 
But "10.04.3 LTS" is the latest which is "LTS"

---

