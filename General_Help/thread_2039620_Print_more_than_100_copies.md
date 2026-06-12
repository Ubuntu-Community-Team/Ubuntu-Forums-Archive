---
title: "Print more than 100 copies"
date: 2012-08-09
forum: General Help
---

### Post by davidub on 2012-08-09
Hi all,

I have a problem with ubuntu that remains even in last version. When I try to print more than 100 copies (i.e. from firefox), the printer options window always change the number to 100 and the up arrow becomes disabled. Is there any way to change this limit? I often need to print more than 1.500 copies so I have to do the same action 15 times...

Thank you in advance,

David

---

### Post by albandy on 2012-08-09
> **davidub said:**
> Hi all,

I have a problem with ubuntu that remains even in last version. When I try to print more than 100 copies (i.e. from firefox), the printer options window always change the number to 100 and the up arrow becomes disabled. Is there any way to change this limit? I often need to print more than 1.500 copies so I have to do the same action 15 times...

Thank you in advance,

David

It seems a bug.
You can do a trick:
print to pdf and open it with adobe acrobat reader, then you can print without limit.

---

### Post by davidub on 2012-08-09
I don't think it can be a bug, because it happens since old versions of ubuntu, and even from terminal using lpd you cannot print more than 100...

---

### Post by albandy on 2012-08-10
> **davidub said:**
> I don't think it can be a bug, because it happens since old versions of ubuntu, and even from terminal using lpd you cannot print more than 100...


this will do the trick:

```

#! /bin/bash
FILENAME=$1
MULTIPLIER=$2
NUMCOPY=$3

until [ $MULTIPLIER -lt 1 ]
do
lpr $FILENAME -#$NUMCOPY
let MULTIPLIER-=1
done



```


Create a file with this code, for example myprint.sh
then assing execution permisions to that file: chmod u+x myprint.sh

usage:
./myprint.sh file_to_print multiplier num_of_copies

For example, if I want to print 1000 copies:
./myprint.sh book.pdf 10 100

---

### Post by plucky on 2012-08-10
> **davidub said:**
> I don't think it can be a bug, because it happens since old versions of ubuntu, and even from terminal using lpd you cannot print more than 100...

Have a look at ```
man lpadmin
``` and look at the parameter **job-page-limit=value**

From the CUPS Help page > CUPS supports page and size-based quotas for each printer. The quotas are tracked individually for each user, but a single set of limits applies to all users for a partiuclar printer. For example, you can limit every user to 5 pages per day on an expensive printer, but you cannot limit every user except Johnny.

The job-k-limit, job-page-limit, and job-quota-peiod options determine whether and how quotas are enforced for a printer. The job-quota-period option determines the time interval for quota tracking. The interval is expressed in seconds, so a day is 86,400, a week is 604,800 and a month is 2,592,000 seconds. The job-k-limit option specifies the job size limit in killobytes. The job-page-limit option specifies the number of pages limit.

For quotas to be enforced, the period and at least one of the limits must be set to a non-zero value. The following options will enable weekly quotas with the given size and page count limits:

/usr/sbin/lpadmin -p printer -o job-quota-period=604800 \
    -o job-k-limit=1024 ENTER
/usr/sbin/lpadmin -p printer -o job-quota-period=604800 \
    -o job-page-limit=100 ENTER

Or, you can combine all three options on the same line.

While there is no way to query the current quota state for a particular user, any application can request a list of jobs for a user and printer that can be used to easily determine that information.

Good Luck

---

