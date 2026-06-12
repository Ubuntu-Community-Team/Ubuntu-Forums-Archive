---
title: "DB and Java"
date: 2010-06-15
forum: General Help
---

### Post by miko5054 on 2010-06-15
im trying to connect to an open office Db with the eclipse but i guess im doing something wrong
this is the connection code
```
  try {
	      Class.forName("org.hsqldb.jdbcDriver");
	      connection = DriverManager.getConnection("jdbc:hsqldb:file:/home/mikmik/&#1513;&#1493;&#1500;&#1495;&#1503; &#1506;&#1489;&#1493;&#1491;&#1492;/New Database", "SA", "");
	    } catch (Exception e) {
	      System.err.println("Unable to find and load driver");
	      System.exit(1);
	    }
```

---

