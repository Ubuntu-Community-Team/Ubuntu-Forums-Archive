---
title: "script failing - colorization getting in way"
date: 2012-09-13
forum: General Help
---

### Post by nagileon on 2012-09-13
```

#!/bin/bash

for n in {1..1000}
do

for themachine in `rvc user:"password"@vsphereserver --path /vsphereserver/Development/computers/TheCluster/resourcePool/pools/PoolX/vms --cmd "exit"|awk '{print $2 $3}'`
do
a=`echo $themachine|grep poweredOn`
x=`echo $a|wc -m`
echo $x
done

if [ $x -gt 1 ]; then
echo "Not all of the machines are off at the moment! Waiting!"
else

for thevm in `rvc user:"password"@vsphereserver --path /vsphereserver/Development/computers/TheCluster/resourcePool/pools/PoolX/vms --cmd "exit"|awk '{print $2}'|tr -d ":"`
do
echo "Powering on: "$thevm

rvc user:"password"@vsphereserver --cmd "vm.on /vsphereserver/Development/computers/TheCluster/resourcePool/pools/PoolX/vms/$thevm" --cmd "exit"
done
break
fi

sleep 1

done

```

In the rvc vm.on part I'm getting "XY01.pool.local**\e[0m**" instead of "XY01.pool.local" and the vsphere complains (correctly) that there is no such machine.

The funny part is that the "echo "Powering on: "$thevm" part gives me the correct VM name. But then the malformed name is injected into the rvc command.
Warmest regards,
Peter

---

### Post by codemonkeyjohn on 2013-02-03
Peter,

You may want to try RVC's scripting functionality.  Put the following code in a file called turn_on_vms.rb and run this command: rvc -s turn_on_vms.rb user:"password"@vsphereserver

This way, you wouldn't have to deal with colorization at all.

Good luck,
John

```
path_to_vms = "/vsphereserver/Development/computers/TheCluster/resourcePool/pools/PoolX/vms"

rvc_exec "find --mark=on_vms #{path_to_vms} +on=true"

if _on_vms!.any?
  puts "Waiting for VMs to shut down"
  rvc_exec "vm.wait_for_shutdown --timeout=1000 --delay=1 ~on_vms"
end

puts "Powering on:"
rvc_exec "ls #{vm_path}"
rvc_exec "vm.on #{path_to_vms}/*"
```

---

