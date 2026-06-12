---
title: "mrtg + snmp cpu load"
date: 2010-06-02
forum: General Help
---

### Post by 8Kuula on 2010-06-02
Im trying to get cpu load to mrtg, and im currently using this target line:
```
Target[cpu]: ssCpuRawUser.0&ssCpuRawUser.0:public@localhost + ssCpuRawSystem.0&ssCpuRawSystem.0:public@localhost + ssCpuRawNice.0&ssCpuRawNice.0:public@localhost
```

I would like to separate cpu nice value to mrtg output graph only, so it would be user+system in input graph and nice in output graph.
How to do that?

Some hours later googling give me picture that "ssCpuRawUser.0&ssCpuRawUser.0:public@localhost..." need to have always with input and output. So far as I know now there is no way to give that output graph 0 value.
Is there?


Other way would be to snmp oid that always gives counter zero value and replacing that to output user and system values, and input nice value, so mrtg would sum 0 values that way.
Which oid gives always counter zero value?


Or is there some other way to make that kind of graph?

---

