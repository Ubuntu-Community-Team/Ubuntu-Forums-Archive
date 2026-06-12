---
title: "Need help with bash script (logfile output)"
date: 2009-11-25
forum: General Help
---

### Post by xzased on 2009-11-25
Here is the script Im using. It is supposed to ls to different servers through ssh. Everything works but I dont know how to make the output of the script go to a file and rewrite or clear the file every time it runs. Thanks

```
#!/bin/sh
#



for HOSTS in  192.168.1.05 192.168.1.06 192.168.1.07
do
echo "Connecting to $HOSTS"
echo "Listing contents of ETC"
echo ""
ssh $HOSTS  '\ls /etc;\'
echo "Finished job on $HOSTS"
echo ""


done

```

---

### Post by sisco311 on 2009-11-25
```
#!/bin/sh
#

for HOSTS in  192.168.1.05 192.168.1.06 192.168.1.07
do
  echo "Connecting to $HOSTS"
  echo "Listing contents of ETC"
  echo ""
  ssh $HOSTS  '\ls /etc;\'
  echo "Finished job on $HOSTS"
  echo ""
done > /path/to/file
```

or if you want to display the output to stdout as well:
```
...
  echo "Finished job on $HOSTS"
  echo ""
done | tee /path/to/file
```

---

### Post by rapsodia on 2009-11-25
you can just do this:

per example to save the output of ls do this: # ls > text.txt 
everytime you run that it will rewrite it. so lets say your script is called hosts then you can do: # hosts > host.txt that will work from outside your script but to log from the script itself you can go: ssh $HOSTS  '\ls /etc;\' > hosts.txt 

let me know if that helped

---

### Post by xzased on 2009-11-25
Thanks guys, that really helped, its working now :popcorn:

---

