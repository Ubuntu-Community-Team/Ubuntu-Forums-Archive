---
title: "Excecuting a script from apache"
date: 2010-05-11
forum: General Help
---

### Post by kempy1000 on 2010-05-11
Hi,

I am trying to make it so when I load a webpage a script runs. I have done this successfully.

My problem is that mythshutdown will not find a vaild config.xml and I cant seam to find where to put it or where to spesify where config.xml is located.

I run ```
 http://192.168.2.5/cgi-bin/test.sh 
``` to excecute the script.

/usr/lib/cgi-bin/test.sh
```

#!/bin/bash

echo "Content-type: text/html"
echo ""

mythshutdown --lock >> /home/chris/temp/log.log

exit 0

```

/home/chris/temp/log.log
```

...............................................................................

No UPnP backends found

Would you like to configure the database connection now? [no]
[console is not interactive, using default 'no']
mythshutdown: Could not initialize myth context. Exiting.

```

I realise the danger in this but it is protected by a htaccess file with digest password and apache is only locally accessable.

---

