---
title: "rsync script giving problems"
date: 2010-05-30
forum: General Help
---

### Post by Moyamo on 2010-05-30
I created a script to do a bunch of rsync commands to update and sync both ways but first verify if I want these actions to be done but it gives errors .
```
#!/bin/bash

####Functions

function syncronize_files
{

    echo "Do you want these actions to take place (y/n)"
    read answer
    
    case $answer in
    
        y|Y    )    rsync -avzu $2/ $1/
                rsync -avzu $1/ $2/
        ;;
    
        n|N    )     exit 0
    
        ;;
        *    ) $(syncronize_files)
    esac    
    
}


####Main

if [ -d "$1" ]; then
    if [ -d "$2" ]; then    
        rsync -avvznu "$2"/ "$1"/
        rsync -avvznu "$1"/ "$2"/
        $(syncronize_files)
    else 
        echo "The directory \"$2\" doesn'nt exist" >&2
        exit 1
    fi
else 
    echo "The directory \"$1\" doesn'nt exist" >&2
    exit 1
fi


```

When I run it it shows something like this

```
yaseen@yaseen-desktop:~/bin/bin$ sync.sh ~/HTML\ Files ~/Public
sending incremental file list
delta-transmission disabled for local transfer or --whole-file
./
total: matches=0  hash_hits=0  false_alarms=0 data=0

sent 46 bytes  received 15 bytes  122.00 bytes/sec
total size is 0  speedup is 0.00 (DRY RUN)
sending incremental file list
delta-transmission disabled for local transfer or --whole-file
./
how-to-hack-into-a-windows-xp-computer-without-changing-password.html
system_page.html
total: matches=0  hash_hits=0  false_alarms=0 data=0

sent 159 bytes  received 21 bytes  360.00 bytes/sec
total size is 443852  speedup is 2465.84 (DRY RUN)


```

if I enter y it says this

