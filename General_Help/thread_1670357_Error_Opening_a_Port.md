---
title: "Error Opening a Port"
date: 2011-01-18
forum: General Help
---

### Post by pepe machine on 2011-01-18
Hello everyone, I'm trying to open ttyS0 serial port in java with the use of javax.comm api.
However i cannot continue because trying to open the port throws a RunTimeException

heres the exact error i've got
```
Exception in thread "main" java.lang.RuntimeException: 
[B]  Error opening "/dev/ttyS0"
  tcgetattr(): Input/output error[/B]
        at com.sun.comm.LinuxDriver.getCommPort(LinuxDriver.java:66)
        at javax.comm.CommPortIdentifier.open(CommPortIdentifier.java:369)
        at testjavaxcomm.PortOpener.main(PortOpener.java:36)
Java Result: 1
``` 
[B]
  Error opening "/dev/ttyS0"
  tcgetattr(): Input/output error[/B]

this is the error I am concerned about, is it an error with the permissions? I tried running my program in the terminal with a sudo but still the error is there. 

typing 
```
ls -l /dev/ttyS*
```

result in 
```
crw-rw---- 1 root dialout 4, 64 2011-01-19 06:09 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2011-01-19 06:09 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2011-01-19 06:09 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2011-01-19 06:09 /dev/ttyS3

```

and I am a member of a dialout group.

Im not really sure if those serial ports above are 'real' serial ports since.. This laptop Im using doesnt have one.. I have 3 USBs and 1 AVG.

I have a USB to Serial cable.. and typing

```
ls -l /dev/ttyUSB0
```

results in

```
crw-rw---- 1 root dialout 188, 0 2011-01-19 06:10 /dev/ttyUSB0

```

Please help me, I think Im missing something here. The java code I have is a pretty basic one.. And I dont think there is an error there. Im thinking that i dont have access to any serial port, please help me.

---

### Post by gustehn on 2011-02-01
bump!
need help with this one too!!

---

