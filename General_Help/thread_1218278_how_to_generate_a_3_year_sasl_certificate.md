---
title: "how to generate a 3 year sasl certificate?"
date: 2009-07-20
forum: General Help
---

### Post by seezee on 2009-07-20
i'm brand new at setting up mail & i've never generated a cert in a linux system. i'm following the instructions at flurdy.com & i've reached the point where i'm supposed to do this:

cd /etc/postfix
openssl req -new -outform PEM \ 
	-out postfix.cert -newkey rsa:2048 -nodes 
	-keyout postfix.key -keyform PEM -days 999 -x509

where postfix.cert & postfix.key are variables (i think). i've tried typing it exactly as in the example, also replacing the 'variables', if that's what they are, with my own text, but i always get an error that [variable] is an unrecognized option.

anyone who knows how to do this, give me a shout, please!

thanks,

--cz

---

### Post by seezee on 2009-07-20
never mind -- apparently, i was supposed to run the command after the second line in the quoted text, fill in some fields, then repeat with the 1st & 3rd lines, skipping the 2nd. of course, if anyone wants to post on this to give the rest of us newbies some clarification as to the proper procedure, i'm sure it would be appreciated.

cheers,

--cz

---

