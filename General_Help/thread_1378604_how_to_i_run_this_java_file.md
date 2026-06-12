---
title: "how to i run this java file"
date: 2010-01-11
forum: General Help
---

### Post by kcirrab on 2010-01-11
ok i have this program. it launches the java program from a .bat file. well as im sure u know ubuntu dont use .bat files....the program im tryin to run can be found here

[http://uppit.com/v/UYBA87BM](http://uppit.com/v/UYBA87BM)

thanks in advanced

---

### Post by luigi_mb on 2010-01-11
> **kcirrab said:**
> ok i have this program. it launches the java program from a .bat file. well as im sure u know ubuntu dont use .bat files....the program im tryin to run can be found here

[http://uppit.com/v/UYBA87BM](http://uppit.com/v/UYBA87BM)

thanks in advanced

The file you have downloaded is a .rar archive, and to unpack it you need **unrar** (use Synaptic to install it). Once unpacked, you will probably see a *.jar* file. Try

```

java -jar [file].jar

```

You can also look at the *.bat* file, and if the line of code above differs , just replace it with the one inside the *.bat* file.

/luigi

---

