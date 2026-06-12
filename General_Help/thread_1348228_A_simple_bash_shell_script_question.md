---
title: "A simple bash shell script question"
date: 2009-12-07
forum: General Help
---

### Post by Koalano on 2009-12-07
Hi friends,

Suppose I have a bash shell script file *testscript* which contains just the following lines:
```

#!/bin/bash
currentLocation=$PWD
echo "hello world" > $currentLocation/test.txt
```If I run *testscript* from a terminal, then a text file named *test.txt* which contains the words "hello world" is created in the current directory.

However, if I create a launcher for *testscript*, and then click that launcher, *test.txt* is not created. I don't understand this, because I expect *test.txt* will also be created in the this case...

Edit: Ah, I'm sorry for the above incorrect description. Actually, *test.txt* is created, but it is located in my home (~/) directory, instead of the directory containing *testscript*. Well, it's still strange, because I think that *test.txt* should be created in the same location with *testscript*.

---

### Post by OllyDBG on 2009-12-07
```
type test
``` and you will know why :)

---

### Post by Koalano on 2009-12-07
> **OllyDBG said:**
> ```
type test
``` and you will know why :)
Hi,

Thank you for your answer, but could you explain it more clearly? Sorry because I'm pretty slow.

---

### Post by OllyDBG on 2009-12-07
Well test is a built-in shell command and BASH will not understand that its a file

in short try to name your file anything but test :)

try test1.sh for example

---

### Post by gvoima on 2009-12-07
> **OllyDBG said:**
> Well test is a built-in shell command and BASH will not understand that its a file
in short try to name your file anything but test :)
try test1.sh for example

This is not relevant, because he named his script testscript.

---

### Post by Agent ME on 2009-12-07
Your script writes to the current directory - not the directory you're running the script from. This isn't always the same.

If you run the script as "./testscript.sh", you're obviously in the same folder as it. But it's possible to run it from a different folder by supplying the path. Try it - as an example: "/home/myuser/scripts/testscript.sh" would launch the script from anywhere, but test.txt will end up in the same directory as you.

There's also a minor problem with your script. If you're in a folder that has a space in the name (like "/home/myuser/My Scripts"), test.txt won't be made. You need to put the output filename in quotes:
```
#!/bin/bash
currentLocation=$PWD
echo "hello world" > "$currentLocation/test.txt"
```

---

### Post by Koalano on 2009-12-07
> **Agent ME said:**
> Your script writes to the current directory - not the directory you're running the script from. This isn't always the same.

If you run the script as "./testscript.sh", you're obviously in the same folder as it. But it's possible to run it from a different folder by supplying the path. Try it - as an example: "/home/myuser/scripts/testscript.sh" would launch the script from anywhere, but test.txt will end up in the same directory as you.

There's also a minor problem with your script. If you're in a folder that has a space in the name (like "/home/myuser/My Scripts"), test.txt won't be made. You need to put the output filename in quotes:
```
#!/bin/bash
currentLocation=$PWD
echo "hello world" > "$currentLocation/test.txt"
```

Thank you very much for your detailed answer. Now I've got it. :D

Best regards,

Koalano.

---

### Post by BenAshton24 on 2009-12-07
```
#!/bin/bash
currentLocation=**$0**
echo "hello world" > "$currentLocation/test.txt"
```

That way, wherever you put your script it will always put the test.txt in the same folder as the script...

Ben.

---

### Post by Agent ME on 2009-12-07
That won't work. $0 gives the name of the script or executable as it was called, not the script's directory.

---

### Post by BenAshton24 on 2009-12-07
> **Agent ME said:**
> That won't work. $0 gives the name of the script or executable as it was called, not the script's directory.

oh ye... (faceplam)

```

#!/bin/bash
currentLocation=`dirname "$0"`
echo "hello world" > "$currentLocation/test.txt"

```

There -.-

---

### Post by Koalano on 2009-12-07
> **BenAshton24 said:**
> oh ye... (faceplam)

```

#!/bin/bash
currentLocation=`dirname "$0"`
echo "hello world" > "$currentLocation/test.txt"

```There -.-

I confirm this one works. Thank you very much buddy :)

---

