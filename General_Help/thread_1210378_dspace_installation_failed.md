---
title: "dspace installation failed"
date: 2009-07-11
forum: General Help
---

### Post by babbar.ankit on 2009-07-11
[email]babbar@babbar-lapi:/home/dspace/dspace-src/dspace/target/dspace-1.5.2-build.dir[/email]$ sudo ant fresh_install
Buildfile: build.xml

init_installation:

init_configs:

setup_database:
     [java] 2009-07-11 20:55:57,166 INFO  org.dspace.core.ConfigurationManager @ Loading system provided config property (-Ddspace.configuration): config/dspace.cfg
     [java] 2009-07-11 20:55:57,184 INFO  org.dspace.core.ConfigurationManager @ Using default log4j provided log configuration,if uninitended, check your dspace.cfg for (log.init.config)
     [java] 2009-07-11 20:55:57,184 INFO  org.dspace.storage.rdbms.InitializeDatabase @ Initializing Database
     [java] 2009-07-11 20:55:57,316 FATAL org.dspace.storage.rdbms.InitializeDatabase @ Caught exception:
     [java] org.postgresql.util.PSQLException: FATAL: password authentication failed for user "dspace"
     [java]     at org.postgresql.core.v3.ConnectionFactoryImpl.doAuthentication(ConnectionFactoryImpl.java:275)
     [java]     at org.postgresql.core.v3.ConnectionFactoryImpl.openConnectionImpl(ConnectionFactoryImpl.java:94)
     [java]     at org.postgresql.core.ConnectionFactory.openConnection(ConnectionFactory.java:65)
     [java]     at org.postgresql.jdbc2.AbstractJdbc2Connection.<init>(AbstractJdbc2Connection.java:116)
     [java]     at org.postgresql.jdbc3.AbstractJdbc3Connection.<init>(AbstractJdbc3Connection.java:30)
     [java]     at org.postgresql.jdbc3.Jdbc3Connection.<init>(Jdbc3Connection.java:24)
     [java]     at org.postgresql.Driver.makeConnection(Driver.java:369)
     [java]     at org.postgresql.Driver.connect(Driver.java:245)
     [java]     at java.sql.DriverManager.getConnection(DriverManager.java:620)
     [java]     at java.sql.DriverManager.getConnection(DriverManager.java:200)
     [java]     at org.apache.commons.dbcp.DriverManagerConnectionFactory.createConnection(DriverManagerConnectionFactory.java:65)
     [java]     at org.apache.commons.dbcp.PoolableConnectionFactory.makeObject(PoolableConnectionFactory.java:294)
     [java]     at org.apache.commons.pool.impl.GenericObjectPool.borrowObject(GenericObjectPool.java:974)
     [java]     at org.apache.commons.dbcp.PoolingDriver.connect(PoolingDriver.java:176)
     [java]     at java.sql.DriverManager.getConnection(DriverManager.java:620)
     [java]     at java.sql.DriverManager.getConnection(DriverManager.java:222)
     [java]     at org.dspace.storage.rdbms.DatabaseManager.getConnection(DatabaseManager.java:550)
     [java]     at org.dspace.storage.rdbms.DatabaseManager.loadSql(DatabaseManager.java:923)
     [java]     at org.dspace.storage.rdbms.InitializeDatabase.main(InitializeDatabase.java:100)

BUILD FAILED
/home/dspace/dspace-src/dspace/target/dspace-1.5.2-build.dir/build.xml:585: Java returned: 1

Total time: 1 second

---

