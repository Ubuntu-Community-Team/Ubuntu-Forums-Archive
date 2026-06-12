---
title: "Q about ssmtp"
date: 2011-12-04
forum: General Help
---

### Post by stleric on 2011-12-04
I'm trying out ssmtp, relaying mail through my gmail account, and I noticed an odd behavior.  When I send a message like so: ```
ssmtp <somebody>@<someplace>.com
Here's my message
^d
```  The message doesn't go through.  However, if I inlclude ```
To:  <somebody>@<someplace>.com
``` in the body of the message then it's cool.

Does the recipient in the command line serve any purpose?  What about sending the same message to multiple recipients?  Are the "From" and "Subject" lines of any significance?

TIA,
eric

---

