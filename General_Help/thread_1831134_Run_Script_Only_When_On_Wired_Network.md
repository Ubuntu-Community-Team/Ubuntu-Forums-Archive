---
title: "Run Script Only When On Wired Network"
date: 2011-08-22
forum: General Help
---

### Post by Kissell on 2011-08-22
I have a script which runs periodically and copies some very large files from the server to my laptop.  

This works fine, except sometimes my laptop is not connected to the wired gigabit network.

I want to prevent the script from running while on the much slower wireless network.

Is there a conditional I can use in the bash script to test for wired connectivty?  something like if [ "$eth0" = "on" ];

---

### Post by LemursDontExist on 2011-08-23
If you know the gateway address (router address?) for your wired network, and your gateway returns pings you could try:

```
ping -c 1 $gateway_ip > /dev/null
if [ $? -eq 0 ]
then
    #wired network is up
    copy_large_files
fi
```

where $gateway_ip is the ip address of your wired gateway on the local network when you're connected.  At the least if your wired and wireless gateways are on different subnets this should work.

Another option would be to try to parse the output of ifconfig, but the ping approach seems simpler if you can work it.

---

### Post by Kissell on 2011-08-23
That will test if I have network connectivity, however, it doesn't let me test the difference between being wired or being wireless, assuming the wireless is the same network as with a home access point.

---

### Post by Idefix82 on 2011-08-23
Parsing the output of
```

ifconfig -s eth0

```
shouldn't be too hard either. Basically, too many zeros in a row means eth0 is not connected.

---

### Post by LemursDontExist on 2011-08-23
> **Kissell said:**
> That will test if I have network connectivity, however, it doesn't let me test the difference between being wired or being wireless, assuming the wireless is the same network as with a home access point.

Another idea is to use netstat

```
if $(netstat -r | grep -q eth0)
then
    # wired network should be up
    copy_large_files
fi
```

should work assuming eth0 is your wired network device - since your routing table shouldn't have any entries for a device that's down?  I'm actually a little sketchy on this, but it seems to work on my machine.

I'm sure there are a million ways to do this, and this is probably not the best, but I hope it gives you some ideas =).

---

### Post by Kissell on 2011-08-23
> **Idefix82 said:**
> Parsing the output of
```

ifconfig -s eth0

```
shouldn't be too hard either. Basically, too many zeros in a row means eth0 is not connected.

When I unplug my ethernet cable and test the command and plug it back in and retest; the number of zeros remains the same, but the flags change.  I tests two computers, and I always have a BMU flag when the cable is unplugged, and a BMRU when it is plugged in.  

This seems to work:
```


ETH0_TEST=`ifconfig -s eth0|grep BMRU`
if [ "$ETH0_TEST" != "" ]; then
  echo ETH0_TEST: "$ETH0_TEST"
  echo "Wired Interface eth0 is Up"
else
  echo ETH0_TEST: "$ETH0_TEST"
  echo "Wired Interface eth0 is Down"
fi


```

Thanks!

---

### Post by Idefix82 on 2011-08-23
Great! You are welcome :-)

---

