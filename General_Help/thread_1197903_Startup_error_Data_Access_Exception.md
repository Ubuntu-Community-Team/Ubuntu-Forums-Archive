---
title: "Startup error: Data Access Exception"
date: 2009-06-26
forum: General Help
---

### Post by muskets on 2009-06-26
Hi; I'm a Linux noob (on Jaunty), and I've had this [financial software]("http://www.moneymapsoftwaresupport.com/") running fine for the past couple months, but all of a sudden it won't open. The error message it gives is the following:[INDENT]                                  com.crown.moneymatters.common.dao.DataAccessException: com.crown.moneymatters.common.dao.DataAccessException: java.sql.SQLException: Table not found in statement [update account]
     at com.crown.moneymatters.common.dao.jdbc.JdbcDaoUtil.init(Unknown Source)
     at com.crown.moneymatters.common.dao.jdbc.JdbcDaoUtil.init(Unknown Source)
     at com.crown.moneymatters.common.dao.DaoUtil.init(Unknown Source)
     at com.crown.moneymatters.common.gui.mainapp.appMoneyMatters2006.fileLaunch(Unknown Source)
     at com.crown.moneymatters.common.gui.mainapp.appMoneyMatters2006.<init>(Unknown Source)
     at com.crown.moneymatters.common.gui.mainapp.appMoneyMatters2006.main(Unknown Source)
     at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
     at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
     at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
     at java.lang.reflect.Method.invoke(Method.java:597)
     at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
     at com.install4j.runtime.Launcher.main(Unknown Source)
 Caused by: com.crown.moneymatters.common.dao.DataAccessException: java.sql.SQLException: Table not found in statement [update account]
     at com.crown.moneymatters.common.dao.jdbc.JdbcDaoUtil.setCurrentDate(Unknown Source)
     ... 12 more
 Caused by: java.sql.SQLException: Table not found in statement [update account]
     at org.hsqldb.jdbc.Util.sqlException(Unknown Source)
     at org.hsqldb.jdbc.jdbcStatement.fetchResult(Unknown Source)
     at org.hsqldb.jdbc.jdbcStatement.executeUpdate(Unknown Source)
     ... 13 more


[/INDENT]I don't know jack about Linux, so it's as good as Greek to me. I can follow directions well, though, so if anyone has a suggestion I'd be glad to try it.


Thanks!

---

