---
title: "Script"
date: 2012-02-19
forum: General Help
---

### Post by zergling on 2012-02-19
Hi Guys,
I am opening up this thread because I would like to implement a script that open up a terminal and execute a particular command on files and/or directories.

I created a new action in Dolphin called "Secure Delete" but when I execute it, I get this message...

shred: missing file operand
Try `shred --help' for more information.


In Dolphin in "Secure Delete" I have 
```
konsole -e "~/test.sh"
```

In my script file called **test.sh** I have
```
#!/bin/bash
shred -u -v -n 5

echo "\n*** Shred will close itself within 10 seconds ***\n"
count=10
while [ $count -ge 0 ]
do
echo $count seconds
sleep 1
count=`expr $count - 1`
done
sleep 3
```

Is there a way to store the files that I select and pass them to the test.sh script?

On the other hand, if I use ```
shred -u -v -n 5
``` in my "Secure Delete" without using the script test.sh everything works beautifully but I cannot see the progress of the deleting file :(

Could someone help me out?

Bye and thank you very much.

---

### Post by Khayyam on 2012-02-19
The "missing file operand" error is due to the fact that your script is not passing a "file" to the command. 

```
#!/bin/bash

shred -u -v -n 5 "$@"
```

> **zergling said:**
> Is there a way to store the files that I select and pass them to the test.sh script?

The shell uses "propositional parameters" for referencing parts of the commands"arguments", for instance "$1" is the first parameter, $2 the second (and so on). There are also "special parameters", "$@" expands to all parameters begining from $1.

So, by adding "$@" all files passed to the script will be the "parameters" provided to the command.

HTH ... khay

---

### Post by zergling on 2012-02-19
It worked!
Thank you very much Khayyam.

---

