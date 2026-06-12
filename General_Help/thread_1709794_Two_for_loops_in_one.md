---
title: "Two for loops in one?"
date: 2011-03-18
forum: General Help
---

### Post by SuaSwe on 2011-03-18
Hi all,

I've been searching high and low for a solution to my problem, and have not had much luck as to yet! 
 The situation is: I have two files containing bits of info that both need to be included in a single command, such as a for loop, but as separate elements. What I need to do is basically this:

```

ssh <servers in list a> ls -la | grep <items in list b>

```

Does anyone have any thoughts on how I might do this? Is it possible to do using bash scripting alone?

---

### Post by pqwoerituytrueiwoq on 2011-03-18
i can write it in php
[PHP]#!/usr/bin/php
$aServers=file("serversA.txt");
$bServers=file("serversB.txt");
if(count($aServers)==count($bServers)){
    for($i=0,$max2=count($aServers);$i<$max2;$i++){
        shell_exec('ssh "'.$aServers[$i].'" ls -la "'.$bServers[$i].'"');
    }
}
else{
    echo "list have a different number of servers\naborting";
}[/PHP]you will need php5-cli for it unless someone can convert it to a shell script
[PHP]#!/usr/bin/php
$aServers=file("serversA.txt");
$bServers=file("serversB.txt");
for($x=0,$max=count($aServers);$x<$max;$x++){
    for($i=0,$max=count($bServers);$i<$max;$i++){
        shell_exec('ssh "'.$aServers[$x].'" ls -la "'.$bServers[$i].'"');
    }
}
[/PHP]

---

### Post by SuaSwe on 2011-03-18
Much obliged for the help - unfortunately I don't have php nor can I install it on this system. :(

---

### Post by SuaSwe on 2011-03-19
Right, I haven't found a solution to the problem exactly, however I did conjure up a way to work around it, namely by inserting the servers in the script file itself, like so:

```

server~$ cat myscript.sh 
#/usr/bin/bash

for i in `cat item_list`; do
ssh server1 ls -la | grep $i >> myscript.out
ssh server2 ls -la | grep $i >> myscript.out
ssh server3 ls -la | grep $i >> myscript.out
ssh server1 ls -la | grep $i >> myscript.out
done
exit 
```

Not 100% ideal for my purposes what with losing the flexibility of being able to change/swap the server list without fiddling with the script itself, but at least it does what I need it to!

---

