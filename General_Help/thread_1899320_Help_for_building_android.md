---
title: "Help for building android?"
date: 2011-12-23
forum: General Help
---

### Post by gannon5197 on 2011-12-23
So, I'm building for android and I've gotten pretty far. I've repo init'd and synced, but when I go to run lunch, it gives me a list of like 20 devices:
```
gannon@ubuntu:~/android/system$ lunch

You're building on Linux

Lunch menu... pick a combo:
     1. full-eng
     2. full_x86-eng
     3. vbox_x86-eng
     4. thunderc-eng
     5. full_thunderc-userdebug
     6. cm_thunderc-userdebug
     7. full_stingray-userdebug
     8. full_wingray-userdebug
     9. full_maguro-userdebug
     10. full_toro-userdebug
     11. full_panda-eng
     12. cm_crespo-userdebug
     13. cm_crespo4g-userdebug
     14. cm_p4tmo-userdebug
     15. cm_p4vzw-userdebug
     16. cm_p4wifi-userdebug
     17. cm_maguro-userdebug
     18. cm_p920-userdebug
     19. cm_p970-userdebug
     20. cm_p990-userdebug
     21. cm_p999-userdebug
     22. cm_pyramid-userdebug
     23. cm_smb_a1011-userdebug
     24. cm_toro-userdebug
```

My device is thunderc, so I selected 4. Now, this is the error I'm getting:
```
Which would you like? [full-eng] 4
build/core/node_fns.mk:187: *** unterminated call to function `call': missing `)'.  Stop.
Traceback (most recent call last):
  File "build/tools/roomservice.py", line 9, in <module>
    device = product[product.index("_") + 1:]
ValueError: substring not found
build/core/node_fns.mk:187: *** unterminated call to function `call': missing `)'.  Stop.

** Don't have a product spec for: 'thunderc'
** Do you have the right repo manifest?

```
I can provide my build/tools/roomservice.py or build/core/node_fns.mk if you need it, which I'm sure you do. I just really could use some help!

---

### Post by gannon5197 on 2011-12-23
[This]("http://pastebin.com/h4fuBpSs") is node_fns.mk, and [this]("http://pastebin.com/eYwiRQx8") is my roomservice.py

---

