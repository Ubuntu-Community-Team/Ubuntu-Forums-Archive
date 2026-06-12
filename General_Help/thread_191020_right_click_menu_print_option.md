---
title: "right click menu print option?"
date: 2006-06-07
forum: General Help
---

### Post by jamesrw on 2006-06-07
is there any way to quickly send a text document to my printer by right clicking.. similar to the 'nautilus-open-terminal' plugin which opens a terminal by right clicking in a specific directory?

or for example like the 'send to' menu in micro$haft winblows...

---

### Post by Ragazzo on 2006-06-07
You can put scripts to ~/.gnome2/nautilus-scripts/ folder and they will show up in Scripts-menu when you right-click.

For example, you could create a file "print.sh":
```

#!/bin/bash

lpr $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

```

---

### Post by fancyl on 2008-03-26
What would I have to type to do that? I want to Right-click (shell) print my OpenOffice docs.

Thanks.

---

