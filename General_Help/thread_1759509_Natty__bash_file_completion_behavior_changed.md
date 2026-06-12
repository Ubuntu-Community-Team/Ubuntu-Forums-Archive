---
title: "Natty : bash file completion behavior changed"
date: 2011-05-15
forum: General Help
---

### Post by raghu1111 on 2011-05-15
Before Ubuntu 11.04, bash completion of filename quotes spaces etc.
If you have file with name 'Test File Name.txt' and 
if you do:
**$ ls Test**<press TAB>
Before Natty, bash would expand this to:
**$ ls Test\ File\ Name.txt**
Note that spaces is escaped.
But in Natty, it does not:
**$ls Test File Name.txt**
And if you press enter now, the it fails because the space is not escaped.

Is there a fix to revert back to old (I think correct) behavior? It does not change even after sourcing /etc/bash_completion.

I am surprised no one has complained about this yet.

---

### Post by Rocket2DMn on 2011-05-15
I don't see this behavior on my fresh install of Natty, but clearly other people have had this issue.  It looks like there is a workaround in bug [lpbug]716008[/lpbug]. Seems to be a bug in acroread actually.

---

### Post by raghu1111 on 2011-05-15
Thanks Rocket. The work around there worked.

$ sudo sed -i '"s/_filedir/_filedir_acroread/" /etc/bash_completion.d/acroread.sh'

In my case I just removed /etc/bash_completion.d/acroread.sh

Why is bash loading completion customization even if my .bashrc is empty (for testing)?
Also it is appalling that some stupid package can screw up every command line typed!

---

### Post by Rocket2DMn on 2011-05-15
Yeah that seems like a pretty serious bug, but it has a Canonical employee as the assignee so I won't do further triage on the bug.

I'm not intimately familiar with all the bash file configurations, but the completion capability is probably built in by default and not dependent on a .bashrc file unless it is overridden there.

---

