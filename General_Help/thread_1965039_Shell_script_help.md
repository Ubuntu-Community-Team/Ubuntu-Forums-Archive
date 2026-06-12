---
title: "Shell script help"
date: 2012-04-25
forum: General Help
---

### Post by Vishal Agarwal on 2012-04-25
Hi,
below is the data for DHCP lease. 

lease 192.168.28.162 {
  starts 3 2012/04/25 05:03:29;
  ends 3 2012/04/25 05:08:29;
  cltt 3 2012/04/25 05:03:29;
  binding state active;
  next binding state free;
  hardware ethernet 00:02:44:91:9a:d3;
  uid "\001\000\002D\221\232\323";
  client-hostname "sandip-roy";


I want to get some of fields from this data in the following format :

host sandip-roy { hardware ethernet 00:02:44:91:9a:d3; fixed-address 192.168.28.162; }

Any help will be appreciated.

---

### Post by sanderj on 2012-04-25
Here you go:

```
$ cat input.txt | awk ' /lease/ { ip = $2 } ; /hardware/ { mac = $3 } ; END { print "host sandip-roy { hardware ethernet " mac " fixed-address " ip "; }" }  '

host sandip-roy { hardware ethernet 00:02:44:91:9a:d3; fixed-address 192.168.28.162; }

$
```

---

### Post by Vishal Agarwal on 2012-04-25
Hi Sanderj,

The advised is near to solution. But The  host should also come from the data itself. and there are more then 100 blocks like this that all needed to be captured.

---

### Post by sanderj on 2012-04-25
> **Vishal Agarwal said:**
> Hi Sanderj,

The advised is near to solution. But The  host should also come from the data itself. and there are more then 100 blocks like this that all needed to be captured.

I'm very sorry for not doing your homework good enough.

---

### Post by Vishal Agarwal on 2012-04-25
Ohh great !

I am not familiar with awk and sed much and I was feeling that there could be some solution. And because of your help i got the complete command as below 

 awk ' /lease/ { ip = $2 } ;  /hardware/ { mac = $3 } ; /client-hostname/ { hname = $2 };  { print " host " hname "  { hardware ethernet " mac " fixed-address " ip "; }" }  ' /var/lib/dhcp3/dhcpd.leases

The only one more help I wanted from you is is there any way to add some conditional formatting  with awk, so that I can capture 

2012/04/25 ;

without  showing this in output.

Thanks for your help again.

---

### Post by codemaniac on 2012-04-25
```
awk ' /lease/ { ip = $2 } ;  /hardware/ { mac = $3 } ; /client-hostname/  { hname = $2 };  { print " host " hname "  { hardware ethernet " mac "  fixed-address " ip "; }" }  '
```

You are missing the END block in your awk snippet .For each line present in the input data file a line will be printed in your report  .Like below which is unwarrented .

> host  { hardware ethernet ; fixed-address
host  { hardware ethernet ; fixed-address
host  { hardware ethernet ; fixed-address
host  { hardware ethernet ; fixed-address
host  { hardware ethernet ; fixed-address
host  { hardware ethernet ; fixed-address
Use END block as suggested by sunderj .

---

### Post by Vishal Agarwal on 2012-04-25
Hi,

If I am adding END then I am getting only one last line. And after removing the END I am getting the completer output as required.

---

### Post by sanderj on 2012-04-25
> **Vishal Agarwal said:**
> Hi,

If I am adding END then I am getting only one last line. And after removing the END I am getting the completer output as required.

Really? Post it ... I think you get too many lines with the awk liner you posted above ...

---

### Post by Vishal Agarwal on 2012-04-25
Pl see below
>  host uttam;  { hardware ethernet 08:10:74:5a:d3:2b; fixed-address 192.168.28.153; }
 host uttam;  { hardware ethernet 08:10:74:5a:d3:2b; fixed-address 192.168.28.202; }
 host uttam;  { hardware ethernet 08:10:74:5a:d3:2b; fixed-address 192.168.28.208; }
 host uttam;  { hardware ethernet 08:10:74:5a:d4:4b; fixed-address 192.168.28.208; }
 host uttam;  { hardware ethernet d8:5d:4c:c7:a0:b6; fixed-address 192.168.28.202; }
 host zaman;  { hardware ethernet 94:0c:6d:ea:ba:8a; fixed-address 192.168.28.128; }
 host zaman;  { hardware ethernet 94:0c:6d:ea:ba:8a; fixed-address 192.168.28.132; }
 host zaman;  { hardware ethernet d8:5d:4c:c7:ad:90; fixed-address 192.168.28.128; }
sysadmin@mail:~$ fgrep "08:10:74:5a:d3:2b" /var/lib/dhcp3/dhcpd.leases
  hardware ethernet 08:10:74:5a:d3:2b;
  hardware ethernet 08:10:74:5a:d3:2b;
  hardware ethernet 08:10:74:5a:d3:2b;
  hardware ethernet 08:10:74:5a:d3:2b;
sysadmin@mail:~$
the same is repeated in same file 4 times

>  awk ' /lease/ { ip = $2 }  ; /hardware/ { mac = $3 } ; /client-hostname/ { hname = $2 };   { print " host " hname "  { hardware ethernet " mac " fixed-address " ip "; }" }  ' /var/lib/dhcp3/dhcpd.leases

---

### Post by codemaniac on 2012-04-25
There seems to be multiple data set segments in your input file .All you need is a datastructure to hold the muliple c-hosts , macs and IPs .
It would be helpful if you post the complete input file in code tags .

---

### Post by Vishal Agarwal on 2012-04-25
> **codemaniac said:**
> There seems to be multiple data set segments in your input file .All you need is a datastructure to hold the muliple c-hosts , macs and IPs .
It would be helpful if you post the complete input file in code tags .

That is true, there are multiple data segments in the input file.

---

