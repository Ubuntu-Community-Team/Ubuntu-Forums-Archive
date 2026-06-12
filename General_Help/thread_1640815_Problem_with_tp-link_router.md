---
title: "Problem with tp-link router ?"
date: 2010-12-08
forum: General Help
---

### Post by kiriakos321 on 2010-12-08
Hello, here and two months i have a problem with my new router and ubuntu 10.10. The problem is that my internet connection show me that my laptop had connect to internet but my broswer can't open a website ( this problem is the same with my netbook  ) to fix it always must turn it off and after on either it never makes.

Thanks!

---

### Post by Glasgow.Tony on 2010-12-08
try disabling ipv6 (if it is enabled). this was the problem for me.

---

### Post by kiriakos321 on 2010-12-08
Can you give me some more info about how to do that ? I am very new.:P

---

### Post by Glasgow.Tony on 2010-12-08
> for firefox:

Type about:config in url bar and search for:

network.dns.disableIPv6

and set it to TRUE

try that if you are using FF, or google for the method of disabling it from command line in linux. i'm a noob aswell, so not really able to be very specific. i done same as you, posted a thread cos my net was connected but browser wouldn't work and someone told me how to disable ipv6 and that fixed it.

good luck.

---

### Post by kiriakos321 on 2010-12-08
I really thank you ! I hope it work :D

---

