---
title: "Gwget will not mirror site"
date: 2009-09-25
forum: General Help
---

### Post by Williamrb on 2009-09-25
HI,

I just installed Wget from add/remove programs.  I ran it and chose to download an entire site, entered in the form [http://websitename](http://websitename) and it only downloaded the index.html file from the website.  Can someone help with this?

Thanks,
Randy

---

### Post by blueridgedog on 2009-09-25
What options did you use for your wget command?

---

### Post by t0p on 2009-09-25
You need to use the **-r** or **--recursive** flag.  Eg:

```
wget -r http://example.com
```

---

