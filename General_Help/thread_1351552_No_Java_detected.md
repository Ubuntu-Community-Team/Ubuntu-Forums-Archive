---
title: "No Java detected"
date: 2009-12-10
forum: General Help
---

### Post by Despot Despondency on 2009-12-10
Hi,

I'm having a problem with a certain web page. When I load it up I get the following message

```

No Java detected. Java is the best way to view and solve problems, but if you cannot run it, try switching to Javascript mode.

```

I never seen it before. I thought I had java installed on my computer so I a bit confused.

Any ideas. TAI

---

### Post by Physical Hook on 2009-12-10
```
sudo apt-get install sun-java6-jre sun-java6-plugin

``````
update-alternatives --config java
```

Restart your browser and it should work.

---

### Post by beetleman64 on 2009-12-10
> **Physical Hook said:**
> ```
sudo apt-get install sun-java6-jre sun-java6-plugin

``````
update-alternatives --config java
```Restart your browser and it should work.

Additionally, in Firefox make sure Javascript is on by going to Edit>Preferences>Content and then make sure the "Enable Javascript box is checked.

---

### Post by Despot Despondency on 2009-12-10
Thanks. That did the trick.

---

