---
title: "torrent file on firefox - disabled flash (I believe the two are connected)"
date: 2011-09-02
forum: General Help
---

### Post by cheezwheel on 2011-09-02
Hello, 

I am a fresh ubuntu user on a fresh ubuntu loaded pc. I have done all the updates recommended, updated the flash and fixed the trackpad issues, but otherwise the version of ubuntu is stock. The flash was working fine for a couple of days on the firefox browser (have not tried any other browsers as of  yet).

I ran into a problem the other day while loading a torrent file (directly after beginning download). The websites I frequent that use mainly flash (pandora, youtube) no longer play their media. I also can no longer execute a torrent file download, as the browser doesn't react the same way to the files as it used to (click download>chose torrent client>begin download).

Now, when I click 'download' nothing happens. 

Btw, the one torrent file that did work is fine (no viruses), and somehow it managed to finish downloading fine as well.

Suggestions?

---

### Post by lovinglinux on 2011-09-05
Looks like you have a corrupted FF profile. Try to create a new one. You can do that by using the following command on a terminal:

```
firefox -P
```

It will launch the profile manager, from where you can create and start new profiles.

---

### Post by cheezwheel on 2011-09-07
I got impatient, and just re-installed ubuntu 10.04 netbook remix and fixed the issues one by one. Another important thing that I did was updated the java plugin. Everything is working tip-top now (torrents, flash, etc.) 

I think the problem may have been that I had an altered sources.list, due to some advice I came across online. I used this 'to do list' [ _[http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/](http://theindexer.wordpress.com/2010/03/21/to-do-list-after-installing-ubuntu-10-04-aka-lucid-lynx/)_ ] , among other things, and I am under the assumption that may have been the problem. 


Many thanks for trying, though.

---

