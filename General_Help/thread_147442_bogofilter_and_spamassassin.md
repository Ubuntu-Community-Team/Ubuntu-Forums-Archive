---
title: "bogofilter and spamassassin"
date: 2006-03-20
forum: General Help
---

### Post by Belette on 2006-03-20
Hi !

I found this in the FAQ :

How can I use SpamAssassin to train Bogofilter?

If you have a working SpamAssassin installation (or care to create one), you can use its return codes to train bogofilter. The easiest way is to create a script for your MDA that runs SpamAssassin, tests the spam/non-spam return code, and runs bogofilter to register the message as spam (or non-spam). The sample procmail recipe below shows one way to do this:

    BOGOFILTER     = "/usr/bin/bogofilter"
    BOGOFILTER_DIR = "training"
    SPAMASSASSIN  = "/usr/bin/spamassassin"

    :0 HBc
    * ? $SPAMASSASSIN -e
    #spam yields non-zero
    #non-spam yields zero
    | $BOGOFILTER -n -d $BOGOFILTER_DIR
    #else (E)
    :0Ec
    | $BOGOFILTER -s -d $BOGOFILTER_DIR

    :0fw
    | $BOGOFILTER -p -e

    :0:
    * ^X-Bogosity:.Spam
    spam

    :0:
    * ^X-Bogosity:.Ham
    non-spam


but my problem is.. i have only postfix, not procmail.
is there a script somewhere on the internet i can use ?

thx

---

