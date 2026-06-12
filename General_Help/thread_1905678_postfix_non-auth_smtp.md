---
title: "postfix non-auth smtp"
date: 2012-01-07
forum: General Help
---

### Post by igmox on 2012-01-07
Hi,

i am trying to setup a non-auth SMTP relay server. i am a newbie, so dont be harsh :)

i need a smtp relay server WITHOUT authentication on the lan side and that will send the mail by authenticating as a certain user on the mail server (port 587). 

i tried postfix and was able to send mail by ssh from it but i could not manage to configure to accept connections from the lan.
thunderbird says smtp connection timeout or smtp refusing connections.

any help appreciated,

thanks.

---

### Post by galvatron408 on 2012-01-07
you need to run the postconf command and set the "mynetworks" to whatever your network range is. So, for example, if my network was 10.110.0.0/16, then I would set "mynetworks=10.110.0.0/16".

When any clients in that subnet sends mail to postfix, they will not be denied.

run postconf by itself to see the settings. run postconf -e to edit the settings.

---

