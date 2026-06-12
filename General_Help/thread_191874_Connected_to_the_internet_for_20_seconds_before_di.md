---
title: "Connected to the internet for 20 seconds before disconnect"
date: 2006-06-08
forum: General Help
---

### Post by SSB on 2006-06-08
I JUST installed Ubuntu and it works great EXCEPT for the fact that the internet just.. dies after about 20 seconds. It tells me there are software updates, I logon to GAIM and open up firefox, but then it all just dies out with no warning. I had no problems at all when running from the live CD. What could be causing this?

---

### Post by Peturrr on 2006-06-08
It looks like ipv6 problems. I don't know for sure, but maybe a search for ipv6 gives you some good results.

---

### Post by scxtt on 2006-06-08
while it's working, type "ifconfig -a" in a terminal and see if you see the device is "UP" - then after it stops working enter "ifconfig -a" again and see if the device is still "UP" ... that won't solve any problem, but it'll help narrow it down some ...

also take a look in your System --> Administration --> Networking and see if anything looks "strange" ...

---

### Post by cyracks on 2006-06-08
Do you have any errors in the logs ?

---

