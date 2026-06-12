---
title: "What does this error message mean?"
date: 2009-11-08
forum: General Help
---

### Post by rcayea on 2009-11-08
I downloaded two vmware appliances from bagside.com and when I go to extract either one, they both give me the following error message. Any thoughts?

Thanks,
Randy 


```

```7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Error: /home/rcayea/Documents/FROM UBUNTU 9.04 to go to 9.10/rcayea/MyMachines/man10.7z: Can not open file as archive

Errors: 1```

```

---

### Post by zvacet on 2009-11-09
```
sudo apt-get install p7zip p7zip-full p7zip-rar
```

---

### Post by rcayea on 2009-11-09
ok. I will give that a try. thanks. I already have 7zip installed but I guess I don't have a specific component of it. Thanks again, Randy

---

### Post by rcayea on 2009-11-09
I still get the same error message as posted in my first post. It must be a faulty packaging job?

---

### Post by alphaniner on 2009-11-09
I think the error is with your syntax.  Please post the command you are using.  It could also be due to the excessively long path.

---

### Post by rcayea on 2009-11-09
Right now I am simply right clicking on it and selecting "extract here"

I haven't tried to change file names yet.

---

### Post by alphaniner on 2009-11-09
Sorry I assumed you were running from terminal.

In that case, I would move the archive to a more practical directory like ~/archives or something.  The "FROM UBUNTU 9.04 to go to 9.10" directory may be causing problems.

---

### Post by rcayea on 2009-11-09
ok. Thanks. I will move it around a bit, maybe shorten the title and see what happens.

---

### Post by rcayea on 2009-11-09
moved the two archives to my home folder, which is rcayea. Same result.

---

