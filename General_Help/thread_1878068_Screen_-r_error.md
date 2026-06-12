---
title: "Screen -r error"
date: 2011-11-09
forum: General Help
---

### Post by Slam Makanen on 2011-11-09
Hello,

I am having difficulty when ssh'd into a proprietary device my company builds.

I can create a new screen with screen -d -m -S <screenname> bash but when I try to attach to the screen I get an error -

Cannot find terminfo entry for 'unknown'

I have found other similar errors online but they all seem to reference colours and some other stuff I don't really understand. This problem only occurs from my new laptop (I use a mac at work). Strangely, my boss says that since upgrading his macbook to Lion he gets the same error.

We are both quite perplexed so please, any help would be very much appreciated.

Thanks,

Will.

---

### Post by Slam Makanen on 2011-11-14
Must be a difficult one if there is no reply after 4 days.

Does anyone have even the slightest idea as to where I should start looking? It's quite frustrating not being able to use the laptop properly because I can't do this one basic yet fundamental thing.

Any help at all is appreciated. Thanks.

---

### Post by Wayne_V on 2011-11-14
have you checked to make sure your TERM variable is set?  ("export TERM=vt100 ; tset"  for example)

from the screen man page:

> Before you begin to use screen you'll need to make sure you  have  cor&#8208;
       rectly  selected  your  terminal  type, just as you would for any other
       termcap/terminfo program.  (You can do this by using tset for example.)

---

### Post by Slam Makanen on 2011-11-14
Aaaah thanks so very much - that was exactly the problem! 

I've been thrown in the deep end with linux for work so trying to learn a lot on the fly. Thanks again for your help, you're a life saver!

---