```
rsync: readlink_stat("/proc/871/task/871/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/871/task/871/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/871/task/871/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/8/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/8/task/8": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/8/task/8/attr": Operation not permitted (1)
rsync: opendir "/proc/871/task/871/fd" failed: Permission denied (13)
rsync: opendir "/proc/871/task/871/fdinfo" failed: Permission denied (13)
rsync: readlink_stat("/proc/875/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/875/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/875/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/8/task/8/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/8/task/8/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/attr": Operation not permitted (1)
rsync: opendir "/proc/875/fd" failed: Permission denied (13)
rsync: opendir "/proc/875/fdinfo" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/803/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/net/stat": Operation not permitted (1)
rsync: readlink_stat("/proc/875/task/875/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/875/task/875/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/875/task/875/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/803/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/task/803": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/task/803/attr": Operation not permitted (1)
rsync: opendir "/proc/875/task/875/fd" failed: Permission denied (13)
rsync: opendir "/proc/875/task/875/fdinfo" failed: Permission denied (13)
rsync: readlink_stat("/proc/880/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/880/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/880/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/803/task/803/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/803/task/803/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/attr": Operation not permitted (1)
rsync: opendir "/proc/880/fd" failed: Permission denied (13)
rsync: opendir "/proc/880/fdinfo" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/808/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/net/stat": Operation not permitted (1)
rsync: readlink_stat("/proc/880/task/880/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/880/task/880/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/880/task/880/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/808/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/task/808": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/task/808/attr": Operation not permitted (1)
rsync: opendir "/proc/880/task/880/fd" failed: Permission denied (13)
rsync: opendir "/proc/880/task/880/fdinfo" failed: Permission denied (13)
rsync: readlink_stat("/proc/886/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/886/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/886/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/808/task/808/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/task/808/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/task/872": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/task/872/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/task/872/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/808/task/872/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852": Operation not permitted (1)
rsync: opendir "/proc/886/fd" failed: Permission denied (13)
rsync: opendir "/proc/886/fdinfo" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/852/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/net": Operation not permitted (1)
rsync: readlink_stat("/proc/886/task/886/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/886/task/886/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/886/task/886/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/852/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/net/stat": Operation not permitted (1)
rsync: opendir "/proc/886/task/886/fd" failed: Permission denied (13)
rsync: opendir "/proc/886/task/886/fdinfo" failed: Permission denied (13)
rsync: readlink_stat("/proc/887/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/887/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/887/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/852/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/task/852": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/task/852/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/task/852/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/852/task/852/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858": Operation not permitted (1)
rsync: opendir "/proc/887/fd" failed: Permission denied (13)
rsync: opendir "/proc/887/fdinfo" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/858/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/net": Operation not permitted (1)
rsync: readlink_stat("/proc/887/task/887/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/887/task/887/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/887/task/887/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/858/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/net/stat": Operation not permitted (1)
rsync: opendir "/proc/887/task/887/fd" failed: Permission denied (13)
rsync: opendir "/proc/887/task/887/fdinfo" failed: Permission denied (13)
rsync: readlink_stat("/proc/9/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/9/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/9/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/858/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/task/858": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/task/858/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/task/858/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/858/task/858/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867": Operation not permitted (1)
rsync: opendir "/proc/9/fd" failed: Permission denied (13)
rsync: opendir "/proc/9/fdinfo" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/867/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/net": Operation not permitted (1)
rsync: readlink_stat("/proc/9/task/9/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/9/task/9/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/9/task/9/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/867/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/net/stat": Operation not permitted (1)
rsync: opendir "/proc/9/task/9/fd" failed: Permission denied (13)
rsync: opendir "/proc/9/task/9/fdinfo" failed: Permission denied (13)
rsync: readlink_stat("/proc/913/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/913/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/913/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/867/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/task/867": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/task/867/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/task/867/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/867/task/867/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870": Operation not permitted (1)
rsync: opendir "/proc/913/fd" failed: Permission denied (13)
rsync: opendir "/proc/913/fdinfo" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/870/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/net": Operation not permitted (1)
rsync: readlink_stat("/proc/913/task/913/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/913/task/913/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/913/task/913/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/870/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/net/stat": Operation not permitted (1)
rsync: opendir "/proc/913/task/913/fd" failed: Permission denied (13)
rsync: opendir "/proc/913/task/913/fdinfo" failed: Permission denied (13)
rsync: readlink_stat("/proc/924/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/924/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/924/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/870/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/task/870": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/task/870/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/task/870/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/870/task/870/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871": Operation not permitted (1)
rsync: opendir "/proc/924/fd" failed: Permission denied (13)
rsync: opendir "/proc/924/fdinfo" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/871/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/net": Operation not permitted (1)
rsync: readlink_stat("/proc/924/task/924/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/924/task/924/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/924/task/924/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/871/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/net/stat": Operation not permitted (1)
rsync: opendir "/proc/924/task/924/fd" failed: Permission denied (13)
rsync: opendir "/proc/924/task/924/fdinfo" failed: Permission denied (13)
rsync: readlink_stat("/proc/936/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/936/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/936/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/871/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/task/871": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/task/871/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/task/871/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/871/task/871/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875": Operation not permitted (1)
rsync: opendir "/proc/936/fd" failed: Permission denied (13)
rsync: opendir "/proc/936/fdinfo" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/875/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/net": Operation not permitted (1)
rsync: readlink_stat("/proc/936/task/936/cwd") failed: Permission denied (13)
rsync: readlink_stat("/proc/936/task/936/root") failed: Permission denied (13)
rsync: readlink_stat("/proc/936/task/936/exe") failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/875/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/net/stat": Operation not permitted (1)
rsync: opendir "/proc/936/task/936/fd" failed: Permission denied (13)
rsync: opendir "/proc/936/task/936/fdinfo" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/875/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/task/875": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/task/875/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/task/875/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/875/task/875/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/net/stat": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/task/880": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/task/880/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/task/880/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/880/task/880/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/net/stat": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/task/886": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/task/886/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/task/886/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/886/task/886/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/net/stat": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/task/887": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/task/887/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/task/887/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/887/task/887/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/net/stat": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/task/9": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/task/9/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/task/9/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/9/task/9/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/net/stat": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/task/913": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/task/913/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/task/913/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/913/task/913/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/net/stat": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/task/924": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/task/924/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/task/924/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/924/task/924/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/net/dev_snmp6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/net/ndiswrapper": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/net/ndiswrapper/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/net/stat": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/task": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/task/936": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/task/936/attr": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/task/936/fd": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/936/task/936/fdinfo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/ac_adapter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/battery": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/button": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/button/power": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/button/power/PWRB": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/button/power/PWRF": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/embedded_controller": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/fan": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/fan/FAN": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/power_resource": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/processor": Operation not permitted (1)
rsync: opendir "/proc/tty/driver" failed: Permission denied (13)
rsync: opendir "/root" failed: Permission denied (13)
rsync: failed to modify permissions on "/proc/acpi/processor/CPU0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/processor/CPU1": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/thermal_zone": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/acpi/thermal_zone/THRM": Operation not permitted (1)
rsync: failed to set times on "/proc/asound": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/card0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/card0/codec97#0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/card0/pcm0c": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/card0/pcm0c/sub0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/card0/pcm0p": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/card0/pcm0p/sub0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/card0/pcm1c": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/card0/pcm1c/sub0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/oss": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/asound/seq": Operation not permitted (1)
rsync: failed to set times on "/proc/bus": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/bus": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/bus/input": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/bus/pci": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/bus/pci/00": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/bus/pci/01": Operation not permitted (1)
rsync: failed to set times on "/proc/driver": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/driver": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/driver/pktcdvd": Operation not permitted (1)
rsync: failed to set times on "/proc/fs": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/fs": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/fs/ext4": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/fs/ext4/sda7": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/fs/jbd2": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/fs/jbd2/sda7-8": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/fs/nfsd": Operation not permitted (1)
rsync: failed to set times on "/proc/irq": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/1": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/1/i8042": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/10": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/11": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/12": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/12/i8042": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/13": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/14": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/14/pata_sis": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/15": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/15/pata_sis": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/17": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/17/ohci1394": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/18": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/18/SiS SI7012": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/19": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/19/eth0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/2": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/20": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/20/ohci_hcd:usb2": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/21": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/21/ohci_hcd:usb3": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/23": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/23/ehci_hcd:usb1": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/3": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/4": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/5": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/6/floppy": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/7": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/7/parport0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/8": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/8/rtc0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/9": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/irq/9/acpi": Operation not permitted (1)
rsync: failed to set times on "/proc/scsi": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/scsi": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/scsi/sg": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/scsi/usb-storage": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/crypto": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/debug": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/cdrom": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/hpet": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/mac_hid": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/parport": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/parport/default": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/parport/parport0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/parport/parport0/devices": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/parport/parport0/devices/lp": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/raid": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/dev/scsi": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/fs": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/fs/epoll": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/fs/inotify": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/fs/mqueue": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/fs/quota": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/keys": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/pty": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/random": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/sched_domain": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/sched_domain/cpu0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/sched_domain/cpu0/domain0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/sched_domain/cpu0/domain1": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/sched_domain/cpu1": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/sched_domain/cpu1/domain0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/sched_domain/cpu1/domain1": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/kernel/slow-work": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/core": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/conf": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/conf/all": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/conf/default": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/conf/eth0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/conf/lo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/conf/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/neigh": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/neigh/default": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/neigh/eth0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/neigh/lo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/neigh/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv4/route": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/conf": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/conf/all": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/conf/default": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/conf/eth0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/conf/lo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/conf/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/icmp": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/neigh": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/neigh/default": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/neigh/eth0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/neigh/lo": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/neigh/wlan0": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/ipv6/route": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/netfilter": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/netfilter/nf_log": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/token-ring": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/net/unix": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sys/vm": Operation not permitted (1)
rsync: failed to set times on "/proc/sysvipc": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/sysvipc": Operation not permitted (1)
rsync: failed to set times on "/proc/tty": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/tty": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/tty/driver": Operation not permitted (1)
rsync: failed to modify permissions on "/proc/tty/ldisc": Operation not permitted (1)

```

it goes on forever but i stopped it with ^C. If I enter n it outputs

```
/home/yaseen/bin/sync.sh: line 32: Do: command not found
/home/yaseen/bin/sync.sh: line 20: Do: command not found


```

if I just enter or type anything else it waits for more input and if I input y or n it does the above.

Please help me fix this 
thanks in advanced

---

### Post by Moyamo on 2010-06-07
nobody knows what's the problem?

---

### Post by CCoder on 2011-01-15
Moyamo,

The problem is caused by permission issues.

(e.g.: "rsync: failed to modify permissions on "/proc/803/task": Operation not permitted (1)")

So all you gotta do, is simply running the script with the needed permissions. Easiest way to do this is running the script with root.

Sudo su -> run script

Without wax,
CCoder.

---

### Post by Moyamo on 2011-01-16
Okay I'll try that thanks.

---

