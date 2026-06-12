---
title: "mysql error + java"
date: 2011-07-06
forum: General Help
---

### Post by BattousaiX on 2011-07-06
I've been working on an issue for a while now, several hours and would appreciate some assistance.

I have a laptop running Windows 7 with Mysql Server 5.1
And Ubuntu 11.04 running Mysql Server 5.1

I wound up just testing some database connectivity with a project I was working on, and it fails with.

```

private static void dropTable(String table) throws ClassNotFoundException, SQLException{
		Class.forName(DRIVER);
		Connection conn=DriverManager.getConnection(URL, USER, PASS);
		String sql="drop table if exists "+table;
		Statement stmt=conn.createStatement();
		stmt.executeUpdate(sql);
	}

```

on line 

```

Connection conn=DriverManager.getConnection(URL, USER, PASS);

```

While I do realize this is Java code, my issue is not the code itself, as it works fine when I switch a variable above to run it locally on my laptop.  


The exceptions are as follows.

```

Exception in thread "main" com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1116)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:344)
	at com.mysql.jdbc.ConnectionImpl.coreConnect(ConnectionImpl.java:2333)
	at com.mysql.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:2370)
	at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2154)
	at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:792)
	at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:47)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:381)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:305)
	at java.sql.DriverManager.getConnection(Unknown Source)
	at java.sql.DriverManager.getConnection(Unknown Source)
	at ConnectionPool.dropTable(ConnectionPool.java:39)
	at ConnectionPool.main(ConnectionPool.java:24)
Caused by: java.net.ConnectException: Connection refused: connect
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(Unknown Source)
	at java.net.PlainSocketImpl.connectToAddress(Unknown Source)
	at java.net.PlainSocketImpl.connect(Unknown Source)
	at java.net.SocksSocketImpl.connect(Unknown Source)
	at java.net.Socket.connect(Unknown Source)
	at java.net.Socket.connect(Unknown Source)
	at java.net.Socket.<init>(Unknown Source)
	at java.net.Socket.<init>(Unknown Source)
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:257)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:294)
	... 16 more

```

While the code is working on my laptop using mysql service there, I can rule out the JDBC.  After when executing the code nothing occurs in mysql logs.

```

-rw-r-----  1 mysql             adm        0 2011-07-06 15:02 mysql.err
-rw-r-----  1 mysql             adm        0 2011-07-06 15:02 mysql.log

```

and nothing syslog is not updated with any failures, related to mysql.  Mysql is running

```

kenpachi@kenpachi-desktop:/var/log$ ps aux | grep mysql
mysql     4318  0.0  0.8 137364 18364 ?        Ssl  15:02   0:00 /usr/sbin/mysqld
kenpachi  4490  0.0  0.0   4156   848 pts/0    S+   15:36   0:00 grep --color=auto mysql

```

and is listening on 3306

```

kenpachi@kenpachi-desktop:/var/log$ sudo netstat -nape | grep 3306
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      114        22275       4318/mysqld

```

I thought it would be a connectivity issue, but the same exact occurrence happened compiling the same test class on Ubuntu.

I would like help making sure that I have a proper setup.

```

kenpachi@kenpachi-desktop:/var/log$ mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 39
Server version: 5.1.54-1ubuntu4 (Ubuntu)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| translator         |
+--------------------+
3 rows in set (0.00 sec)

mysql> show tables;
+----------------------+
| Tables_in_translator |
+----------------------+
| language             |
+----------------------+
1 row in set (0.00 sec)


```

my.cnf

```

#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user            = mysql
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1
#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1

log_error                = /var/log/mysql/error.log

# Here you can see queries with especially long duration
#log_slow_queries       = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
#log_bin                        = /var/log/mysql/mysql-bin.log
expire_logs_days        = 10
max_binlog_size         = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet      = 16M

[mysql]
#no-auto-rehash # faster start of mysql but no tab completition

[isamchk]
key_buffer              = 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/

```

---

### Post by BattousaiX on 2011-07-06
I now have it working locally on Ubuntu using the Ubuntu mysql server, but still not finding any failures in a log, not sure how to go further from here.

---

### Post by dragonfly41 on 2011-07-06
some clues here?

