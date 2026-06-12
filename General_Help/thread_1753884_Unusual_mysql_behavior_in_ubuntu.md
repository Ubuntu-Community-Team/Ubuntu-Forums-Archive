---
title: "Unusual mysql behavior in ubuntu"
date: 2011-05-09
forum: General Help
---

### Post by akuthor on 2011-05-09
I run a mysql server on my LAN and have run into an issue with machines running ubuntu accessing the data in a timely manner.  I've been banging my head against this for a while now and can't seem to get too clear a grip on it, but here is what I know:

[LIST]
[*]Any connection to the server from an ubuntu installation using either openoffice or libreoffice (via the JDBC connector) operates so slowly that it takes upwards of 10 seconds for simple queries to be accomplished.  This behavior was not always the case 2+ years ago the one ubuntu box I had accessing the server worked just fine, but after some upgrade (I wish I could remember which, probably Lucid, but I can't guarantee that)this behavior appeared.  I assumed at the time that is was just that particular machine and since it was a secondary machine never bothered to troubleshoot it.  Now, new machines with completely fresh Natty installs exhibit the exact same behavior.
[*]The server used to run on Red Hat EL 5 but has been ported over to Ubuntu and the problem has been consistent over both of those OSes.  So it appears to be independent of the server.  In addition, it seems to not be related to the stack space issue that many mysql admins report when running off ubuntu; I've long since fixed that issue.
[*]It does not appear to be a general linux issue.  Client connections from Red Hat machines with the exact same configuration work at normal (i.e., very fast) speed.
[*]I don't think it's an openoffice/libreoffice issue. Not only do these programs work as expected on Red Hat installs, but the windows versions (with JDBC) work just fine as well.
[*]Given that I'm using the JDBC for these connections, I also tried different java run-times.  The issue exists under both the open-java and sun-java JRE's.
[/LIST]

Anyone seen this before, or got any ideas?  I'm completely out at this point.

---

### Post by DaithiF on 2011-05-09
I don't have any concrete suggestions on what the issue might be, but first thing I would try to figure out is whether the problem on the ubuntu clients is jdbc-specific, or applies to mysql generally.

so run one of the queries via the mysql command line client rather than via open office jdbc and see how long it takes.

e.g.
```
mysql -h server-ip -u user -ppassword -D database <<EOF
select field1,field2
from sometable
EOF
```

another thing -- are you configuring the clients with server names or IP address?  maybe you've got some DNS issues on the ubuntu boxes such that any server name look ups get stuck / take a long time.  use ping / dig etc. to see how long the dns replies take.

---

### Post by akuthor on 2011-05-09
Thanks for the reply.

I should have mentioned non-client connections as well in my initial post; command line connections do operate at full speed, as do connections through the gui MSQL query browser.  And while that does seem to point to either the client programs or the connector, both of these pieces function under all the other instances listed above, so I don't know what it is about ubuntu (or just as likely whatever it is I do during my typical install) that isn't talking with these pieces.

I should also mention that I've tried both the packaged ubuntu distribution JDBC and the download direct from mysql with the same results.

--edit:  Oh yeah, I'm using direct, static IP addressing so there's DNS issue.

---

### Post by DaithiF on 2011-05-09
interesting, i wonder if oo is starting up a new JVM for the connection.  can you monitor the number of java processes before & while running a query

something like:
```
watch -n 1 ps -ef | grep java | wc -l

```

otherwise I'd be curious to see if i can replicate the issue ... can you give me a simplest possible version of one of your OO files which manifests the issue, i can substitute a server of my own.  thanks

---

### Post by akuthor on 2011-05-09
Watch doesn't show any additional JVM's during any part of the oo process from opening to query.

Here's a stripped down version of the odb file.  Although, I've removed the username and server address it may be helpful to know that I connect with a mysql user profile that does not require password authentication for this database (I have tried adding password authentication and that didn't seem to fix the problem either).

The lag is noticeable (~1-2s) when opening or scrolling through a table or a simple query.  However, when opening the form, which requires the population of 3 linked tables, the lag is so extreme the system usually gives me a non-responsive window warning before it finishes building the window and populating the components.

---

### Post by DaithiF on 2011-05-10
thanks.  I ran some tests against a server of mine -- a very simple select query against a small table (500 rows).

I also experienced noticeable lag when scrolling through the resulting recordset -- it takes approx 5 seconds to respond if I hit the 'last record' navigation button, ie. to scroll through the 500 rows to get to the last page.

I ran some network packet captures, and the interesting thing is that the issue is not at the mysql level -- a single query was sent to the server and a single response returned (with all rows), and that was within about 10millisecs of the request.

So the issue is at the client level -- presumably either the JDBC driver or OO is then caching the results and returning them in chunks (very slowly) as OO asks for particular pages.

To try to see if the issue is OO client or JDBC driver, I switched to use the OO mysql native connector rather than JDBC (install libreoffice-mysql-connector and change the database connection type to Mysql (native)).  Same network pattern as before (ie. single request/response), but this time no noticeable lag when scrolling through the resultsets.

So basically the JDBC mysql driver isn't doing a very good job at efficiently caching the results and returning them to the client.  I tried the latest Mysql connector (5.1.16) as well as the version packaged in ubuntu 11.04 (5.1.10), and no difference in behaviour.

Is switching to the mysql native connector an option for you?

---

### Post by akuthor on 2011-05-10
I was using JDBC mainly for what I perceived to be maximum cross-platform compatibility of the client file.  Functionality, however, is more important so switching to the native mysql for the ubuntu boxes seems to solve the problem, and is no particular hardship.

The only question that remains is, is this worth a bug report and, if so, to whom?  As I've pointed out, JDBC used to work just fine on older versions of ubuntu and still works just fine on Red Hat EL 5 which says to me that there's an old version of some library file that works (given how far behind the curve RHEL5 is though, it could be a library several versions old).  So, did a recent library change break JDBC or did mysql fail to keep up with the development of some of it's dependencies?

Thanks again for all the help.

---

### Post by DaithiF on 2011-05-10
> **akuthor said:**
> I was using JDBC mainly for what I perceived to be maximum cross-platform compatibility of the client file.  Functionality, however, is more important so switching to the native mysql for the ubuntu boxes seems to solve the problem, and is no particular hardship.
great.

> 
The only question that remains is, is this worth a bug report and, if so, to whom?  As I've pointed out, JDBC used to work just fine on older versions of ubuntu and still works just fine on Red Hat EL 5 which says to me that there's an old version of some library file that works (given how far behind the curve RHEL5 is though, it could be a library several versions old).  So, did a recent library change break JDBC or did mysql fail to keep up with the development of some of it's dependencies?

To answer the 'to whom' question probably requires narrowing down the problem to either the JDBC driver itself (in which case oracle/mysql), or how the OO client interacts with/calls the driver (libreoffice developers).  Probably more effort that I have time for :) , but if I had to, I would start by trying to reproduce the lag with a simple java program calling the JDBC driver and scrolling through a recordset ... ie. take OO out of the loop and see if the problem remains.  I would be surprised if this is where the problem lies, that driver is surely too widely used to have a flaw like this.  So if its not possible to reproduce within a standalone java program, then next step is probably a look at the OO codebase and/or file a bug with that project.

---

