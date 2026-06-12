---
title: "Problem with the Opera deb"
date: 2009-07-28
forum: General Help
---

### Post by vckeating on 2009-07-28
I've been having problems with the opera deb for some time now.  In my software sources I have [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free, but for the last month (at least) I've been getting a 404 when I do an apt-get update, and more bizarrely, I now get the message W: Conflicting distribution: [http://deb.opera.com](http://deb.opera.com) stable Release (expected stable but got lenny).

Any ideas why this is happening?  

Thanks!

- V

---

### Post by x33a on 2009-07-28
i experienced this problem too.

i think the repo is for debian only.

better way, which works for me is to go here:

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

download the debs from here. 

This way, you can see the detailed changelog too.

---

### Post by vckeating on 2009-07-29
Thanks for the reply.  I've done some further poking around and it seems that the only way to correct this is to change 'stable' to 'lenny' in the software sources.  It's a little bit of a problem overall since I believe that most of the tutorials on Opera for Ubuntu list the 'stable' as the one to get.

---

