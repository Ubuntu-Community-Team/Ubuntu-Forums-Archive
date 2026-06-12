---
title: "How To: GET COMPIZ AND UNITY 2D WORKING"
date: 2011-04-30
forum: General Help
---

### Post by homy06 on 2011-04-30
So even though unity should work with my card it doesn't, I get the usual bugs like harware activated, but not in use type stuff. 

So I installed Unity 2d and it worked, but no compiz :(

I found out how to get compiz and unity to play nice, and it's really simple.

install the Compiz Fusion Icon, you can find it in synaptic or the command:

```
sudo apt-get install fusion-icon
```

Then when you click on the icon it should appear in your upper right panel.

Right click it and go down to compiz options, you should see the option for 
Indirect Rendering, click it if it's not already checked. 

Then right click again and check the Reload Windows Manager and it should blank out for sec then come back with all your old compiz keys working. 

Hopefully this helps someone. It's not unity, but it'll do until the bugs are fixed. 

Don't forget to put it in the startup application menu. That way you don't need to do it everytime you log in. when you do this, I noticed the icon doesn't appear in the upper right corner, but it still works.

---

### Post by arbrandes on 2011-05-06
If I run fusion-icon at startup (after having chosen compiz), weird things happen when I log in.  Mostly, the top bar breaks.  Have you witnessed this problem, and if so, have you found a workaround?

[edit]
Found a workaround.  Simply put, I created a bash script that sleeps 15 seconds before replacing metacity with compiz.  In my machine this gives unity-2d enough time to load its stuff.

```

#!/bin/bash

sleep 15
compiz --replace ccp --indirect-rendering

```

I then proceeded to call the script from startup, and all is well.

Also, forks that use unity-2d with compiz might like to remove the double title bar of maximized windows:

[http://jaket.is-a-geek.com/blog/linux/remove-titlebar-on-maximized-windows-with-compiz](http://jaket.is-a-geek.com/blog/linux/remove-titlebar-on-maximized-windows-with-compiz)
[/edit]

---

