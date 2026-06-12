---
title: "bash color in a script not working"
date: 2011-03-05
forum: General Help
---

### Post by UncleBoarder on 2011-03-05
This works (meaning it changes color) from CLI...

echo -e '\e[1;36m' testCyan

But if I put that same exact line in a script, the result is not colored, and it displays the actual command on screen like this...

-e '\e[1;36m' testCyan

The script is obviously executing.  Why isn't it interpreting the backslash command in the script?

---

### Post by Vaphell on 2011-03-06
do you use sh or bash to execute the script?

color.sh:
```

echo -e '\E[32;01m'test...
echo -e '\E[1;22m'test...
echo -e '\E[1;36m'testCyan
tput sgr0

```
bash color.sh:
```

**[COLOR="DarkGreen"]test...[/COLOR]**
[COLOR="Green"]test...[/COLOR]
**[COLOR="Cyan"]testCyan[/COLOR]**

```
sh color.sh:
```

-e \E[32;01mtest...
-e \E[1;22mtest...
-e \E[1;36mtestCyan
```

sh seems to not recognize -e as a parameter or something.

use bash hashbang in your script to define bash (#!/bin/bash) as a shell to call.

---

### Post by UncleBoarder on 2011-03-06
Thanks!

---

