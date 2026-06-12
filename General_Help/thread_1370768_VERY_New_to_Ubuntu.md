---
title: "VERY New to Ubuntu"
date: 2010-01-02
forum: General Help
---

### Post by Twizzler999 on 2010-01-02
Hello-  I am very new to Ubuntu and brand new to this forum.  I am interested in learning how to connect to a website using the command line rather then Firefox.  I thought it would be easier to find information on how to do this. I have several Ubuntu/Linux books, searched google and various other Ubuntu forums but can't seem to find the answer to what I thought would be a pretty basic question.  Any help you experienced users could provide would be much appreciaited.  Thanks.  :):)

---

### Post by impact on 2010-01-02
Do you want to browse a website in a terminal? Use any of the text-based browsers such as links, elinks or my personal favourite w3m. (first install it by typing "sudo apt-get install w3m" or via the package manager, then start it by "w3m www.google.com" or any other web page).

Or do you want to download a page or a file from the internet? Then use wget instead of w3m.

---

### Post by SuperSonic4 on 2010-01-02
> **impact said:**
> Do you want to browse a website in a terminal? Use any of the text-based browsers such as links, elinks or my personal favourite w3m. (first install it by typing "sudo apt-get install w3m" or via the package manager, then start it by "w3m www.google.com" or any other web page).

Or do you want to download a page or a file from the internet? Then use wget instead of w3m.

Also

If you want to download flash (like youtube) try get_flash_videos.

---

### Post by sisco311 on 2010-01-02
w3m is installed by default. Other CLI web browsers are lynx, links, links2 and elinks.

links2 is a webbrowser which can use framebuffer:
```
links2 -g
```

You can use wget or curl to download files.

---

