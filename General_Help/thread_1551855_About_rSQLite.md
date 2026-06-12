---
title: "About rSQLite"
date: 2010-08-12
forum: General Help
---

### Post by satimis on 2010-08-12
Hi folks,

Ubuntu 1004 64 bit

On which repo can I downland rSQLite for R

RSQLite: SQLite interface for R
[http://cran.r-project.org/web/packages/RSQLite/](http://cran.r-project.org/web/packages/RSQLite/)

```

$ apt-cache search sqlite | grep r-cran
$ apt-cache search rsqlite
$ apt-cache search sqlite | grep cran

```
All without printout


TIA

B.R.
satimis

---

### Post by gunksta on 2010-08-17
I just happened to stumble upon your question, while looking for some other help with RSQLite. Your observation is 100% correct. The necessary package is not to be found in the Ubuntu repositories. You have to install it manually.

Before installing RSQLite, make sure you have "r-base-dev" installed or the following will not work. Use Synaptic or apt-get to do this.

Open a R session (you do not need to be root) and enter:
```
 install.packages("RSQLite", dependencies=TRUE)
```

You should get a TK pop-up asking you which mirror to use. Select one that looks reasonably close. I live in New York and tend to use the Pennsylvania mirror. I wouldn't use one based in the Netherlands.

R will spend the next few minutes downloading, compiling and installing RSQLite and all dependencies. This may take a few minutes.

If you get stuck trying to figure out how to use it, I found this blog post to be incredibly useful: 

[http://statcompute.blogspot.com/2005/12/interact-r-with-sqlite-using-rsqlite.html](http://statcompute.blogspot.com/2005/12/interact-r-with-sqlite-using-rsqlite.html).

---

### Post by satimis on 2010-08-17
> **gunksta said:**
> I just happened to stumble upon your question, while looking for some other help with RSQLite. Your observation is 100% correct. The necessary package is not to be found in the Ubuntu repositories. You have to install it manually.

Before installing RSQLite, make sure you have "r-base-dev" installed or the following will not work. Use Synaptic or apt-get to do this.

Open a R session (you do not need to be root) and enter:
```
 install.packages("RSQLite", dependencies=TRUE)
```

You should get a TK pop-up asking you which mirror to use. Select one that looks reasonably close. I live in New York and tend to use the Pennsylvania mirror. I wouldn't use one based in the Netherlands.

R will spend the next few minutes downloading, compiling and installing RSQLite and all dependencies. This may take a few minutes.

If you get stuck trying to figure out how to use it, I found this blog post to be incredibly useful: 

[http://statcompute.blogspot.com/2005/12/interact-r-with-sqlite-using-rsqlite.html](http://statcompute.blogspot.com/2005/12/interact-r-with-sqlite-using-rsqlite.html).

Hi gunksta,

Thanks for your advice and URL.

I have RSQLite installed on R.  Is it possible to uninstall it easily?

Thanks

B.R.
satimis

---

### Post by gunksta on 2010-08-18
All you have to do is delete the RSQLite folder in the ~/R folder. Or, you could just delete the entire R folder. No muss, no fuss.

---

### Post by satimis on 2010-08-18
> **gunksta said:**
> All you have to do is delete the RSQLite folder in the ~/R folder. Or, you could just delete the entire R folder. No muss, no fuss.

Hi,

$ sudo find / -name RSQLite -type d```

/home/satimis/R/x86_64-pc-linux-gnu-library/2.10/RSQLite

```

Whether remove /RSQLite?  Thanks

B.R.
satimis

---

### Post by gunksta on 2010-08-18
If you remove the RSQLite folder, it will remove the extension.

---

### Post by satimis on 2010-08-18
> **gunksta said:**
> If you remove the RSQLite folder, it will remove the extension.

Thanks

satimis

---

