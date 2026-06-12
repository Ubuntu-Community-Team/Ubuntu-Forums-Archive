---
title: "Mysql issue"
date: 2009-07-03
forum: General Help
---

### Post by nunki on 2009-07-03
Im currently running Intrepid. I have the lamp server installed via 
```

sudo tasksel install lamp-server

```

I have developed a website (currently hosted on my machine) backed by a mysql database. I am using php to fetch data from the database to display on the webpage. Everything works fine when I connect from my computer. When I connect from another computer, the html builds fine, and some other php functions work. However, no database results are ever sent back.

Looks like there must be some setting that is preventing mysql from running queries when the source is not my computer. Im a little stumped.

---

### Post by Celauran on 2009-07-03
The queries themselves are still originating from your machine, though. Is PHP returning any errors? Anything in the logs?

---

### Post by nunki on 2009-07-03
Ok Ive narrowed this down. Looks like it works fine if you use firefox. IE on the otherhand is not playing nice (shocker). IE reports no errors, but somehow is not liking my jQuery or my php.

---

### Post by Celauran on 2009-07-03
Sounds more like an IE display problem than a problem with the queries themselves. Have you tried commenting out however the results are intended to be displayed and replaced it with some simple echo statements? This should help narrow down specifically what the problem is and then you can go from there.

---

