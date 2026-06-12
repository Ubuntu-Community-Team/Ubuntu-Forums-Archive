---
title: "would this work?"
date: 2010-07-31
forum: General Help
---

### Post by jesseafrantz on 2010-07-31
I am trying to run a .batch file, I was wondering if this edit would make it work, this is a java application-loader. 

```

#bin/bash 
java -Xmx500m  -cp .;Theme.jar Gui 0 1 lowmem members 32 
pause 

```

---

### Post by lykeion on 2010-08-01
Well, it could work fine. Why don't you try it?

One thing to think of though is that you set the classpath to current dir . so if you run the script from elsewhere it won't work.

To solve this you can get the absolute path of the script and change to this dir before you launch the java app. Maybe something like this:
```
#resolve directory absolute path
SCRIPTPATH=$(echo $0 | sed s/.*\\///g)
if [ "$0" = "./$SCRIPTPATH" ];then
	ABSPATH=$(echo `pwd`/$0 | sed "s/\/$SCRIPTPATH//g" | sed 's/\/\.//g')
else
	ABSPATH=$(echo $0 | sed "s/\/$SCRIPTPATH//g")
fi
# change to absolute path
cd $ABSPATH

# then execute the java launcher line here:
java -Xmx500m (etc)
```PS. Noticed you missed the bang in **_[shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)")_**, maybe just a typo. Also for best portability use this instead:```
#!/usr/bin/env bash
```

---

### Post by jesseafrantz on 2010-08-01
> **lykeion said:**
> Well, it could work fine. Why don't you try it?

One thing to think of though is that you set the classpath to current dir . so if you run the script from elsewhere it won't work.

To solve this you can get the absolute path of the script and change to this dir before you launch the java app. Maybe something like this:
```
#resolve directory absolute path
SCRIPTPATH=$(echo $0 | sed s/.*\\///g)
if [ "$0" = "./$SCRIPTPATH" ];then
    ABSPATH=$(echo `pwd`/$0 | sed "s/\/$SCRIPTPATH//g" | sed 's/\/\.//g')
else
    ABSPATH=$(echo $0 | sed "s/\/$SCRIPTPATH//g")
fi
# change to absolute path
cd $ABSPATH

# then execute the java launcher line here:
java -Xmx500m (etc)
```PS. Noticed you missed the bang in **_[shebang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29")_**, maybe just a typo. Also for best portability use this instead:```
#!/usr/bin/env bash
```
My method didn't work but, I tried what you suggested and it worked fine. Thanks!

---

