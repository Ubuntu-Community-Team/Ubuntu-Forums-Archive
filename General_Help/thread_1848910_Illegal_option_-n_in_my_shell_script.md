---
title: "Illegal option -n in my shell script"
date: 2011-09-23
forum: General Help
---

### Post by shibby4555 on 2011-09-23
I'm pretty new at shell scripting. But I caught the bug and can't stop
I don't understand why I keep getting this error. I'm making a simple network information tool. And keep getting illegal option -n when I run it. Here is the script. Very simple, not remotely complete. 

I ran chmod u+x "filename" so it is executable. Any ideas?

```

#!/bin/sh

echo "Finding your external IP address..."
echo "Your IP is:"
wget -qO - http://www.whatismyip.org

sleep 3
read -n 1 -p "Press any key to continue"

```

---

### Post by patryk77 on 2011-09-23
I have one ;)

When you execute:
read -n 1 -p "Press any key to continue"

and it works, it's because it is being interpreted by the bash shell (at least, I assume that is what you use - it works for me).

Try this:
```
#!/bin/bash

echo "Finding your external IP address..."
echo "Your IP is:"
wget -qO - http://www.whatismyip.org
echo 
sleep 3
read -n 1 -p "Press any key to continue"

```

(The extra "echo" just adds a new line after wget)

---

### Post by Ancanus on 2011-09-23
If using sh:

```


#!/bin/sh

echo "Finding your external IP address..."
echo "Your IP is:"
wget -qO - http://www.whatismyip.org
sleep 3
echo -n "\nPress any key to continue..."
**read null**
```

If using bash:

```

#!/bin/**bash**

echo "Finding your external IP address..."
echo "Your IP is:"
wget -qO - http://www.whatismyip.org
sleep 3
read -n 1 -p "\nPress any key to continue"

```


You are getting this error because you are running your script using sh as the shell interpreter, but these read arguments only supported in bash.

---

### Post by shibby4555 on 2011-09-23
Wow, totally overlooked that.
So simple! Thanks

---

