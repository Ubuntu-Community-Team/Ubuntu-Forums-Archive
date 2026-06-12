---
title: "Ubuntu Software Center Question"
date: 2010-10-13
forum: General Help
---

### Post by Don Ju4n on 2010-10-13
HI Everyone :)

Im a newbie who just switched and I'm trying to download an app called docky from the Ubuntu Software Center. When I click install a pop up comes up saying 

"The action would require the installation of packages from not authenticated sources."

When I click ok to proceed with the download, it won't start downloading. I tried with other applications and none of them would install because the same pop up would come up. So can anyone please tell me what to do about it? 

Thanks :)

---

### Post by sanderd17 on 2010-10-13
Go in the Software-center to edit -> software sources and check all sources.

If that doesn't work, try the command line way:

```

sudo apt-get install docky

```

---

### Post by Don Ju4n on 2010-10-13
> **sanderd17 said:**
> Go in the Software-center to edit -> software sources and check all sources.

If that doesn't work, try the command line way:

```

sudo apt-get install docky

```


Worked great thanks :)

---

