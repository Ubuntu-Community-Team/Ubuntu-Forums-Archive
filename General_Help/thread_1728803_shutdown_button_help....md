---
title: "shutdown button help..."
date: 2011-04-14
forum: General Help
---

### Post by oklokl on 2011-04-14
[COLOR=#3A32C3]10.10 M

test.sh

#!/bin/bash[/COLOR]
 [COLOR=#3A32C3]sudo [COLOR=#FF0000]halt;[/COLOR]sudo   sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;sync;[/COLOR]
 [COLOR=#3A32C3]sudo shutdown -h 1;sudo init 0;sudo poweroff



revise wishes T^T..](*,)
[/COLOR][COLOR=#3A32C3]Usage: [COLOR=#FF0000]halt[/COLOR] [OPTION]...[/COLOR] 
 [COLOR=#3A32C3]Halt the system.[/COLOR]
 
 [COLOR=#FF0000]Options:[/COLOR]
 [COLOR=#FF0000]  -n, --no-sync               don't sync before reboot or halt[/COLOR]
 [COLOR=#FF0000]  -f, --force                 force reboot or halt, don't call shutdown([/COLOR]
 [COLOR=#FF0000]  -p, --poweroff              switch off the power when called as halt[/COLOR]
 [COLOR=#FF0000]  -w, --wtmp-only             don't actually reboot or halt, just write wtmp[/COLOR]
  [COLOR=#FF0000]record[/COLOR]
 [COLOR=#FF0000]  -q, --quiet                 reduce output to errors only[/COLOR]
 [COLOR=#FF0000]  -v, --verbose               increase output to include informational messages[/COLOR]
 [COLOR=#FF0000]      --help                  display this help and exit[/COLOR]
 [COLOR=#FF0000]      --version               output version information and exit[/COLOR]
 
 [COLOR=#FF0000]This command is intended to instruct the kernel to reboot or halt the system;[/COLOR]
 [COLOR=#FF0000]when run without the -f option, or when in a system runlevel other than 0 or 6,[/COLOR]
 [COLOR=#FF0000]it will actually execute /sbin/shutdown.[/COLOR]

---

