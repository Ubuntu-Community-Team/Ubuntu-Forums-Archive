---
title: "Another Grub 2 doubt"
date: 2010-02-15
forum: General Help
---

### Post by jsriz on 2010-02-15
hi guyz 
Think i finally am getting along with customizing grub2
need a litll help 
in menu.lst we culd add a blank line like the default
"
title Other operating systems:
root
"

i tried writing a script similar to this 


"
#!/bin/sh -e
echo "Adding Title"
cat<<EOF
menuentry "######Welcome To SriZ-Lapi######"
{
set root 
}
EOF
"

named it 06_title put it in /etc/grub.d  
ran chmod +x 
ran update-grub2
Result:

no echo of Adding Title
no menuentry in grub on restart

please tell me where i went wrong:o

---

### Post by jsriz on 2010-02-15
Shameless self bump!!!

---

### Post by oldfred on 2010-02-15
did you use ) or } for the last line?

Simple entry.

menuentry "Reboot" {
    reboot
}

---

### Post by jsriz on 2010-02-15
my bad
sry ill correct that it was 
}
upon reboot some error flashes for a fraction of sec

---

### Post by oldfred on 2010-02-15
There is a line at the top of 40_custom that it says not to delete. Perhaps it needs that line? 
also set root=  but I do not know if it will accept a blank or has to have an entry.

---

### Post by jsriz on 2010-02-19
Ha AT LAST Worked


```

#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

echo "Adding Title"
cat<<EOF
menuentry "######Welcome To SriZ-Lapi######"
{
set root=
}
EOF

```


But in running sudo upgrade-grub it does not echo Adding Title(shudnt it)
But happy with ma customization and 1st shot at shell scripting

---

### Post by jsriz on 2010-02-19
> **oldfred said:**
> did you use ) or } for the last line?

Simple entry.

menuentry "Reboot" {
    reboot
}

hey i jus wanted to know what is the command for shutdown

---

