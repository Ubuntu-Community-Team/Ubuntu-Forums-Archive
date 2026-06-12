---
title: "blender core dumped"
date: 2012-09-16
forum: General Help
---

### Post by halitalptekin on 2012-09-16
Hi there.I have linux 12 64 bit.If I start the blender I got a below problem.

```

halit@laptop-Inspiron-N4050:~$ blender
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  32
  Current serial number in output stream:  32
Parçalama ar&#305;zas&#305; (core dumped)


```glxinfo | grep render
```


X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```lspci | grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] 
```

Please help me.Thanks

---

