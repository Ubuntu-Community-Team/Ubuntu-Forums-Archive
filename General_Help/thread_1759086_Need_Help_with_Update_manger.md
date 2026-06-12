---
title: "Need Help with Update manger"
date: 2011-05-15
forum: General Help
---

### Post by iohern on 2011-05-15
My update manager will not recive updates because it can not recive from the sugar team and i have removed the sugar packages but it still gives me this message> W:Failed to fetch [http://ppa.launchpad.net/sugarteam/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sugarteam/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sugarteam/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sugarteam/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead. how do i fix this

---

### Post by kostkon on 2011-05-15
You also need to remove its entries from your software sources list.

To do this, open your software centre, select *Edit -> Software Sources*, select the *3rd party software* tab and delete the 2 entries for sugar. Then press close and that'll be it.

---

