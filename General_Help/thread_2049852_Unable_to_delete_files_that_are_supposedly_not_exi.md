---
title: "Unable to delete files that are supposedly not existing"
date: 2012-08-29
forum: General Help
---

### Post by allisvibration on 2012-08-29
I have an OSX Mountain Lion Laptop connected to and ubuntu 11.10 system in my local network and tried to copy one rather large .csv file from the OSX machine to the ubuntu machine. I stopped the file transfer as I realised it created several empty files in the target folder.

I now have a few hundred files sitting there which I can not delete using:

   ```
 sudo find . -name "*.csv" | xargs /bin/rm
```

It is saying file does not exist....



Any ideas on that?

All these files sitting there make the system incredible slow :(

---

### Post by Vaphell on 2012-08-29
how about this:
```
sudo find . -name "*.csv" -delete
```

---

