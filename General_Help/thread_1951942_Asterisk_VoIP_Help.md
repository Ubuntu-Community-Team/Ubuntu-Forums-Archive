---
title: "Asterisk VoIP Help"
date: 2012-04-03
forum: General Help
---

### Post by grandpatech on 2012-04-03
Hello folks - yep - new to Ubuntu Forums - old Ubuntu user.  I didn't know where to post this question, so, here goes..

 We had an old non-Ubuntu  server running with Asterisk 1.4 - that blew up. We now installed Ubuntu 11.4 and Asterisk 1.6.2.9 and I copied the configs from our old server to the new asterisk.

 We got most everything back up and running  except the Meetme - Conferencing calling.

 When I try to enter a room, I get a quick disconnect on the phone and this on the CLI..

I x'd out the actual numbers but this is the output...

Parsing '/etc/asterisk/meetme.conf':   == Found
  == Spawn extension (internal, 78xxx, 1) exited non-zero on 'SIP/71xxx-00000016

I don't know what else to look for since I am not yet versed on Ubuntu/Asterisk. 

I would like to know if I am missing something in the configs I have shown here..
Meetme
conf => 78xxx,1234
conf => 78xxx,1234
conf => 78xxx,1234

Extensions
exten => 78xxx,1,meetme(1)
exten => _78xxx,1,SET(GLOBAL(MEETME_RECORDINGFILE)=/home/samba/record/${EXTEN}/conf-${EXTEN}-${STRFTIME(${EPOCH},,%Y-%m-%d_%H:%M:%S)})
exten => _78xxx,n,meetme(1,r)
exten => _78xxx,1,SET(GLOBAL(MEETME_RECORDINGFILE)=/home/samba/record/${EXTEN}/conf-${EXTEN}-${STRFTIME(${EPOCH},,%Y-%m-%d_%H:%M:%S)})
exten => _78xxx,n,meetme(2,r)
exten => _78xxxx,1,SET(GLOBAL(MEETME_RECORDINGFILE)=/home/samba/record/${EXTEN}/conf-${EXTEN}-${STRFTIME(${EPOCH},,%Y-%m-%d_%H:%M:%S)})
exten => _78xxx,n,meetme(3,r)

We had set a recording on the old setup which I don't care about for the purposes of getting the conf callls to work

If there is additional info needed, I will be happy to comply.

In the meantime, I hope I've given enough info to get some assist.

Thank you

---

