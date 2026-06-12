---
title: "Change calculator default size?"
date: 2009-11-17
forum: General Help
---

### Post by timsdeepsky on 2009-11-17
Anybody know how to change calculator default size in Ubuntu 9.10?....Instead of always dragging it bigger all the time??
Thanks a lot for any input....

---

### Post by SteveDee on 2009-11-18
> **timsdeepsky said:**
> Anybody know how to change calculator default size in Ubuntu 9.10?....Instead of always dragging it bigger all the time??
Thanks a lot for any input....

No, but I can tell you that the calculator app is gcalctool.

You can set its initial screen position via gconf-editor but I can't see a size setting.

Suggest you web search on "gcalctool" and also take a look at this: [http://bashcurescancer.com/man/cmd/gcalctool](http://bashcurescancer.com/man/cmd/gcalctool)

---

### Post by sisco311 on 2009-11-18
> **timsdeepsky said:**
> Anybody know how to change calculator default size in Ubuntu 9.10?....Instead of always dragging it bigger all the time??
Thanks a lot for any input....

If you have the desktop effects enabled (compiz-fusion): [http://wiki.compiz-fusion.org/WindowMatching]("http://wiki.compiz-fusion.org/WindowMatching")

If not, you can use devilspie: [uhelp]community/Devilspie[/uhelp]

Install it:
```
sudo apt-get install devilspie
```

create a configuration directory and a config file:
```
mkdir ~/.devilspie
```
```
gedit ~/.devilspie/gcalctool.ds
```

~/.devilspie/gcalctool.ds:
```
(if (is (application_name) "gcalctool")
  (begin
     (geometry "800x600+0+0")
  )
)

```

where 800x600 is the size of the window, +0+0 is the position of the window (top-left) (optional)

Press Alt+F2 and run devilspie.

Add it to the startup applications.

---

### Post by timsdeepsky on 2009-11-18
Thanks sisco311 and SteveDee....
This works perfect....I am using the "devilspie"....

---

### Post by sisco311 on 2009-11-19
> **timsdeepsky said:**
> Thanks sisco311 and SteveDee....
This works perfect....I am using the "devilspie"....

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

