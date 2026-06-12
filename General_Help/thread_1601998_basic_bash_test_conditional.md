---
title: "basic bash test conditional"
date: 2010-10-20
forum: General Help
---

### Post by meg23 on 2010-10-20
I basically need to test if sun-java6-bin exists in apt, and if not add the proper repository to get installed. This is more or less the script I want to run, however I cannot think how to make it work. 

test $(sudo apt-cache search sun-java6-bin)=0 ; then
		sudo echo deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner >> /etc/apt/sources.list
	else
		exit
	fi

---

### Post by CharlesA on 2010-10-20
```
#!/bin/bash

if [[ -z $(apt-cache search sun-java6-bin) ]]
then
echo "deb http://archive.canonical.com/ lucid partner" >> /etc/apt/sources.list
else
exit
fi
```

Run the whole script with sudo as you will run into permission denied errors if you redirect output with sudo.

---

### Post by meg23 on 2010-10-20
Thanks that did it. However, only using single brackets:

if [ -z $(apt-cache search sun-java6-bin) ]

---

### Post by CharlesA on 2010-10-21
It's better to use [[ instead of [. See [here]("http://mywiki.wooledge.org/BashGuide/Practices#Bash_Tests").

---

