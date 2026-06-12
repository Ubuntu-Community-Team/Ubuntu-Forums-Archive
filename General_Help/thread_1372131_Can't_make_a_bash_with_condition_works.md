---
title: "Can't make a bash with condition works"
date: 2010-01-04
forum: General Help
---

### Post by lollo3011 on 2010-01-04
Hi there, I hope it's the right section.
So, i'm creating a script which tell me if i'm connected or not to the Internet, and if i'm connected it has to print my IP. The IP or "Disconected" will be displayed on Conky.
So, these are the scripts:

ip.sh
```
#!/bin/bash
wget http://checkip.dyndns.org/ -q -O - |
grep -Eo '\<[[:digit:]]{1,3}(\.[[:digit:]]{1,3}){3}\>'
```

And my own script:
```
#!/bin/bash
T1='/home/lollo3011/.scripts/ip.sh'
if [ "$T1" = "" ]; then
echo Disconnected
else
sh '/home/lollo3011/.scripts/ip.sh'
fi
```

So, If "ip.sh" prints nothing, print Disconnected, else run ip.sh and print my IP.
The problem is: Connected or not to the Internet, it always prints my IP. And if i'm not connected, it prints nothing; it never prints "Disconnected". 
Maybe it's why ```
if [ "$T1" = "" ]
``` Doesn't mean "if $T1 = Nothing"
Any help? I already tried to find it on google, but nothing came up :(

---

### Post by john newbuntu on 2010-01-04
There is a conky variable if_up (network) command that you could check to see if your interfaces are set up.  Would this suffice for your purpose?

If you actually want to run a script and check for connection, then the way you are doing in your script will have to change.  First of, you are assigning a value to T1, which means it will always be non blank.  Change this to something like:
T1=`<your entire wget command from ip.sh goes here>`
Note the use of back quote.  You could then use the -z option to check for blanks
if [ -z "$T1" ]; then
 ...
else
 ...
fi

---

### Post by lollo3011 on 2010-01-04
> **john newbuntu said:**
> There is a conky variable if_up (network) command that you could check to see if your interfaces are set up.  Would this suffice for your purpose?

If you actually want to run a script and check for connection, then the way you are doing in your script will have to change.  First of, you are assigning a value to T1, which means it will always be non blank.  Change this to something like:
T1=`<your entire wget command from ip.sh goes here>`
Note the use of back quote.  You could then use the -z option to check for blanks
if [ -z "$T1" ]; then
 ...
else
 ...
fi
I forgot to say that i already tried the {if_up} variable, but it doensn't work: it always prints that the network is up. If i'm connected on wlan0, and i write
${if_up wlan0}Connected${endif}
${if_up eth0}Connected${endif}
Il always prints: Connected, on both the networks :S

For the bash thing... Thanks! It works now :D
I had already tried [ -z "$T1" ] but i didn't put "`" instead of '
Again Thank you :)

---

### Post by mcduck on 2010-01-04
> **lollo3011 said:**
> 
Maybe it's why ```
if [ "$T1" = "" ]
``` Doesn't mean "if $T1 = Nothing"
Any help? I already tried to find it on google, but nothing came up :(

There's your problem. The "=" is used for setting values of variables, it's not a test operator.
```
if [ "$T1" -eq "" ]
```

But if you just want to check if the file exists, the correct way to do that would be this:
```
if [ -e "§T1" ]
```

edit: two links for you:
[Bash file test operators]("http://tldp.org/LDP/abs/html/fto.html")
[Bash comparision operators]("http://tldp.org/LDP/abs/html/comparison-ops.html")

---

