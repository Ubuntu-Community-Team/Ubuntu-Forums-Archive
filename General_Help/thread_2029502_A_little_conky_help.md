---
title: "A little conky help?"
date: 2012-07-19
forum: General Help
---

### Post by tmette on 2012-07-19
I'm new to conky so excuse the ignorance here. I'm having trouble getting conky to display properly after a login or reboot. Here is what my startup script looks like

```

#!/bin/sh
sleep 20
conky -d -c ~/.conky
exit
```

I've also attached a screenshot of what shows up on my desktop. I know the startup script is working but it's not showing the customization. My conky script is located in ~/.conky so I assume the filepath is correct in the startup script? Is there something simple that I'm missing here? :confused:

---

### Post by Toz on 2012-07-19
Can you post back the contents of ~/.conky?

From where/how are you executing this script?

---

### Post by Vaphell on 2012-07-19
what happens when you change ~/.conky to absolute /home/yourname/.conky?

---

### Post by tmette on 2012-07-20
> **Toz said:**
> Can you post back the contents of ~/.conky?

From where/how are you executing this script?

The contents of .conky are two directories:

conky_grey (empty)
conky_orange (scripts for the orange theme)

annd I moved the contents of conky_grey in the ~/.conky directory:

conky_grey.lua
conky_grey (this one doesn't have an extension which I don't understand?)


Also, I tried changing the start-up script to an absolute path (/home/username/.conky) and that resulted in no change.

I appreciate the help with this, hopefully I can get it working properly. If it helps, I also got these conky scripts from [this website]("http://www.techdrivein.com/2011/02/6-awesome-conky-configs-that-just-works.html") and followed the directions

---

### Post by Vaphell on 2012-07-20
```
$ conky --help
-c, --config=FILE         **config file** to load
```
directory is not going to work, point to the actual file (~/.conky/conky_grey?)

it even says so on that page
> To run Conky_Grey, copy paste the following command into Terminal.

conky -c ~/.conky/conkyrc_grey

---

### Post by Shadius on 2012-07-20
> **Vaphell said:**
> ```
$ conky --help
-c, --config=FILE         **config file** to load
```
directory is not going to work, point to the actual file (~/.conky/conky_grey?)

it even says so on that page

Yes, I agree with this. This should work.

---

### Post by tmette on 2012-07-20
Thanks guys, I'll test it out later this weekend!

---

### Post by Habitual on 2012-07-20
```
conky -c /home/jj/Documents/Archives/Conky/Clock/digital
```

is a real-life example of a working conky startup via .sh

---

