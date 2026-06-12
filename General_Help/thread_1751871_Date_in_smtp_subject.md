---
title: "Date in smtp subject"
date: 2011-05-07
forum: General Help
---

### Post by SAKRI on 2011-05-07
Hi all,

I want to insert previous date in the email subject using perl, I am using the below:



$smtp->mail($from);
foreach $t (@to){
$smtp->to($t);
}
$previous_date=$(date '+%F' --date '1 days ago');
$smtp->data();
$SUBJECT="Test 1";
foreach $t (@to){
$smtp->datasend("To: $t\n");
}
$smtp->datasend("Subject:" .$SUBJECT & previous_date ."\n");

Thanks in advance.:)

---

### Post by Lars Noodén on 2011-05-07
Look at [Date::Calc](http://search.cpan.org/~stbey/Date-Calc-6.3/lib/Date/Calc.pod) in [CPAN](http://www.cpan.org/) for tools to manipulate dates.  It's in the package **libdate-calc-perl**.

---

