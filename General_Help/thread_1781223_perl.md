---
title: "perl"
date: 2011-06-13
forum: General Help
---

### Post by irakla7777777 on 2011-06-13
i want to execute system command with perlm but it gives me error.

command is wmic client. 
here it is 


#!/usr/bin/perl
open (EP, "/home/user/Templates/domainpc.log");

while (<EP>) {
    chomp;
 
system('wmic -U domain/user%password //$_  "SELECT name from Win32_process"');

}


problem is that  perl not perceives $_ this symbol

if i use :

system('wmic -U domain/user%password //192.168.1.10  "SELECT name from Win32_process"');

command execut well.

---

### Post by Dave_L on 2011-06-13
Perl interprets variables in double-quoted strings, not single-quoted strings. Try this:

```
system("wmic -U domain/user%password //$_ 'SELECT name from Win32_process'");
```

---

