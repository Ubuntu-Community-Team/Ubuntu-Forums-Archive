---
title: "Samsun Mobile Broadband not connecting"
date: 2010-10-16
forum: General Help
---

### Post by Vishnu V on 2010-10-16
Hi
I have a Samsung C5212 mobile. I use it this as mobile broadband modem  in Ubuntu 10.04 without any problems. But in maverick I am not able to connect it to Internet.  I tried both bluetooth and data cable. Both fails

I googled about the problem and got command nmcli. But gives an error message
```

vishnu@vishnu-laptop:~$ nmcli con up uuid f99fc3b0-85fa-4bb5-8664-ff1e2f3e0d84 iface  /dev/ttyACM0 
Error: No suitable device found: device '/dev/ttyACM0' not compatible with connection 'AIRCEL'.

```
Results of nmcli con list and nmcli dev
```

vishnu@vishnu-laptop:~$ nmcli  con list
NAME                      UUID                                   TYPE              SCOPE    TIMESTAMP-REAL            
AIRCEL1                   1246d3f8-1b4e-44d2-9c5e-c25b64f0b04a   gsm               user     never                             
AIRCEL                    f99fc3b0-85fa-4bb5-8664-ff1e2f3e0d84   gsm               user     Wednesday 13 October 2010 07:29:19 AM IST
BSNL                      0719b16b-8d05-406a-83aa-35ab8e7a39c3   gsm               user     Saturday 16 October 2010 09:37:26 AM IST


vishnu@vishnu-laptop:~$ nmcli  dev
DEVICE     TYPE              STATE       
wlan0      802-11-wireless   disconnected
eth0       802-3-ethernet    connected   
ttyACM0    gsm               disconnected


```

This problem is only for SAMSUNG mobile. I tried Sony Ericsson K750i,Nokia 3110 which do not have any problem

Please help . Thanks

---

### Post by compgamer89 on 2010-11-23
I am having a similar issue that seems to be related.  Though connecting through the NM applet GUI does work initially, the connection will occasionally drop out resulting in an inability to connect until the computer is restarted.  Interestingly, even while the modem/computer are still in "compatible" state, nmcli reports the same error as above:

Error: No suitable device found: no device found for connection 'XXXX'.

and also

Error: No suitable device found: device 'ttyUSB0' not compatible with connection 'XXXX'.

when 'iface ttyUSB0' is included in the nmcli command.

For reference, the device I'm using is a Huawei USB stick, with lsusb reporting:
ID 12d1:1404 Huawei Technologies Co., Ltd.

I am using the most recent versions of network-manager and modemmanager, namely 0.8.1+git.20100810t184654.ab580f4-0ubuntu2  and 0.4+git.20100809t153145.be28089-0ubuntu1, respectively.

Any help would be appreciated, and commandline control of NetworkManager would be very useful in this case (since the system is functioning as a headless gateway for the network).

Thanks to all!

---

### Post by Vishnu V on 2010-12-17
I installed wvdial and i can connect to net using wvdial

---

### Post by Mohan91 on 2011-11-25
Hi, I'm using Ubuntu 10.04(GNOME). I'm using Samsung C5212 mobile to connect to web in Windows. But, I don't know how to connect the web in Ubuntu 10.04 through mobile, can anyone suggest me the steps.

---

### Post by Vishnu V on 2011-12-03
> **Mohan91 said:**
> Hi, I'm using Ubuntu 10.04(GNOME). I'm using Samsung C5212 mobile to connect to web in Windows. But, I don't know how to connect the web in Ubuntu 10.04 through mobile, can anyone suggest me the steps.

By using data cable
1. Connect your mobile to computer. System will detect the a new gsm modem is connected Select configure mobile broad band , if not go to system -> preferences -> network connection  under mobile broad band add new

select country provider and select APN

now you can connect to Internet from network connection.

This link may help you
[http://www.youtube.com/watch?v=MbbK1j5Kb_I]("http://www.youtube.com/watch?v=MbbK1j5Kb_I")

---

