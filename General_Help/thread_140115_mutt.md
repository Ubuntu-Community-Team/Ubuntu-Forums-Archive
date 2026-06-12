---
title: "mutt"
date: 2006-03-05
forum: General Help
---

### Post by jsmidt on 2006-03-05
how do I get mutt to recieve the mail I get from gmail?  Ie.. how do I get it to retrieve mail from smtp.gmail.com?

---

### Post by skymt on 2006-03-05
SMTP is for outgoing mail. Gmail's incoming mail server is pop.gmail.com. Mutt, being a minimalist MUA, doesn't have a POP client built in. Instead, you have to use one like [getmail](http://pyropus.ca/software/getmail/) or [fetchmail](http://freshmeat.net/projects/fetchmail/). fetchmail is the classic, getmail is similar, but simpler to set up. I use getmail, since I don't need SMTP injection (I use getmail's procmail mode).

For information about how to set up getmail and mutt, see the getmail homepage and the [mutt wiki](http://wiki.mutt.org/).

---

### Post by andrew.46 on 2007-07-02
Hi,

 It is such a pity thath this is an old thread:

> **jsmidt said:**
> how do I get mutt to recieve the mail I get from gmail?  Ie.. how do I get it to retrieve mail from smtp.gmail.com?

because I have just published a page that deals with exactly that:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

                       Andrew

---

