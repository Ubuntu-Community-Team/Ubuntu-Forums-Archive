---
title: "How to find out what drivers I have for my Realtek NIC?"
date: 2011-02-02
forum: General Help
---

### Post by zozza on 2011-02-02
Is there a way of finding our what driver version I have for a piece of hardware?

I have a Realtek card but do not want to install from here ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L)) if I already have a more recent version.

How can I find out the version?  Thanks.

---

### Post by plucky on 2011-02-02
> **zozza said:**
> Is there a way of finding our what driver version I have for a piece of hardware?

I have a Realtek card but do not want to install from here ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L)) if I already have a more recent version.

How can I find out the version?  Thanks.

What does ```
sudo lshw -C network
``` show you in a terminal window.

---

### Post by Habitual on 2011-02-03
> **zozza said:**
> Is there a way of finding our what driver version I have for a piece of hardware?

Yep. 
```
sudo jockey-text -l
```

---

