---
title: "Help with 'expect'"
date: 2012-07-08
forum: General Help
---

### Post by YIFY on 2012-07-08
hi guys I am in need for some 'expect' scripting help

I have the following bash script and need to make this automated using the same password everytime (since i am configuring different deviced everytime, I can not use SSH Key for this)

Can anyone tell me how to integrate the 'expect' usages into this script so that MySecrectPass will be used to log into the ssh and transfer the files and get mac address:

please find the bits I need automated below

```

login="user@192.168.1.99" 
ssh_args="-o StrictHostKeyChecking=no"  

#Get the mac address 
mac=$(echo "ip -o link show dev eth0  | sed 's/.*link\/ether \([0-9:a-f]*\).*/\1/g'" | ssh $ssh_args $login)

if [[ $mac == "" ]]; then 
      exit
fi

 echo "CPE mac address == $mac"

scp $ssh_args -r system.cfg $login:/tmp/  

scp $ssh_args cp ../XM* $login:/tmp/fw.bin


```

---

