---
title: "How to put &quot;Search for files&quot; into file browser context menu?"
date: 2010-06-11
forum: General Help
---

### Post by pstein on 2010-06-11
I can start "Search for files" from menu
 
Applications->Accessories->Search for files....
 
and it works fine.
 
However I would like to put it into the context menu of the Nautilus File Browser.
 
When I select it e.g. for folder
 
/home/peter
 
then the start base directory should be obviously set AUTOMATICALLY to
/home/peter
 
how can I achieve this?
 
Peter

---

### Post by kaibob on 2010-06-11
You can do that with a nautilus script with the following:

```
#!/bin/bash

gnome-search-tool --path=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
```

For information about nautilus scripts see:

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

You can also do this with Nautilus Actions--which is a Nautilus extension--but I no longer use this extension and can't provide more specific information on the exact procedure.

[http://www.grumz.net/index.php?q=taxonomy/term/5/9](http://www.grumz.net/index.php?q=taxonomy/term/5/9)

---

### Post by skooter1121 on 2010-06-14
I prefer to use:

#!/bin/bash

gnome-search-tool

Since this uses any gconf-editor custom search settings you may have set. While the:

gnome-search-tool --path=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS

uses the default settings.



-Skooter

---

### Post by Morbius1 on 2010-06-14
I use a slight variation of kaibob's nautilus script:
```
#!/bin/sh
 gnome-search-tool --hidden --contains= --path="$(echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS)"
```The "hidden" and "contains=" are just predetermined options being set.

If you use "--path=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" it will default to the parent folder if the location you're selecting has spaces in the directory name. For example if I try to do a search on:

/Windows/WinXP/Documents and Settings 

it will start the search at /Windows/WinXP.

If I use the echo variation it will start and Documents and Settings.

Either way just create the script
Save it to /home/username/.gnome2/nautilus-scripts/Search
Make it executable
And it should show up on a right click under "Scripts"

---

### Post by kaibob on 2010-06-14
> **Morbius1 said:**
> I use a slight variation of kaibob's nautilus script:
```
#!/bin/sh
 gnome-search-tool --hidden --contains= --path="$(echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS)"
```The "hidden" and "contains=" are just predetermined options being set.

If you use "--path=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" it will default to the parent folder if the location you're selecting has spaces in the directory name. 
Thanks for pointing that out. I tried my suggestion  with some directories with spaces in their names, and it does not work even if I double quote $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS. Your suggestion works fine, though.

---

