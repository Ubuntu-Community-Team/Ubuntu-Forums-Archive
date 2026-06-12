---
title: "Hula clobbers sendmail bin"
date: 2006-05-24
forum: General Help
---

### Post by agillesp on 2006-05-24
Hello Everyone,

I thought there use to be a sub-forum specifically for server admin ... maybe the forums have changed around a bit.  Sorry if this is posted in the wrong place.

Anywho.  I recently moved from a Postfix mail server (nightmare) to Hula (breeze!).  Everything's working pretty well (although IMAP doesn't come up for some reason ... that's another topic though).  Eventually I came to realize I was no longer receiving emails from Horde or Cron.  This is obviously because the sendmail bin gets removed by apt-get.  I also cannot get it back since Hula and Sendmail are mutually exclusive in apt-get.

Does Hula have a drop-in replacement much like Exim is over Sendmail?

Thanks for any help.
-Abe

---

