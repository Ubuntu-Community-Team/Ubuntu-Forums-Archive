---
title: "Update-Manager seems to have wrong information - don't know how to fix"
date: 2012-05-18
forum: General Help
---

### Post by Starwolf on 2012-05-18
Update-Maner tells me that I haven't updated my package information for 9 days.

But if I click on "check", it fails and gives out this message:

```
W:Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found [IP: 141.30.13.30 80]
, W:Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages  404  Not Found [IP: 141.30.13.30 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```I can' think of anything instead of running apt-get update, but this doesn't change anything... Help would be greatly appreciated.

---

### Post by Cheesemill on 2012-05-18
Sounds like a problem with the de servers. Try selecting a different mirror instead.

You can do this from the Software Centre by going to Edit > Software Sources.

---

### Post by Starwolf on 2012-05-20
I had this idea myself in the meantime - I ran the update with another server, then switched back to the German servers - now everything seems fine again.


Thank you for the quick reply^^

---

