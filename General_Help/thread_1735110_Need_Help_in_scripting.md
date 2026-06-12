---
title: "Need Help in scripting"
date: 2011-04-20
forum: General Help
---

### Post by v3ct0r on 2011-04-20
Hi all,
      I have been using kubuntu 10.10 for sometime...And it works just like dream for me..The problem is:

I use 3-4 proxy connections depending on which is the fastest at that time...I have edited my apt.conf for proxy and added all my proxies in there..I comment out the proxies each time when i have to switch to some other proxy...doing this from command line is very irritating..

can anyone suggest how to write a script to change the proxies automatically???
Any other solution to this problem????
Hope i have made myself clear enough..This is my first post..So, excuse me if i am not clear enough...

---

### Post by v3ct0r on 2011-04-23
BUMP!!!!1
if i am not clear enough,please tell so.....

---

### Post by Vaphell on 2011-04-23
can you show the relevant part of the config file where the changes occur and describe what exactly should happen? I am not familiar with proxy configuration but i can manipulate text :)

---

### Post by v3ct0r on 2011-04-24
> **Vaphell said:**
> can you show the relevant part of the config file where the changes occur and describe what exactly should happen? I am not familiar with proxy configuration but i can manipulate text :)




#Acquire::http::proxy "http://usr1:pwd1@proxy1:port/";
#Acquire::https::proxy "https://usr1:pwd1@proxy1:port/";
#Acquire::ftp::proxy "ftp://usr1:pwd1@proxy1:port/";

Acquire::http::proxy "http://localhost:8118/";
Acquire::https::proxy "https://localhost:8118/";
Acquire::ftp::proxy "ftp://localhost:8118/";

#Acquire::http::proxy "http://usr2:pwd2@proxy2:port/";
#Acquire::https::proxy "https:///usr2:pwd2@proxy2:port/";
#Acquire::ftp::proxy "ftp:///usr2:pwd2@proxy2:port/";

#Acquire::http::proxy "http://usr3:pwd3@proxy3:port/";
#Acquire::https::proxy "https://usr3:pwd3@proxy3:port/";
#Acquire::ftp::proxy "ftp://usr3:pwd3@proxy3:port/";


i use one of them at a time....so, i have to comment out other each time i need to change proxy config....

Am i clear enough now??????

---

### Post by v3ct0r on 2011-04-27
BUMP!!!!
Anyone?????????????????????

---

### Post by Vaphell on 2011-04-27
Irritation is strong with this one...

chill out :) i'll try to concoct some script

---

### Post by Vaphell on 2011-04-27
not particularly pretty nor efficient
```
#!/bin/bash

cfg='./proxy_test.txt'
list=( $( grep 'http::proxy' "$cfg" | sed -r 's|^.*"http://(.*)/".*$|\1|g' ) )

for (( i=0; i<${#list[@]}; i++ ))
do
  echo $(( i+1 ))')' ${list[i]}
done

echo "Choose proxy:"
read n
(( n-- ))
echo Current proxy: ${list[n]}

for (( i=0; i<${#list[@]}; i++ ))
do
  if [ $n -eq $i ]
  then
    sed -ri '/'${list[i]}'/s|^[#]?||' "$cfg"
  else
    sed -ri '/'${list[i]}'/s|^[#]?|#|' "$cfg"
  fi
done

```

back up your current file, set proper path to your apt.conf at the beginning (cfg variable), test if the script does what it's supposed to do.
Most likely you need to run it with sudo

---

