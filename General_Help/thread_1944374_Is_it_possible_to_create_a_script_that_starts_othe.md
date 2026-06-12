---
title: "Is it possible to create a script that starts other scripts?"
date: 2012-03-21
forum: General Help
---

### Post by Kivech on 2012-03-21
Hi all,

I was just wondering. I have two scripts (bash, if I am not mistaken) that perform all kinds of activities. 
For my own convenience, I would like to create one script that calls both of them subsequently. Is this possible?

My main concern is that since the script should activate two scripts, would it automatically wait for one script to finish before it starts the other, or would it just run one, run the other, with any disregard to what is going on on my system?

Any info would be great.

---

### Post by HiImTye on 2012-03-21
to start a terminal script inside of a terminal script just call it like you would anything else, i.e.
```
cd /path/to/file
./script.sh
```or simply
```
/path/to/script.sh
```using this method it will wait until the script is finished and then continue afterwards (with some exceptions, notably WINE commands, unless a second WINE command is after it, but that is not normally the case)
if you want for it to start one and then the other add an &, i.e.
```
cd /path/to/file
./script.sh &
./script2.sh &
./script3.sh
```alternatively, if you are calling the scripts manually and forget to add an & you can hit Ctrl+Z and then issue the bg command, i.e.
```
tye@T:~/Launchers$ ./ktorrent.sh
^Z
[1]+  Stopped                 ./ktorrent.sh
tye@T:~/Launchers$ bg
[1]+ ./ktorrent.sh &
tye@T:~/Launchers$ killall ktorrent.sh
[1]+  Terminated              ./ktorrent.sh
tye@T:~/Launchers$ 
```

---

