---
title: "Geolocation is bad in Firefox"
date: 2011-08-12
forum: General Help
---

### Post by lordadi on 2011-08-12
Firstly, not sure if I should put this in the programming section or not - but decided to put it here due to a larger audience.

Whenever I go to any page requesting my geolocation (on a laptop, with wifi only):

[LIST]
[*]On Firefox 5, my location is reported about 40 km out (at the city centre, where neither I nor my ISP are).
[*]On Chromium, my location is reported correctly, as where I live (with ~30 feet!)
[/LIST]
What gives? Is this a known issue with FF?

The fact that this can be reproduced *every single time* indicates either a software issue with FF5 or that chromium has superpowers. Any ideas anyone?

For testing purposes, I've been using this page: [http://code.google.com/apis/maps/documentation/javascript/examples/map-geolocation.html](http://code.google.com/apis/maps/documentation/javascript/examples/map-geolocation.html)

---

### Post by gordintoronto on 2011-08-12
Wild! I got the same result: Firefox showed City Hall, Chrome showed my house. Perhaps Chrome takes advantage of Google's (streetviews) hotspot sniffing.

---

### Post by flipper T on 2011-08-12
what has this got to do with ubuntu ?

---

### Post by lordadi on 2011-08-13
gordintoronto: yep, you are probably seeing identical results.

What's more interesting is that this behaviour does NOT exist in FF on Windows or Chrome in Windows (I mean that the both detect location correctly).

flipper T: this is here precisely because of the above statement. It may be an ubuntu issue, it may be a firefox one. Just tapping into the collective :)

---

### Post by flipper T on 2011-08-13
now you have clarified, i withdraw my pithy (drunken/bitchy) comment

:)

---

### Post by lordadi on 2011-08-13
No worries, Flipper T. Does it work correctly for you in FF on Ubu?

---

### Post by lisati on 2011-08-13
An interesting article on the accuracy of Geolocation can be found here: [http://whatismyipaddress.com/geolocation-accuracy](http://whatismyipaddress.com/geolocation-accuracy)

---

### Post by flipper T on 2011-08-13
works fine for me in chromium

about 3 miles to the south in ff 5

---

### Post by gordintoronto on 2011-08-13
Running Firefox under Windows 7 gave the exact location. When I tried it in IE, I was told the browser does not support geolocation.

BTW, the programming forum is for asking questions about a program you are writing.

---

