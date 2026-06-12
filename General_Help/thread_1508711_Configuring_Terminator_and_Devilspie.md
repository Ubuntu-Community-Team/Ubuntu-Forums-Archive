---
title: "Configuring Terminator and Devilspie"
date: 2010-06-13
forum: General Help
---

### Post by joshmuffin on 2010-06-13
Hello all. 

I'm trying (well aiming) to customize my desktop so that on login Terminator is on workspace 3 (split 3 ways and running lynx, irssi and top.

I'm using gdevilspie to configure it but I understand and can use the normal config files. When I use gdevilspie to make a terminal background it works but when i try to do stuff with terminator it doesn't. Here's my terminator config so far:
```
( if 
( begin 
( is ( window_class ) "terminator" )
) 
( begin 
( undecorate )
( spawn_sync "top" )
( set_workspace 3 )
( maximize_horizontally )
( center )
( below )
( set_viewport 3 )
( println "match" )
)
)

```

Once I do get devilspie sorted I also need help making Terminator automatically split and run the correct commands. 

Any help. advice or links are greatly appreciated thanks in advance, Josh.

---

### Post by joshmuffin on 2010-06-14
I got devilspie working I just need help with the terminator thing... Anyone?

---

### Post by joshmuffin on 2010-06-16
I guess ill just changed to solved and figure out the teminator thing somewhere else. PM or reply to thread if you need any help with devilspie

---

