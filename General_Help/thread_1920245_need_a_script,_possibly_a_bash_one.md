---
title: "need a script, possibly a bash one"
date: 2012-02-04
forum: General Help
---

### Post by eckeroo on 2012-02-04
How can you automate the following sequence of commands?:

1#   ps -e

2#   find pid for 'ac_client'

3#   kill pid

---

### Post by cortman on 2012-02-04
This should work.

```

#!/bin/sh

var=$(ps -ef | grep ac_client | awk '{ print $2 }')
kill -9 $var
```

---

### Post by Khayyam on 2012-02-04
cortman ..

grep will also return itself as a PID .. eg:

```
% ps -ef | grep string
username   751   590  0 19:04 pts/9    00:00:00 grep string
```

To make the string unique we enclose a char of string in a braket

```
#!/bin/sh

var=$(ps -ef | grep [a]c_client | awk '{ print $2 }')
kill -9 $var
```

---

### Post by Toz on 2012-02-04
How about making use of **pidof**?
```

kill -9 `pidof ac_client`
```

---

### Post by Khayyam on 2012-02-04
Toz ...

Yes, that would be more elegant. Basically with the above we aren't checking if 'ac_client' has more than one instance/PID, or for anything more than a match on the string (which in some instances could return more than we expect).

We could simplfy it further:

```
#!/bin/bash

killall -9 ac_client
``` 

BTW,  ` ` substitution is depreciated for $( )

```
kill -9 $(pidof ac_client)
```

best ...

---

