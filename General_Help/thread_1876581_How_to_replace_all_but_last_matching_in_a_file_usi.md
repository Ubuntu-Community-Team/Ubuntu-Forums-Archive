---
title: "How to replace all but last matching in a file using bash"
date: 2011-11-06
forum: General Help
---

### Post by tanoloco on 2011-11-06
This is a question regarding linux in general, not only ubuntu,
I hope it's allowed posting questions regarding programming doubts.

Assuming using **bash**, having a configuration file like:

> 
param-a=aaaaaa
param-b=bbbbbb
**param-foo=first occurence <-- Replace**
param-c=cccccc
***# param-foo=first commented foo <-- Commented: don't replace***
param-d=dddddd
param-e=eeeeee
**param-foo=second occurence <-- Replace**
***param-foo=third occurence <-- Last active: don't replace***
param-x=xxxxxx1
param-f=ffffff
***# param-foo=second commented foo <-- Commented: don't replace***
param-x=xxxxxx2


In which you can find multiple commented or uncommented lines of the param-foo, how can you comment all the uncommented param-foos except the very last active one, resulting in:

> 
param-a=aaaaaa
param-b=bbbbbb
**# param-foo=first occurence <-- Replaced**
param-c=cccccc
***# param-foo=commented foo <-- Left***
param-d=dddddd
param-e=eeeeee
**# param-foo=second occurence <-- Replaced**
***param-foo=third occurence <-- Left***
param-x=xxxxxx1
param-f=ffffff
**# param-foo=second commented foo <-- Left**
param-x=xxxxxx2


Two questions:
1. How to do it with only one desired param?
(only param-foo in the example above) 

2. How to do it with all multiple active params at once? 
(param-foo + param-x in the example above)

I'm really puzzled :confused:
Thanks

---

### Post by hwttdz on 2011-11-06
```

#!/bin/bash
NUM_MATCHES=`grep -Ec "^param-foo|^param-x"`
let NUM_REPLACE=$NUM_MATCHES-1
for i in {1..$NUM_REPLACE}
do
  perl -0777 -pi -e 's/\nparam-(foo|x)/\n#param-\\$1/'
done

```

You'll have to iron out the escaping of stuff in the perl regex, but that's more or less the idea, at least of what you described, possibly not what you intended to describe.  Also I'm sort of bypassing the "bash" bit by making a command line call to perl.

---

### Post by tanoloco on 2011-11-07
Hi there :)

Thank you for your input ..
I cannot understand where to specify the input file in your script, maybe you meant:
```
NUM_MATCHES=`echo $input_file| grep -Ec "^param-foo|^param-x"`
```

:confused:

Anyhow I tried to lunch it with or without my interpretation and it hangs up.
I've got the perl interpreter anyhow.

However in the meanwhile I found a solution (not by myself!)
```
awk -F= 'NR == FNR {
  !/^#/ && _p[$1]++ && nr[$1] = NR
  next
  }    
$1 in nr && FNR != nr[$1] {
  FNR != nr[$1] && $0 = "# " $0 
  }1' infile infile
```

The infile has to be inserted twice!
I leave it here for future reference.

Thanks!

---

