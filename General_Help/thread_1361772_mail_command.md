---
title: "mail command"
date: 2009-12-22
forum: General Help
---

### Post by Jenkins1 on 2009-12-22
I am trying to send my ip address as the subject of an email however I am not getting very far as I can't set the variable as the subject.

This is my attempt so far
```

set | wget -O - -q icanhazip.com
echo $1
mail -s "$1" <myemail>@googlemail.com </dev/null

```
All I get is a blank subject any thoughts?

Thanks in advanced.

---

### Post by kidders on 2009-12-23
Hi there,

Try this ...```
#!/bin/sh
ipaddress="`wget -O - -q icanhazip.com`"
mail -s "$ipaddress" <myemail>@googlemail.com </dev/null
```

Your current script may be confusing you into *thinking* it's working, because the "set" line would write your IP address to stdout (ie it's not the "echo" line that's doing it).

I hope that helps.

---

### Post by Jenkins1 on 2009-12-27
> **kidders said:**
> Hi there,

Try this ...```
#!/bin/sh
ipaddress="`wget -O - -q icanhazip.com`"
mail -s "$ipaddress" <myemail>@googlemail.com </dev/null
```

Your current script may be confusing you into *thinking* it's working, because the "set" line would write your IP address to stdout (ie it's not the "echo" line that's doing it).

I hope that helps.

Just what I needed thanks very much.

---