[http://ubuntuforums.org/showthread.php?t=991141](http://ubuntuforums.org/showthread.php?t=991141)

post #9

---

### Post by BattousaiX on 2011-07-06
> **dragonfly41 said:**
> some clues here?

[http://ubuntuforums.org/showthread.php?t=991141](http://ubuntuforums.org/showthread.php?t=991141)

post #9

Thanks, just tried, still same issue.  :(

---

### Post by BattousaiX on 2011-07-06
Noticed a minor issue with hostname, changed, doesn't effect anything.  But my code was not actually reaching server, or should not have.  Let's see if this will change logging.

---

### Post by BattousaiX on 2011-07-06
No firewall rules or anything blocking.

```

kenpachi@kenpachi-server:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by BattousaiX on 2011-07-06
tcp dump ignoring SSH, as I connected via SSH.  This was ran while I was attempting to compile the above test.

```

kenpachi@kenpachi-server:~$ sudo tcpdump -vvvi eth0 | grep -v ssh
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
19:09:09.029129 IP (tos 0x10, ttl 64, id 21088, offset 0, flags [DF], proto TCP (6), length 172)
19:09:09.030129 IP (tos 0x0, ttl 64, id 32756, offset 0, flags [DF], proto UDP (17), length 71)
    kenpachi-server.45067 > homeportal.domain: [udp sum ok] 6812+ PTR? 70.1.168.192.in-addr.arpa. (43)
19:09:09.030645 IP (tos 0x0, ttl 128, id 8390, offset 0, flags [DF], proto TCP (6), length 40)
19:09:09.032442 IP (tos 0x0, ttl 255, id 18721, offset 0, flags [DF], proto UDP (17), length 204)
    homeportal.domain > kenpachi-server.45067: [udp sum ok] 6812* q: PTR? 70.1.168.192.in-addr.arpa. 1/1/1 70.1.168.192.in-addr.arpa. [2d] PTR Kenpachi-PC. ns: 70.1.168.192.in-addr.arpa. [11h35m28s] NS homeportal.gateway.2wire.net. ar: homeportal.gateway.2wire.net. [11h35m28s] A 192.168.1.254 (176)
19:09:09.032619 IP (tos 0x0, ttl 64, id 32756, offset 0, flags [DF], proto UDP (17), length 71)
    kenpachi-server.45609 > homeportal.domain: [udp sum ok] 5892+ PTR? 74.1.168.192.in-addr.arpa. (43)
19:09:09.036601 IP (tos 0x0, ttl 255, id 18722, offset 0, flags [DF], proto UDP (17), length 208)
    homeportal.domain > kenpachi-server.45609: [udp sum ok] 5892* q: PTR? 74.1.168.192.in-addr.arpa. 1/1/1 74.1.168.192.in-addr.arpa. [2d] PTR kenpachi-server. ns: 74.1.168.192.in-addr.arpa. [11h35m28s] NS homeportal.gateway.2wire.net. ar: homeportal.gateway.2wire.net. [11h35m28s] A 192.168.1.254 (180)
19:09:09.036814 IP (tos 0x0, ttl 64, id 32757, offset 0, flags [DF], proto UDP (17), length 72)
    kenpachi-server.44345 > homeportal.domain: [udp sum ok] 34573+ PTR? 254.1.168.192.in-addr.arpa. (44)
19:09:09.040684 IP (tos 0x0, ttl 255, id 18723, offset 0, flags [DF], proto UDP (17), length 206)
    homeportal.domain > kenpachi-server.44345: [udp sum ok] 34573* q: PTR? 254.1.168.192.in-addr.arpa. 1/1/1 254.1.168.192.in-addr.arpa. [2d] PTR homeportal. ns: 254.1.168.192.in-addr.arpa. [11h35m28s] NS homeportal.gateway.2wire.net. ar: homeportal.gateway.2wire.net. [11h35m28s] A 192.168.1.254 (178)
19:09:09.389782 IP (tos 0x40, ttl 1, id 22994, offset 0, flags [none], proto UDP (17), length 446)
    192.168.1.64.1045 > 239.255.255.250.8082: [udp sum ok] UDP, length 418
19:09:09.389901 IP (tos 0x0, ttl 64, id 32846, offset 0, flags [DF], proto UDP (17), length 74)
    kenpachi-server.41493 > homeportal.domain: [udp sum ok] 29892+ PTR? 250.255.255.239.in-addr.arpa. (46)
19:09:09.461253 IP (tos 0x0, ttl 255, id 18724, offset 0, flags [DF], proto UDP (17), length 131)
    homeportal.domain > kenpachi-server.41493: [udp sum ok] 29892 NXDomain q: PTR? 250.255.255.239.in-addr.arpa. 0/1/0 ns: 239.in-addr.arpa. [48m4s] SOA sns.dns.icann.org. noc.dns.icann.org. 2011062221 7200 3600 604800 3600 (103)
19:09:09.561880 IP6 (hlim 255, next-header UDP (17) payload length: 54) fe80::216:76ff:feb1:3ebf.mdns > ff02::fb.mdns: [udp sum ok] 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
19:09:09.561937 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 74)
    kenpachi-server.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
19:09:10.127798 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.67 (Broadcast) tell homeportal, length 46
19:09:10.162618 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has BattousaiX-PC (Broadcast) tell homeportal, length 46
19:09:10.563166 IP6 (hlim 255, next-header UDP (17) payload length: 54) fe80::216:76ff:feb1:3ebf.mdns > ff02::fb.mdns: [udp sum ok] 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
19:09:10.563218 IP (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 74)
    kenpachi-server.mdns > 224.0.0.251.mdns: [udp sum ok] 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
19:09:11.163823 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.64 (Broadcast) tell homeportal, length 46

```

Server: kenpachi-server: 192.168.1.74
Laptop: kenpachi-pc    : 192.168.1.70

---

### Post by BattousaiX on 2011-07-07
Full java code - As I'm doing testing, I had to recreate the table a few times with another project I started when parsing a site, using the same methods to test, I just changed the SQL string.  Here is the code.

```

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.sql.Statement;

public class ConnectionPool {
	//private final static String USER = "kenapchi";
	private final static String USER = "################";
	private final static String PASS = "################";
	//private final static String URL="jdbc:mysql://localhost:3306/translator";
	private final static String URL="jdbc:mysql://kenpachi-server:3306/translator";
	private final static String DRIVER = "com.mysql.jdbc.Driver";
	private final static String SERVER = "kenpachi-server";

	private final static String PORT = "3306";
	private final static String DATABASE = "translator";

	//private final static String URL = "jdbc:mysql://" + SERVER + ":" + PORT+ "//" + DATABASE + "?autoReconnect=true&reconnectAtTxEnd=true";

	public static void main(String args[]) throws ClassNotFoundException,
			SQLException {
		String languageTableString = "create table language(language_id smallint unsigned not null auto_increment, language varchar(20), primary key(language_id));";

		dropTable("language");
		// createTable(languageTableString);

	}

	private static void createTable(String sql) throws ClassNotFoundException,
			SQLException {
		Class.forName(DRIVER);
		Connection conn = DriverManager.getConnection(URL, USER, PASS);
		Statement stmt = conn.createStatement();
		stmt.executeUpdate(sql);
	}

	private static void dropTable(String table) {
		try {
			
			Class.forName(DRIVER);
			Connection conn = DriverManager.getConnection(URL, USER, PASS);
			String sql = "drop table if exists " + table;
			Statement stmt = conn.createStatement();
			stmt.executeUpdate(sql);
		} catch (com.mysql.jdbc.exceptions.jdbc4.CommunicationsException e) {
			System.out.println(e.getMessage());
			// we got dropped from the database.. it will auto reconnect so
			// let's call ourself again
			dropTable(table);
		} catch (Exception e) {
			System.out.println(e.getMessage());
		}
	}

	// private static void dropTable(String table) throws
	// ClassNotFoundException, SQLException{
	// Class.forName(DRIVER);
	// Connection conn=DriverManager.getConnection(URL, USER, PASS);
	// String sql="drop table if exists "+table;
	// Statement stmt=conn.createStatement();
	// stmt.executeUpdate(sql);
	// }
	//
	/*
	 * public void insertIntoSetListTable(int page, String date, String link,
	 * String song, String artist, String album) throws ClassNotFoundException,
	 * SQLException{ Class.forName(DRIVER); Connection
	 * conn=DriverManager.getConnection(URL, USER, PASS);
	 * 
	 * String sql=
	 * "INSERT INTO SET_LIST(page, date, link, song, artist, album) VALUES(?,?,?,?,?,?);"
	 * ;
	 * 
	 * PreparedStatement pstmt=conn.prepareStatement(sql); pstmt.setInt(1,
	 * page); pstmt.setString(2, date); pstmt.setString(3, link);
	 * pstmt.setString(4, song); pstmt.setString(5, artist); pstmt.setString(6,
	 * album); pstmt.executeUpdate(); conn.close(); }
	 */

}


```

---

### Post by BattousaiX on 2011-07-07
```

Exception in thread "main" com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1116)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:344)
	at com.mysql.jdbc.ConnectionImpl.coreConnect(ConnectionImpl.java:2333)
	at com.mysql.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:2370)
	at com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2154)
	at com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:792)
	at com.mysql.jdbc.JDBC4Connection.<init>(JDBC4Connection.java:47)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:381)
	at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:305)
	at java.sql.DriverManager.getConnection(Unknown Source)
	at java.sql.DriverManager.getConnection(Unknown Source)
	at ConnectionPool.insertLanguage(ConnectionPool.java:82)
	at ConnectionPool.main(ConnectionPool.java:27)
