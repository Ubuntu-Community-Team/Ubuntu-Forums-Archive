---
title: "Creating a special Launcher (chromium)"
date: 2011-05-04
forum: General Help
---

### Post by luvgirl12345 on 2011-05-04
Would it be possible to make a launcher that checks if a tab with a specified address is open and if it is just opens the browser with the tab selected... if not opens a new tab with the specified address?

Not sure if checking chromiums open tabs is possible... maybe this would need a extension of some sort!

Thanks

---

### Post by spikoley on 2011-05-06
I don't think you can check to see if a tab is open, but you can create a launcher to open a specific site.  Check the man page for the options.

```
man chromium-browser
```

The command should look something like this:

```
chromium-browser http://www.ubuntuforums.org
```

I don't think its exactly what you are looking for, but it should get you pointed in the right direction.

---

