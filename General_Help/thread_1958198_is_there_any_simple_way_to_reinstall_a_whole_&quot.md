---
title: "is there any simple way to reinstall a whole &quot;LC_MESSAGES&quot; directory?"
date: 2012-04-13
forum: General Help
---

### Post by Fernando Negro on 2012-04-13
I have accidentaly deleted the "LC_MESSAGES" directory of my locale. :oops:

*(Im my particular case, the one located at "/usr/share/locale/pt_PT/". And I have, for the time being, copied the one located at "/usr/share/locale/pt/ as a substitute.)*

The only two solutions that I know of to restore everything back to how it was are: either to *reinstall the whole system* (which is, *very much unpractical* in my case, since this is a *multi-user* system; or to check, *one by one* - from what I see in other locale directories, such as the default "en_US" - which programs use files stored in the "/usr/share/locale/" directories and reinstall their respective packages.

But because my knowledge of GNU/Linux is very limited, I was wondering if someone who knows much more than I do knows of a better way to solve my problem...

---

### Post by Fernando Negro on 2012-04-17
(Answering my own question)

I guess not...

Having a separate /home partition is always a good idea, in case there's any problem with the operating system itself and we need to change it or reinstall it - which is the partition scheme I've always had, because of this. And I've just found out there's a simple way to reinstall it and keep each of the users' /home directory intact - [http://ubuntuforums.org/showthread.php?t=1308767](http://ubuntuforums.org/showthread.php?t=1308767).

Therefore, problem solved. A reinstallation is the better solution for me, although the reconfiguration will be a bit time consuming.

Stupid me, for not being careful in the operation I tried to do. I'll be very careful in the future, and will check what I'm doing, before I execute any delete command...

Any administrator/moderator of this forum can either mark this thread as "[SOLVED]" or delete it, in its entirety, since it is a pretty frivolous one...

(Sorry about this.)

---

