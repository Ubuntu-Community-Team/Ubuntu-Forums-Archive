---
title: "Bash, grep from A to B ?"
date: 2010-12-27
forum: General Help
---

### Post by damogran on 2010-12-27
Hi there,

this probably isn't the right category but I'm not sure which anyway where to place my question. 

What I have is a HTML file which has a part starting with 
<!--Evaluation Rating-->

and ends with the same string. I now would like to grep anything between  the two <!--Evaluation Rating--> lines.

Can this be accomplished with the basic bash utils? 

Thanks in advance!

damo

---

### Post by mobilediesel on 2010-12-27
> **damogran said:**
> Hi there,

this probably isn't the right category but I'm not sure which anyway where to place my question. 

What I have is a HTML file which has a part starting with 
<!--Evaluation Rating-->

and ends with the same string. I now would like to grep anything between  the two <!--Evaluation Rating--> lines.

Can this be accomplished with the basic bash utils? 

Thanks in advance!

damo

I don't think grep can do it but sed can:
```
sed -n '/<!--Evaluation Rating-->/,/<!--Evaluation Rating-->/p' filename.html
```

---

### Post by damogran on 2010-12-30
perfect. thanks a million!

---

