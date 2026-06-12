---
title: "Frustrated with acpidump -- help"
date: 2012-04-13
forum: General Help
---

### Post by clueless11 on 2012-04-13
I'm trying to create dsdt in 11.10.
when i run the following command I get the error message "no match at -e line blahblahblah"

mkdir ACPI && dmesg | perl -we '$n=0; while (<>) { if (($t,$a,$l,$o) = (/^[^a-zA-Z]*ACPI: ([-._A-Z0-9]{4,4}) +([0-9A-F]{8,8}), ([0-9A-F]{4,4})+(?:\s*\(([^)]+))?/)) { $o && $o=~s/[^-._a-zA-Z0-9]+/-/g; ($cmd="acpidump -a $a -l $l > \"ACPI/${t}".($o?"_$o":"").".aml\""); print "Running command: \"$cmd\"\n"; system($cmd); ++$n; } } die("No match") unless $n;' && zip -r ACPI-Tables.zip ACPI

Can anybody tell me what I'm doing wrong???

---

### Post by roelforg on 2012-04-13
Can you tell us what it's supposed to do?

---

### Post by clueless11 on 2012-04-13
trying to dump acpi tables

eg see [http://www.projectosx.com/forum/index.php?showtopic=359](http://www.projectosx.com/forum/index.php?showtopic=359)

---

### Post by roelforg on 2012-04-13
> **clueless11 said:**
> trying to dump acpi tables
 
eg see [http://www.projectosx.com/forum/index.php?showtopic=359](http://www.projectosx.com/forum/index.php?showtopic=359)
 
Maybe it has to do with you trying to use a command from an osx site on linux

---

### Post by clueless11 on 2012-04-13
i gather not ... this is what the site says.  There are numerous other sites (google) that give the same linux command incidentally.

boot some Live CD and install "acpidump". It's usually in a package called "acpidump" (Ubuntu) or "pmtools" (Fedora). Then become root using "sudo su" (Ubuntu) or "su -" (Fedora) and run the following command:
CODE
mkdir ACPI && dmesg .....

---

### Post by roelforg on 2012-04-13
[http://manpages.ubuntu.com/manpages/oneiric/man1/acpidump.1.html](http://manpages.ubuntu.com/manpages/oneiric/man1/acpidump.1.html)
 
Check the examples,
does anything come close to what you want?
 
The last one looks like it does the same.

---

### Post by clueless11 on 2012-04-13
I suspect its doing a lot more ... looks to me like probably a bunch of acpidump commands with a variety of switches probing a lot of memory addresses??? ... but I can't really figure out the perl script (I tried to break it down and gave up :<), nor why its burping.



perl -we '$n=0;

while (<>)

{ if (($t,$a,$l,$o) = (/^[^a-zA-Z]*ACPI: ([-._A-Z0-9]{4,4}) +([0-9A-F]{8,8}), ([0-9A-F]{4,4})+(?:\s*\(([^)]+))?/))

{ $o && $o=~s/[^-._a-zA-Z0-9]+/-/g;

($cmd="acpidump -a $a -l $l > \"ACPI/${t}".($o?"_$o":"").".aml\"");

print "Running command: \"$cmd\"\n";

system($cmd); ++$n; } }

die("No match") unless $n;'

&& zip -r ACPI-Tables.zip ACPI

---

