---
title: "Script - Syntax error: end of file unexpected"
date: 2010-08-07
forum: General Help
---

### Post by .09. on 2010-08-07
Hi

I have Ubuntu Server 10.04 installed and can't seem to get this script working.

```
#!/bin/sh
if ps auxwww |grep -v grep |grep -c newcs.x86_64 >/dev/null
then
echo "NewCS... ok"
else
echo "NewCS... restarting"
/usr/local/bin/newcs.x86_64 -C /var/etc/newcs.xml &
fi
sleep 5
if ps auxwww |grep -v grep |grep -c CCcam.x86_64 >/dev/null
then
echo "CCcam... ok"
else
echo "CCcam... restarting"
/usr/local/bin/CCcam.x86_64 &
fi
```I get this error message: 

```
CCcamCheck.sh: 17: Syntax error: end of file unexpected (expecting "then")
```Any ideas what could be the problem?

---

