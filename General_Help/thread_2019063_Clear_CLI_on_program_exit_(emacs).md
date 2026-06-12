---
title: "Clear CLI on program exit (emacs)"
date: 2012-07-07
forum: General Help
---

### Post by Volens on 2012-07-07
How would one have the system run "clear" on exiting emacs?

Would there be some way to do it through a .bashrc or .emacs file?

I have only been able to find articles discussing running programs when bash exits.

---

### Post by Volens on 2012-07-07
In a moment of clarity I realized I could make a bash script that runs clear after running emacs and that can still take arguments.

```

#!/bin/bash

emacs $1
clear

```

I clearly need more coffee.

---

### Post by msammels on 2012-07-07
Haha, Volens, it happens to us all :P Glad you got it sorted.

---

