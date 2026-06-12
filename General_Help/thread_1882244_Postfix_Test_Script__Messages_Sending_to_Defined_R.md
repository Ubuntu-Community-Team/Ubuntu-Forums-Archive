---
title: "Postfix Test Script :: Messages Sending to Defined Recipient and Email@hostname"
date: 2011-11-17
forum: General Help
---

### Post by own3mall on 2011-11-17
I'm running Ubuntu 10.04 on one of my servers and 11.10 on the other.  Both are using a relay host for sending outgoing email.  I'm using postfix to send email.  I'm using the below script to send a test message to my email address.

```

#!/bin/bash
    SUBJECT="Test Email"
    # Email To ?
    EMAIL="myemail@gmail.com"
    # Email text/message
    EMAILMESSAGE="Ubuntu server test email.  Do not respond.  This is a test."
    #echo "This is an email message test"> $EMAILMESSAGE
    #echo "This is email text" >>$EMAILMESSAGE
    # send an email using /bin/mail
    echo $EMAILMESSAGE | /usr/bin/mail -s $SUBJECT $EMAIL
    # echo "Hey testing 123" | /usr/bin/mail -s "Testing Subject" myemail@gmail.com

exit 1

```

When I run the script, it sends an email to Email@hostname and to the email address set in the EMAIL variable.   Why is it sending mail to Email@hostname ???? I don't see any part of the script that tells it to do that....

This works properly... the only recipient of a message is [email]myemail@gmail.com[/email]

```

echo "Hey testing 123" | /usr/bin/mail -s "Testing Subject" myemail@gmail.com

```

Appreciate any help.  Thanks

---

### Post by dcstar on 2011-11-17
> **own3mall said:**
> I'm running Ubuntu 10.04 on one of my servers and 11.10 on the other.  Both are using a relay host for sending outgoing email.  I'm using postfix to send email.  I'm using the below script to send a test message to my email address.

```

    SUBJECT="Test Email"
.........
    **echo $EMAILMESSAGE | /usr/bin/mail -s $SUBJECT $EMAIL**

```

Appreciate any help.  Thanks

Will expand to:

```
Ubuntu server test email.  Do not respond.  This is a test. | /usr/bin/mail -s **Testing Subject** myemail@gmail.com
```

No quotes after the -s. If you don't see quotes in the variable, there are no quotes there when it is used.

---

### Post by own3mall on 2011-11-18
Thanks.  I'll give it a shot.

---