Caused by: java.net.ConnectException: Connection refused: connect
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(Unknown Source)
	at java.net.PlainSocketImpl.connectToAddress(Unknown Source)
	at java.net.PlainSocketImpl.connect(Unknown Source)
	at java.net.SocksSocketImpl.connect(Unknown Source)
	at java.net.Socket.connect(Unknown Source)
	at java.net.Socket.connect(Unknown Source)
	at java.net.Socket.<init>(Unknown Source)
	at java.net.Socket.<init>(Unknown Source)
	at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:257)
	at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:294)
	... 16 more

```

**Step 1 - Allow connection from client**
Add IP to /etc/my.cnf here
```

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1
bind-address            = **192.168.1.74**

```

Then restart mysql
```

kenpachi@kenpachi-server:/var/log$ sudo service mysql stop
mysql stop/waiting
kenpachi@kenpachi-server:/var/log$ sudo service mysql start
mysql start/running, process 2441

```

Which then leaves the following issue.

```

Exception in thread "main" com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException: INSERT command denied to user 'kenpachi'@'Kenpachi-PC' for table 'language'
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(Unknown Source)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(Unknown Source)
	at java.lang.reflect.Constructor.newInstance(Unknown Source)
	at com.mysql.jdbc.Util.handleNewInstance(Util.java:411)
	at com.mysql.jdbc.Util.getInstance(Util.java:386)
	at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:1052)
	at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3597)
	at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3529)
	at com.mysql.jdbc.MysqlIO.sendCommand(MysqlIO.java:1990)
	at com.mysql.jdbc.MysqlIO.sqlQueryDirect(MysqlIO.java:2151)
	at com.mysql.jdbc.ConnectionImpl.execSQL(ConnectionImpl.java:2625)
	at com.mysql.jdbc.PreparedStatement.executeInternal(PreparedStatement.java:2119)
	at com.mysql.jdbc.PreparedStatement.executeUpdate(PreparedStatement.java:2415)
	at com.mysql.jdbc.PreparedStatement.executeUpdate(PreparedStatement.java:2333)
	at com.mysql.jdbc.PreparedStatement.executeUpdate(PreparedStatement.java:2318)
	at ConnectionPool.insertLanguage(ConnectionPool.java:88)
	at ConnectionPool.main(ConnectionPool.java:27)

```

**Step 2 - Grant mysql access**
```

mysql> GRANT ALL PRIVILEGES ON *.* TO 'USER'@'SERVER' IDENTIFIED BY "PASSWORD";
Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

```

I still haven't looked into apparmor yet but I also did this in the process.

```

sudo aa-complain /usr/sbin/mysqld

```

---

