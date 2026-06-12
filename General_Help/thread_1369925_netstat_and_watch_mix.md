---
title: "netstat and watch mix"
date: 2010-01-01
forum: General Help
---

### Post by akaikaze on 2010-01-01
Hi,

I have a small problem. I want to monitor network connections with watch and netstat commands. Just like this

```
watch 'netstat -naop'
```

Problem is that I can not figure out how to scroll through results of watch command.There are more sessions then there are lines in terminal that can be displayed on monitor. Any idea will be appreciated.

---

### Post by ajgreeny on 2010-01-01
It will not beblive, but you could send the output to a file 
```
watch 'netstat -naop' >watch.txt
```then open the txt file.  Depending on the output, it may or may not be a bit scrambled, however.

---

### Post by akaikaze on 2010-01-02
I am trying to create gnome terminal that will have tabs, which show differnt info. Like this

```
sudo gnome-terminal --maximize --tab -t TCPDUMP -e 'tcpdump' --tab -t
 NETSTAT -e 'watch "netstat -natvpo"' --tab -t OPEN.PORTS -e 'watch 
"netstat -napot | grep LIST"' --tab -t IFTOP -e 'iftop' --tab -t A.LOG -e 
'watch --differences "tail -n 100  /var/log/auth.log  |grep authentication 
"' --tab -t RAID -e 'watch "mdadm --detail /dev/md0"'  --tab -t ATOP -e 
'atop' 
```

If i want to monitor results in close to real time, i can use watch or while loop. Problem for me, with while, is that it appends results to terminal. Soon there is to much data, and if i add clear in while loop, it does not clear previous output, it just scrolls result.

---

