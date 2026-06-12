---
title: "Linux power managment in user mode driver"
date: 2012-03-20
forum: General Help
---

### Post by vivsundar on 2012-03-20
I am developing a user mode driver for a smart card reader,  for which i am using pcsc daemon which loads a driver(a linux_driver.so  file) from a predetermined path stored in the file system.  
  
**The problem is that, during system suspend and resume is  there any means to register a handle with the power manager from my user  mode driver and gain control of the power manager ?**
  

I am trying to use acpi daemon... not sure whether it will work.
  



with regards
  Vivek.

---

