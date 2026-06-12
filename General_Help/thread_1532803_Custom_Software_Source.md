---
title: "Custom Software Source"
date: 2010-07-17
forum: General Help
---

### Post by pokepal101 on 2010-07-17
Hi. I'm a bit of a noob at Ubuntu (I can use the terminal and stuff though), and I want to know if I can specify a custom server for downloading updates and packages.

I am running Ubuntu 10.04 and I want to use Adam Internet's FileArena server: [ftp://filearena.net/pub/ubuntu](ftp://filearena.net/pub/ubuntu)
It's not listed in the list of servers and I want to know how I can add it or use it (because downloads from there don't count towards my download allowance).

Is this possible?

---

### Post by neoargon on 2010-07-17
> **pokepal101 said:**
> Hi. I'm a bit of a noob at Ubuntu (I can use the terminal and stuff though), and I want to know if I can specify a custom server for downloading updates and packages.

I am running Ubuntu 10.04 and I want to use Adam Internet's FileArena server: [ftp://filearena.net/pub/ubuntu](ftp://filearena.net/pub/ubuntu)
It's not listed in the list of servers and I want to know how I can add it or use it (because downloads from there don't count towards my download allowance).

Is this possible?
Yes

---

### Post by neoargon on 2010-07-17
In the Software sources application,   add the custom server in "Other software "tab . Uncheck the checks in first tab (*ubuntu software). 
Hope that helped
Any more doubt?

---

### Post by Dayofswords on 2010-07-17
i have no idea what the other people are talking about...
like the poster above me.. i dont how thats even relavent


to do this quickly you can open a terminal(Applications > Accessories > Terminal) and use this command
this will only if you are using the Main Server
(highlight and copy, go to terminal and right click and paste and hit enter)
```
gksudo sed -i 's/http:\/\/archive.ubuntu.com\/ubuntu/ftp:\/\/filearena.net\/pub\/ubuntu\//g' /etc/apt/sources.list
```

and your done...

---

### Post by pokepal101 on 2010-07-17
> **Dayofswords said:**
> i have no idea what the other people are talking about...
like the poster above me.. i dont how thats even relavent


to do this quickly you can open a terminal(Applications > Accessories > Terminal) and use this command
this will only if you are using the Main Server
(highlight and copy, go to terminal and right click and paste and hit enter)
```
gksudo sed -i 's/http:\/\/archive.ubuntu.com\/ubuntu/ftp:\/\/filearena.net\/pub\/ubuntu\//g' /etc/apt/sources.list
```

and your done...
Thanks Dayofswords, that worked (semi) perfectly.I had to modify the file myself, but other than that, it worked great!
Thanks! (again)

---

### Post by Dayofswords on 2010-07-17
yeah, there doesn't seem to be a custom "update server" option, all i could find was manual editing

---

