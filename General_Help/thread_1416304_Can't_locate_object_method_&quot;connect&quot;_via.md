---
title: "Can't locate object method &quot;connect&quot; via package &quot;DBI&quot;"
date: 2010-02-25
forum: General Help
---

### Post by kantu on 2010-02-25
I get the follwing error message when i try to run a simple perl script to access mysql , I tried googling but didnt help 

Can't locate object method "connect" via package "DBI"

```

#!/usr/bin/perl

use CGI::Carp qw(fatalsToBrowser);
my $dsn = 'dbi:mysql:try:localhost:3306'; 
 
# set the user and password 
my $user = 'usr'; 
my $pass = 'pwd'; 
 
# now connect and get a database handle  
my $dbh = DBI->connect($dsn, $user, $pass) 
 or die "Can&#8217;t connect to the DB: $DBI::errstr\n"; 
my $sth = $dbh->prepare("select name from test"); 
$sth->execute; 
 
while(@row = $sth->fetchrow_array()) { 
 print "$row[0]<br>"; 
} 
$sth->finish();
$dbh->disconnect();
```

---

### Post by kantu on 2010-02-26
i forgot to use 
use DBI ;
now it works

---

