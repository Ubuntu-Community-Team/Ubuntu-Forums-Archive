---
title: "ODBC admin program crashing"
date: 2009-07-07
forum: General Help
---

### Post by Bob Unitt on 2009-07-07
Gentlefolk,

Not sure where's the best place to post this question - so I'll try here...

I'm on ubuntu 9.04. I'm trying to get ODBC working to a local MySQL database. I've installed MySQL (5.0.75-0ubuntu10.2) and that's working fine. I then tried to follow the instructions for installing ODBC given on <http://www.howtoforge.com/adding-an-odbc-driver-for-mysql-on-ubuntu> and got as far as apparently completing step 4 'Add the mysql driver to the list of ODBC drivers' successfully.

Subsequently, whenever I run 'sudo iodbcadm-gtk' and try to open the 'ODBC Drivers' tab or add a 'User DSN' or a 'System DSN', the program crashes-out completely with a 'Segmentation fault' in the terminal window.

Please help before I tear-out what little hair I have left...

---

### Post by flubbard on 2009-07-08
I'm having the same problem.

 - flub

---

### Post by Bob Unitt on 2009-07-08
> **flubbard said:**
> I'm having the same problem.

 - flub

Are you on the same versions of things as me ?

---

### Post by flubbard on 2009-07-08
I'm using eebuntu (close enough) with administrator version 3.52.6.  

I'm guessing that the seg fault is caused by either an incorrectly addressed object or otherwise trying to do something with the object that it expects to be there that isn't.
 
I seem to have found my problem.  In my case, one of the files that I specified when creating the ODBC connection was not present.  I had to remove the entry in the ~/.odbcinst.ini file before I could run the admin tool again without the seg fault.  It looks like the default file is just blank.  I found these by doing
```

#locate .odbcinst.ini

```
This time I tried to browse to the file to make sure that I had it typed wrong.  Originally, I misread the 'S' as a 5.  I no longer have the seg fault.  

Hope this helps!

 - flub

---

### Post by Bob Unitt on 2009-07-09
Flub - I tried what you said, but it didn't make any difference :-

I delete the existing '.odbcinst.ini' and '.odbc.ini' files.
I run 'iodbcadm-gtk' in a terminal.
I select the 'ODBC Drivers' tab.
I press 'Add a driver'.
I enter 'MySQL' as the driver description.
I browse/select '/usr/lib/odbc/libmyodbc.so' as the Driver file name.
I browse/select '/usr/lib/odbc/libodbcmyS.so' as the Setup file name.
I press 'OK'.

I immediately get a 'Segmentation fault' and the program crashes.

Subsequent executions of the program crash with a 'Segmentation fault' as soon as the 'ODBC Drivers' tab is selected.

I've tried this both as 'root' (via 'sudo') and as an ordinary user, but it makes no difference.

One possible variation is that I didn't add any 'Keyword'/'Value' pairs when I initially created the MySQL ODBC driver, did you ?

Bob Unitt

---

### Post by Bob Unitt on 2009-07-09
Flub - additional information:-

I've just tried adding an ODBC Driver using the 'libnn.so'/'libodbcnnS.so' files, and it didn't cause a crash - so whatever is wrong would appear to be MySQL specific, rather than a generic 'iodbcadm-gtk' problem.

Bob

---

### Post by Bob Unitt on 2009-07-09
This is getting utterly frustrating - I've successfully installed and added MySQL drivers to a couple of laptops, one running ubuntu 8.10, and the other running ubuntu 9.04; in both cases they work perfectly, so the _only_ machine I can't get this to work on is the one I _really_ need it on !

I've also de-installed and re-installed on the machine giving the error, with no change :-(

What is a 'Segmentation Fault', anyway ? - the way it works occasionally but not consistently has the feel of an uninitialised variable whose contents are whatever happened to be in that bit of memory when the program was started - one of the worst bugs to find and fix, IMHO.

Alternatively - is there another ODBC Administrator package I could use instead ?

---

### Post by flubbard on 2009-07-09
I do not have not put any "Keyword/Value" pairs in my installation.  I would wonder if there might be a file permission issue on your '/usr/lib/odbc/libmyodbc.so' and '/usr/lib/odbc/libodbcmyS.so' files.  I see that I have rw-r--r-- access on all of these files.  I would also note that I am running that admin as root and not through sudo, though I'm not sure if that would make any difference.

My understanding of a seg fault is that it will occur whenever you have a program accessing and area of memory outside of what the operating system has allotted to it.  This could occur if a variable was not properly initialized, or not initialized to the right size.  It could also occur if you open and then read from a file that is not present.  You can normally avoid seg faults by proper error checking and checking that files are present before either opening or reading from each.  My guess is that it is a combination of the file not being in the location and with the permissions that it needs to have coupled with the fact that the program does not first check for the error and give you something that you can work with.

I'm not sure of other admin pieces but would like to know about some.  I am having my own problem at this point.  I have my database on a remote server, but even when I put in the "server" keyword/value pair, it says that the user is not authorized on "localhost"  I can't seem to get it to look to another server other than localhost.  I would appreciate any thoughts.

  - Flub

---

### Post by Bob Unitt on 2009-07-09
Flub, thanks for your help so far. 

Could you please post the contents of your '.odbcinst.ini' and '.odbc.ini' files here, so I can try and craft mine by hand ? 

Concerning you 'localhost' problem - at what stage does it report the error - when you define it, or not until you try to use it ?

I'll keep looking for alternate ODBC admins, and report here if I find one that works.

TIA
Bob

---

### Post by Bob Unitt on 2009-07-09
Flub,

I found this web-page on my travels - it might help with your 'LocalHost' problem (or, of course, it might not...) :-

