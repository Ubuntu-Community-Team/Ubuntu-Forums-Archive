---
title: "How to download html website - troubleshoot"
date: 2012-08-01
forum: General Help
---

### Post by ericjoe on 2012-08-01
Good day. I would like to download 19 consecutive websites using GNU wget in a Windows platform.

The websites are shown below:

[HTML]http://faculty.washington.edu/chudler/stm0.html[/HTML]
[HTML]http://faculty.washington.edu/chudler/stm1.html[/HTML]
....
[HTML]http://faculty.washington.edu/chudler/stm18.html
[/HTML]
In fact, the entire 19 websites are a quiz, in which some of them will automatically loads the subsequent website after **a certain time**. You may check on the website [HTML]http://faculty.washington.edu/chudler/stm1.html[/HTML]

I have tried using this wget code:
```
wget -i abc.txt
```,
in which all 19 website links are stored in "abc.txt"

The downloaded html files work for
[HTML]http://faculty.washington.edu/chudler/stm0.html[/HTML]
[HTML]http://faculty.washington.edu/chudler/stm1.html[/HTML]

After that, [HTML]http://faculty.washington.edu/chudler/stm2.html[/HTML] fails to load offline as the [HTML]http://faculty.washington.edu/chudler/stm1.html[/HTML] reconnects to the next website automatically after a certain time. 

Can anyone provide some guidances? Any advice is appreciated. Thanks.

---

