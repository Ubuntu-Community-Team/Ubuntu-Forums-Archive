---
title: "Failed to fetch http://ppa.launchpad.net..."
date: 2011-11-20
forum: General Help
---

### Post by Advait on 2011-11-20
W:Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Hi All, See above and see attached pic. I searched google and the forums and didn't find any clear solution. I'm using 10.10. Any solution? Plz know that I'm a newbie and can barely use the command line. Thanks! -Tom

---

### Post by Paddy Landau on 2011-11-20
Sometimes the repositories go temporarily off-line.

Try again later (well, it is already later, so try now).

---

### Post by Advait on 2011-11-20
> **Paddy Landau said:**
> Sometimes the repositories go temporarily off-line.

Try again later (well, it is already later, so try now).

Thanks for the reply. I tried again; same problem. Problem has been happening each and every time I try to update for the past 3 months or so. I've seen this problem about 12 times so far. Any ideas? 

I'm using Firefox 8 with No-Script. But I'm assuming the Ubuntu update module doesn't involve the browser.

Thanks for your kind help.

---

### Post by Paddy Landau on 2011-11-21
Ah, I've checked the URI, and it does not exist.

Please would you post back, attaching the file [FONT=Fixedsys]/etc/apt/sources.list[/FONT] to your post.

---

### Post by raja.genupula on 2011-11-21
> **Advait said:**
> W:Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Hi All, See above and see attached pic. I searched google and the forums and didn't find any clear solution. I'm using 10.10. Any solution? Plz know that I'm a newbie and can barely use the command line. Thanks! -Tom

do this
go to update manager -> settings -> 1st tab download from ...there change your server to some other best server to your location . 

and update again

---

### Post by Advait on 2011-11-21
> **Paddy Landau said:**
> Ah, I've checked the URI, and it does not exist.

Please would you post back, attaching the file [FONT=Fixedsys]/etc/apt/sources.list[/FONT] to your post.

When I try to attach the file it says "Invalid File". Please advise. Thanks!

Cheers,

Tom

---

### Post by Advait on 2011-11-21
> **raja.genupula said:**
> do this
go to update manager -> settings -> 1st tab download from ...there change your server to some other best server to your location . 

and update again

OK, I followed your instructions. Located best server -> downloaded and installed updates -> Rebooted pc -> Started another updated -> Same error reappeared. Any way to fix? Thanks!

Cheers,

Tom

---

### Post by Paddy Landau on 2011-11-21
> **Advait said:**
> When I try to attach the file it says "Invalid File".
Ah. Ubuntu forums doesn't like it. Please let me see your sources: You have two options; use whichever is easier for you.

Either:

[LIST]
[*]Compress the file into your own folder (say, Desktop), and attach that.
[/LIST]
Or:

[LIST]
[*]Edit the file.
[*]Copy the contents.
[*]Create a new post.
[*]Paste the contents between [noparse]```
 and 
```[/noparse].
[/LIST]

EDIT: Or just do as oldos2er says in the next post.

---

### Post by oldos2er on 2011-11-21
There is no PPA named "user". I suggest you run **gksu software-properties-gtk** and remove it. It should be under the 'Other Software' tab.

---

