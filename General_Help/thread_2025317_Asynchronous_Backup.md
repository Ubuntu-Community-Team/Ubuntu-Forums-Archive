---
title: "Asynchronous Backup"
date: 2012-07-14
forum: General Help
---

### Post by chamira on 2012-07-14
I am looking for a basic backup application that I can use to synchronize my files ONE WAY with my external HDD.

That is, my External HDD contains files that my Desktop HDD does not contain and I DON'T want them to be copied across to the desktop.

I have tried a couple of aplications but they all seem to want to synch both HDDs.

I just want the backp to check if the files on my Desktop already exist on the external HDD and if it new/newer version, copy across/overwrite to the External HDD, otherwise do nothing.

Can anyone please give me some pointers?

---

### Post by sudodus on 2012-07-14
You can run ***rsync***. In the most simple mode it is just a copy command like ***cp***. But you will soon find that it can do a lot more ...

Read ```
man rsync
``` First browse it quickly, then read it a little slower to find what you want. This command from that manual shows a typical asynchronous backup command

```
rsync -av /src/foo/ /dest/foo
```

If you want to know what it 'plans to do' use the option

-n  alias --dry-run

```
rsync -avn /src/foo/ /dest/foo
```

---

### Post by chamira on 2012-07-14
Thanks for such a fast response **sudodus**, I will give this a try and get back to you.

---

### Post by sudodus on 2012-07-14
> **chamira said:**
> Thanks for such a fast response **sudodus**, I will give this a try and get back to you.
Good luck with ***rsync*** :-)

---

