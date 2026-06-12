---
title: "Having troubles with fastboot from Android SDK"
date: 2012-02-23
forum: General Help
---

### Post by waloshin on 2012-02-23
I know this is Mac, but I have also tried this on Ubuntu with the same errors:

I am getting this:

cd /Users/waloshin/Pictures/an/platform-tools/fastboot: /Users/waloshin/Pictures/an/platform-tools/fastboot: cannot execute binary file

[IMG]http://i41.tinypic.com/bhrom.png[/IMG]

Or if I try this: 

[img]http://i40.tinypic.com/3582rlu.png[/img]

[IMG]http://i43.tinypic.com/1gkqb5.png[/IMG]

The file is in there:

---

### Post by HeroOfCanton on 2012-02-23
Just a guess, but maybe the permissions are wrong?

```
chmod 755 ./fastboot 
```

---

### Post by drillerccg on 2012-03-03
I've written this on XDA [http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62](http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62)

---

