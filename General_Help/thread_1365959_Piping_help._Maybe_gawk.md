---
title: "Piping help. Maybe gawk?"
date: 2009-12-27
forum: General Help
---

### Post by ant2ne on 2009-12-27
this works and is cool
```
VBoxManage list vms | grep Name | grep -v UUID | cut -c 18-70
```



here is its output
```
Virtual-buntu
VBox_XPsp3
VBox_Ub9.10_Server_01
Ub9.10_32bit_Server_01
```



i'd like to pipe this output into something like the following
```
VBoxManage showvminfo (VBoxManage list vms | grep Name | grep -v UUID | cut -c 18-70) | grep State:
``` This would then return each VMs powered on state. But I don't know how to get it to work. I'm thinking gawk is what I need, but gawk is very complicated.

---

### Post by john newbuntu on 2009-12-28
Does back quoting help?  (The key generally to the left of '1' in your keyboard)
VBoxManage showvminfo (`VBoxManage list vms | grep Name | grep -v UUID | cut
-c 18-70`) | grep State:

---

### Post by falconindy on 2009-12-28
Or rather, put a $ in front of the ( ). To use backticks you'd need to lose the parenthesis.

Cancel that, I see what you're trying to do... Pipe the output to a while loop like so:

```
VBoxManage list vms | grep Name | grep -v UUID | cut -c 18-70 | while read vm; do
  echo -n ${vm}:
  VBoxManage showvminfo $vm | grep State: | cut -d\  -f2-
done
```

No guarentees this works off the bat as my VBoxManage output is different from yours, but hopefully this gets you going in the right direction.

---

### Post by ant2ne on 2009-12-28
There is no output with that script. I think it is because, i see a read vm but I don't see where you assign data to that variable.

---

