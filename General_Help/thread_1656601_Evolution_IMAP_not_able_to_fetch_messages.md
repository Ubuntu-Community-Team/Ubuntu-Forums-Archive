---
title: "Evolution IMAP not able to fetch messages"
date: 2010-12-31
forum: General Help
---

### Post by majdi on 2010-12-31
Hi,

Using IMAP to retrieve emails in Evolution is not working correctly. Some messages are recieved, others are not. Those messages that cannot be recieved, reports the following error message: Unable to retrieve message

Running the following;

evolution 2.28.3-0ubuntu10
Ubuntu 10.04.1 LTS
2.6.32-26-generic

What is the recommended fix here?

---

### Post by dcstar on 2010-12-31
> **majdi said:**
> Hi,

Using IMAP to retrieve emails in Evolution is not working correctly. Some messages are received, others are not. Those messages that cannot be received, reports the following error message: Unable to retrieve message
.......

I use IMAP fine on the same setup, check your network connection and try and see if you can provide more details of the error message.

---

### Post by majdi on 2011-01-04
It is definitely not a network related issue as I have tested this on more than on connection with the same result.

The error shows up as follows;

Unable to retrieve message
Cannot get message with message ID : No such message available.

I can see this has been reported as a bug at the following link;

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/580300](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/580300)

Any idea on how to fix this?

---

### Post by majdi on 2011-01-06
I'm still having the same problem, should I install Evolution 2.30 to fix this or is there another fix for this?

---

### Post by HermanAB on 2011-01-06
Howdy,

It is likely funny characters in the message triggering a bug in Evolution. Try Thunderbird or Kmail - they will have different bugs...

---

