---
title: "Running Bioperl"
date: 2010-12-15
forum: General Help
---

### Post by mindlessbrain on 2010-12-15
Hey guys.

I am having an awful time getting bioperl up and running on my Ubuntu 10.04 OS. Its very sad. I love bioperl!

If I'm running something that doesn't require the internet, like file parsing, its fine. But when I have something like this (just a standard piece of code straight from the Wiki):

```

#!/usr/bin/perl 
 
use Bio::DB::SwissProt; 
 
$database = new Bio::DB::SwissProt; 
 
$seq = $database->get_Seq_by_id("MALK_ECOLI"); 
 
my $out = Bio::SeqIO->newFh ( -fh => \*STDOUT, 
-format => 'fasta'); 
 
print $out $seq;

``` 

I get this:

root@jill-desktop:/home/jill/Desktop# perl testing_bioperl4.pl

-------------------- WARNING ---------------------
MSG: id (MALK_ECOLI) does not exist
---------------------------------------------------

------------- EXCEPTION: Bio::Root::Exception -------------
MSG: Did not provide a valid Bio::PrimarySeqI object
STACK: Error::throw
STACK: Bio::Root::Root::throw /usr/local/share/perl/5.10.1/Bio/Root/Root.pm:328
STACK: Bio::SeqIO::fasta::write_seq /usr/local/share/perl/5.10.1/Bio/SeqIO/fasta.pm:178
STACK: Bio::SeqIO::PRINT /usr/local/share/perl/5.10.1/Bio/SeqIO.pm:661
STACK: testing_bioperl4.pl:12

Anybody have any clue as to whats going on? I've been fighting this off and on for over a month, and its getting a bit ridiculous. Someone told me it might be a mysql error, and mysql in fact did not work, but now supposedly it does. 

root@jill-desktop:/home/jill/Desktop# mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 41
Server version: 5.1.41-3ubuntu12.8 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> exit
Bye

Also, I followed the instructions on the Wiki to get the Ubuntu Server installed. 

Help would be very, very appreciated!

~mb

---

### Post by mindlessbrain on 2010-12-15
I installed the GBrowser, and now I get a different error. 

root@jill-desktop:/home/jill/Desktop# perl testing_bioperl4.pl

-------------------- WARNING ---------------------
MSG: id (MALK_ECOLI) does not exist
---------------------------------------------------

------------- EXCEPTION  -------------
MSG: Did not provide a valid Bio::PrimarySeqI object
STACK Bio::SeqIO::fasta::write_seq /usr/local/share/perl/5.10.1/Bio/SeqIO/fasta.pm:178
STACK Bio::SeqIO::PRINT /usr/local/share/perl/5.10.1/Bio/SeqIO.pm:661
STACK toplevel testing_bioperl4.pl:14

--------------------------------------

I think there's some kind of path or environmental variable not set right, but I just can't figure out what.

---

### Post by mindlessbrain on 2010-12-15
Ok, I figured part of the issue out. 

When using Swissprot I need to set up my database so it looks like:

my $banque = Bio::DB::SwissProt->new('-servertype' => 'expasy', 'hostlocation' => 'australia');

its got to have that extra bit on there, maybe because I'm not in the US? Weird things happen when you're out of the country.

I still can't get retrieving a swissprot sequence through Bio::Perl to work, but that is ok I guess. I've tried out GenBank, and that works. So far everything else seems to work. 

So, there ya go. Hope I've helped someone.

---

### Post by zhlu1986 on 2011-06-24
> **mindlessbrain said:**
> Ok, I figured part of the issue out. 

When using Swissprot I need to set up my database so it looks like:

my $banque = Bio::DB::SwissProt->new('-servertype' => 'expasy', 'hostlocation' => 'australia');

its got to have that extra bit on there, maybe because I'm not in the US? Weird things happen when you're out of the country.

I still can't get retrieving a swissprot sequence through Bio::Perl to work, but that is ok I guess. I've tried out GenBank, and that works. So far everything else seems to work. 

So, there ya go. Hope I've helped someone.

Thank you .
I have the same problem.
Lucy to see your messages.
I still do not know how to use swissprot database

---

