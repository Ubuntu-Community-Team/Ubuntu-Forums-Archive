---
title: "shell Script to boost Compiz (for poor graphics cards)"
date: 2011-02-03
forum: General Help
---

### Post by GNU MaXo on 2011-02-03
hey guys, I made a simple script that boost Compiz by giving it less nice value. which helps for people like me with lousy Graphic cards (i.e, Intel !!) to reduce compiz laggs while doing heavy processing.

the script is targeted to be executed at init.d, so it'll run automatically after each restart. it takes only two steps to apply it:

**_Step 1:_** in terminal, write this:
```
gksu gedit /usr/bin/comboost
```
then copy and paste the following code in the text editor:
```
#!/bin/sh

compiz=$(pgrep compiz)
until [ "$compiz" != "" ];
do
	compiz=$(pgrep compiz)
	sleep 10
done

renice -10 -p $compiz
```
save and close, then in the terminal write this:
```
sudo chmod +x /usr/bin/comboost
```

**_Step 2:_** in the terminal write this:
```
sudo gedit /etc/init.d/rc
```
and before the last line (that says "exit 0") add this:
```
comboost
```

so finally it'll appear like this:
```
..
comboost
exit 0
```

now you're done :guitar:

you can execute it right away from terminal:
```
sudo comboost
```
or restart your PC.

it should work with any linux distro.
enjoy..

---

