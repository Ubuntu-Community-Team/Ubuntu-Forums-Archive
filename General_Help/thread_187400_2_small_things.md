---
title: "2 small things"
date: 2006-06-02
forum: General Help
---

### Post by Ozitraveller on 2006-06-02
sources.list has duplicate entries for 'dapper-security universe'

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


Places menu has:
   Desktop folder|Desktop

How do I fix this menu?

This is from a fresh install from that Dapper Release 6.06.

---

### Post by blackjack6.21.91 on 2006-06-02
Well the sources.list you could manually edit to eliminate the duplicate sources.  Be sure your root.

         sudo gedit /etc/apt/sources.list

I don't know about the menu though..

---

### Post by meng on 2006-06-02
That is true BUT both are commented out (inactive) due to the leading #.
If you wish to enable, remove the # in front of one pair.

I'm not exactly sure what you're seeing with the second problem, but you could open the file manager and go to Bookmarks > Edit Bookmarks and try to fix it.

---

