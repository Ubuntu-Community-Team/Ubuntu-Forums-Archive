---
title: "Problem with urllib in ubuntu 9.10"
date: 2009-12-07
forum: General Help
---

### Post by PriyaS on 2009-12-07
I have upgraded from 8.04 to 9.10.Now i am facing problem with the urllib in the following code 
gtrans.py

python gtrans.py hi en '&#2344;&#2350;&#2360;&#2381;&#2340;&#2375;'
```

#!/usr/bin/env python
# author: sublime@3euser.com
# License: GPL v3 or later
# usage: gtrans <from_lang> <to_lang> <text>

import sys
import urllib
import urllib2

import urlparse





def url_fix(s, charset='utf-8'):
    """Sometimes you get an URL by a user that just isn't a real
    URL because it contains unsafe characters like ' ' and so on.  This
    function can fix some of the problems in a similar way browsers
    handle data entered by the user:

 

    :param charset: The target charset for the URL if the url was
                    given as unicode string.
    """
    if isinstance(s, unicode):
        s = s.encode(charset, 'ignore')
    scheme, netloc, path, qs, anchor = urlparse.urlsplit(s)
    path = urllib.quote(path, '/%')
    qs = urllib.quote_plus(qs, ':&=')
    return urlparse.urlunsplit((scheme, netloc, path, qs, anchor))



#testurl ="http://translate.google.com/#"+sys.argv[2]+"|"+sys.argv[3]+"|"+sys.argv[1]


print sys.argv[1]
print sys.argv[2]
print sys.argv[3]


#testurl = 'http://translate.google.com/'+'#'+sys.argv[1]+"|"+sys.argv[2]+"|"+urllib.quote_plus(' '.join(sys.argv[3]))


testurl = 'http://translate.google.com/'+'#'+urllib.quote_plus(sys.argv[1]+"|"+sys.argv[2]+"|"+sys.argv[3])

url=url_fix(testurl)


print url

transtext =eval(urllib2.urlopen(urllib2.Request(url)).read().replace('null,', '"",'))
print transtext



```


Output :

```


hi
en
&#2344;&#2350;&#2360;&#2381;&#2340;&#2375;
http://translate.google.com/#hi%7Cen%7C%E0%A4%A8%E0%A4%AE%E0%A4%B8%E0%A5%8D%E0%A4%A4%E0%A5%87
(Copy paste the link in a browser we can sees the correct translated output hello whereas from the program its not working.Similar Code works fine with ubuntu 8.04 but its not working with 9.10)

Traceback (most recent call last):
  File "gtrans.py", line 77, in <module>
    transtext =eval(urllib2.urlopen(urllib2.Request(url)).read().replace('null,', '"",'))
TypeError: expected string without null bytes




```

Can any one please suggest a solution for this.Thank you

---

