---
title: "10th Argument problem - passed to script"
date: 2009-11-11
forum: General Help
---

### Post by alex81 on 2009-11-11
Hello all, 

I am trying to solve a script problem. 

I have a java program, which is packaged in a jar file. I am trying to create a script to call it so instead I don't have to type 

java -jar <jarFileName> [args] 

**BUT instead **

scriptName [args]

The problem is that the java application takes more than 9 arguments. When I have $10 in the script file it always interprets that to be the first agument + "0". When I have $11 in the script file it interprets it to be the first arugument + "1". 

Is there anyway to get around this problem? 

Any help would be appreciated.

---

### Post by lswb on 2009-11-11
Try ${10} instead of $10. For args greater than 9, always use ${nn} instead of $nn.

---

### Post by alex81 on 2009-11-11
Thank you!

---

