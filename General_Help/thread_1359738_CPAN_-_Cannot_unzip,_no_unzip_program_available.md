---
title: "CPAN - Cannot unzip, no unzip program available"
date: 2009-12-20
forum: General Help
---

### Post by abasel on 2009-12-20
When I try and install extra perl modules I get "Cannot unzip, no unzip program available". I have installed unzip so am not sure what is wrong.

---

### Post by rushowr on 2010-07-14
Simple fix mate (I fought with it earlier today :P )...

sudo nano /etc/perl/CPAN/Config.pm

Find the line that says:
*&#8216;unzip&#8217; => q[]* and change it to
 *&#8216;unzip&#8217; => q[/usr/bin/unzip]*

---