<http://www.iodbc.org/index.php?page=docs/faq>

HTH
Bob

---

### Post by flubbard on 2009-07-09
Thanks for the link.  I will take a look at it.  Below is my .odbc.ini file

```

[ODBC Data Sources]
mysql_db_pgm = Legal Assistant

[mysql_db_pgm]
Driver      = /usr/lib/odbc/libmyodbc.so
Description = Test Database
Server      = 172.16.0.101
Database    = test_db
Password    = PASS
User        = USER

```

I get my error when I try to test the connection.  After I put in the username and password, it displays the error claiming that 'USER'@'localhost' could not be logged in, where it should be @'172.16.0.101'

  - flub

---

### Post by Bob Unitt on 2009-07-09
> **flubbard said:**
> Thanks for the link.  I will take a look at it.  Below is my .odbc.ini file
<SNIP>


Thanks for that, any chance of your '.odbcinst.ini' as well ?

> **flubbard said:**
> I get my error when I try to test the connection.  After I put in the username and password, it displays the error claiming that 'USER'@'localhost' could not be logged in, where it should be @'172.16.0.101'
  - flub

Can you actually connect to the server at all ?

Bob

---

### Post by flubbard on 2009-07-09
Sorry, I missed the other file.  The odbcnst.ini file is:

```

[ODBC Drivers]
Legal Assistant = Installed

[Legal Assistant]
Driver = /usr/lib/odbc/libmyodbc.so
Setup  = /usr/lib/odbc/libodbcmyS.so

```

As for connecting to the server,  I can connect through mysql between the same machines using 
```

$ mysql -h 172.16.0.101 -u USER -p

```
and everything works as it should to allow me to get at the mysql command prompt.  But I cannot seem to get the odbc connection to work.  I have checked, and it does appear to be trying to connect to the localhost because when I put in appropriate user information for the local machine, the odbc test succeeds.  Still having trouble with the remote.  I'm wondering at this point if I either have the keyword wrong or if I have to do something funny to indicate that it should be addressed by IP address.

  - flub

---

### Post by Bob Unitt on 2009-07-13
I wonder if either of our problems are due to these unresolved ubuntu bugs ?

<https://bugs.launchpad.net/ubuntu/+source/myodbc/+bug/262715>
<https://bugs.launchpad.net/ubuntu/+source/myodbc/+bug/119387>

If so, I'm not sure what to do next :-(

---

### Post by flubbard on 2009-07-13
Well, I've had some progress with my project, but I'm not sure how much help it's going to be for you.  First, I was able to find that there is an environment variable MYSQL_HOST which is referenced at times, but it did not seem to fix my problem.  I am able to connect to a local database, but not able to specify the database, at least through the test function.

As for my particular issue, I have been trying to run a Visual Basic program in Linux which accesses data from a MySQL database through the ADODB connector.  After working on this for quite a while, I thought my best bet would be to use the unix-odbc utility to underly the wine database controls.  Well, I'm not sure in the end of that was really necessary.  I was able to install the ActiveX controls that were necessary in Wine and then create the new data source, again from within wine.  At this point, Wine is correctly emulating the windows environment, including ActiveX and data sources and the program functions correctly, just from the Windows executable.  

I'm not sure where you stand at this point.  What error message are you still getting?

---

### Post by Bob Unitt on 2009-07-13
Still where I was - having added the MySQL ODBC drivers as per documentation, any attempt to access the '... DSN' or 'ODBC Drivers' tab on the 'Administrator' screen causes the admin program to crash. Running from a terminal shows that the cause of the crash is a 'Segmentation Fault', but there's nothing in any log-files. This is really annoying as I have the MySQL database working OK through it's own utilities, it's just the ODBC connection that I can't get configured.

I've just ahd a thought - which did you install first, MySQL or the ODBC stuff ?

---

### Post by flubbard on 2009-07-13
I believe that I installed the ODBC stuff first, but they are both on now.  A couple of thoughts:

What user are you using to run the admin piece?  Also, where all do you have .iodbc.ini and odbcinst.ini files.  I would recommend first running 
```
# updatedb
```
Then running 
```

# locate iodbc.ini 
# locate odbcinst.ini

```
You should see one of each in the example folder and then one for each of your users that have databases set up.  What happens if you delete these files (other than the examples).  You should probably make a copy first, or simply rename them.

I'm not sure why it should be throwing a seg fault if no data sources are being initialized.

  - flub

---

### Post by Bob Unitt on 2009-07-14
Flub, I begin to suspect for a number of reasons that my problems (ODBC wasn't the only thing that wasn't quite right) were down to my rather old hardware not being compatible with ubuntu 9.04. I'm currently engaged in re-building the whole system from scratch on ubuntu 8.04 (I'm told 8.10 is to be avoided). I'll update this thread when I've finished re-installing everything and can test ODBC again.
Bob

---

### Post by Bob Unitt on 2009-07-14
Flub,

Looks like I was right - I've now reverted to ubuntu 8.04 on this PC and have successfully accessed a MySQL database via ODBC from 'OpenOffice Database'.

I've also done most of this OK an a newer laptop on ubuntu 9.04, so I'm fairly sure it's not a native problem with ubuntu. One thing that does appear to be broken, however, is the dependencies for the ODBC connection in OpenOffice - you need to install (via Synaptic) the package 'unixodbc' to get rid of the 'missing libodbc.so.1' message.

HTH
Bob

---

### Post by flubbard on 2009-07-14
Bob,

Glad to hear that it seems to be working now.  I have in mind in my reading that unixodbc normally needs to be installed becuase the others are more or less wrappers which eventually use unixodbc on the back end.  I'm not certain of this, but I think that is the gist of what I read.  Glad to hear that it is working for you now.

  - flub

---

