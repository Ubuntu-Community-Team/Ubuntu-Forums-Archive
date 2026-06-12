---
title: "+r to /var/log/auth.log ? is this safe ?"
date: 2011-04-11
forum: General Help
---

### Post by highspider on 2011-04-11
Is it safe to add +r permission to the auth.log.1 and auth.log
 
-rw-r--r-- /var/log/auth.log
-rw-r--r-- /var/log/auth.log.1

why i needed to ~ on apache2 web (password protected area) - I made a simple perl.cgi to read successful and failed ssh login attempts.

of courses the "www-data" users returned a error 500 thru apache2 with out adding the +r to the auth.log 
is this ok. 

The basic script is here for reference. (not good at perl first script ever)
```
#!/usr/bin/perl
#
# Will display a html report of all successful and failed ssh logins
# by: highspider

#VARS
$SUCCESS='Accepted password for';
$FAILED='Failed password for';
my @files= qw| /var/log/auth.log /var/log/auth.log.1  |;
my @ary;

#LOOP AND GET THE FILE'S DATA INTO AN ARRAY
for my $filename(@files){
    open INF, $filename ||
        die "Cannot open $filename for reading: $!\n";
    push @ary, <INF>;
    close INF;
}

#HTML HEADER
print "Content-type:text/html\n\n";
print "<html>\n";
print "<head><title>SSH LOGS</title></head>\n";
print "<body>\n";

#SUCCESSFUL TABLES
print "<h1>Succesful SSH logins</h1>\n";
print "<table border=\"1\">\n";
foreach $line (@ary) {
 if ($line =~ m/$SUCCESS/) {
   print "<tr><td>$line<tr><td>\n";
 }
}
print "</table>\n";

#FAILED TABLES
print "<h1>Failed SSH logins</h1>\n";
print "<table border=\"1\">\n";
foreach $line (@ary) {
 if ($line =~ m/$FAILED/) {
   print "<tr><td>$line<tr><td>\n";
  }
}
print "</table>\n";

#HTML FOOTER
print "</body>\n";
print "</html>\n";

```

---

### Post by highspider on 2011-04-14
[COLOR=Red][COLOR=RoyalBlue]BUMP[/COLOR]

Is it safe to add +r permission to the auth.log.1 and auth.log[/COLOR]

 [COLOR=RoyalBlue](Ubuntu default)_______________________ [/COLOR]                                            [COLOR=RoyalBlue] (my new permissions)[/COLOR]
-rw-r----- /var/log/auth.log_______.______-rw-r--r-- /var/log/auth.log
 -rw-r----- /var/log/auth.log.1____________-rw-r--r-- /var/log/auth.log.1

---

### Post by chadlongstaff on 2013-02-26
probably not, add yourself to the "adm" group instead as this group already has read access to /var/log/auth.log

---

### Post by matt_symes on 2013-02-26
Old thread. Closed.

---

