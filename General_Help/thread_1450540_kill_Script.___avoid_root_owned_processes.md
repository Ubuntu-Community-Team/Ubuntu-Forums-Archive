---
title: "kill Script.   avoid root owned processes ????"
date: 2010-04-09
forum: General Help
---

### Post by pczafer on 2010-04-09
Hi guys i wrote a script to kill processes by given name 

```
#!/bin/bash
ps -ef | grep $1 | awk ‘{print $2}’ | xargs kill
```


How can i add a IF state to this script to avoid root owned processes to be killed??????

---

### Post by cjhabs on 2010-04-09
> **pczafer said:**
> Hi guys i wrote a script to kill processes by given name 

```
#!/bin/bash
ps -ef | grep $1 | awk ‘{print $2}’ | xargs kill
```


How can i add a IF state to this script to avoid root owned processes to be killed??????

```

ps -ef | grep $1 | grep -v root | awk ‘{print $2}’ | xargs kill

```

---

### Post by pczafer on 2010-04-09
> **cjhabs said:**
> ```

ps -ef | grep $1 | grep -v root | awk ‘{print $2}’ | xargs kill

```

Thanks this works but i really wanted with if state because i want to echo some text like 

echo 'This is a root process! Normal users can not kill this process'


any help for this???

---

### Post by KeyserSoze93 on 2010-04-09
ps -ef | awk '$1!~/root/{print}' | grep $1 | awk '{print $2}'

---

### Post by blueridgedog on 2010-04-09
Why can the user that needs the script simply use the killall command?

```
killall processname
```

such as 

```
killall firefox
```

---

### Post by cjhabs on 2010-04-09
> **pczafer said:**
> Thanks this works but i really wanted with if state because i want to echo some text like 

echo 'This is a root process! Normal users can not kill this process'


any help for this???

You can use a construct like:
ps -ef | while read pid
do
echo $pid
pid=`echo $pid | awk '{print $2}'`
echo $pid
done

---

