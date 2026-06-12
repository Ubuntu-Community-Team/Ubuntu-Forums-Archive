---
title: "LikewiseOpen/BeyondTrust 6.0 &amp; AD"
date: 2012-03-05
forum: General Help
---

### Post by frogotronic on 2012-03-05
Hello,

  I've downloaded and installed BeyondTrust (formerly LO) and gotten my machine joined to my AD (by an IT admin that has admin privileges for joining to an AD).

But...I don't see my drives?

According to this how to ( [http://www.beyondtrust.com/Technical-Support/Downloads/files/pbiso/Manuals/likewise-open-60-guide.html#quick-start](http://www.beyondtrust.com/Technical-Support/Downloads/files/pbiso/Manuals/likewise-open-60-guide.html#quick-start) )

I'm supposed to reboot and then "Leave the Domain" and then rejoin somehow????

I guess I don't quite understand AD and how BeyoundTrust should work.

I thought that once I was joined, my network drives would automagically appear in nautilus?  What am I missing?

Thanks,
CH   :popcorn:

---

### Post by jmcclintockBT on 2012-03-05
PBIS Open won't process a Windows logon script if that's what you were expecting, sorry about that.
 
Joshua

---

### Post by HiImTye on 2012-03-05
I found this [PDF]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cts=1330998066987&ved=0CE4QFjAC&url=http%3A%2F%2Fwww.beyondtrust.com%2FTechnical-Support%2FDownloads%2Ffiles%2Fpbise%2FManuals%2Fubuntu-active-directory.pdf&ei=E2tVT4CwH4KpiQLYk6W0Bg&usg=AFQjCNE5-vv3_Ho2USXqjKRYqCmoif0kWA") which might give you some ideas

---

### Post by frogotronic on 2012-03-05
Ok, so I'm joined...but "no drives"

What I mean to say is that when I login to the same network on a Windows 7 machine, all my network drives are automagically mapped in Windows Explorer.  When I am logged in via LikewiseOpen (BT), the drives *do not* appear in nautilus.

Is this what is supposed to happen?  Am I confusing AD with Single Sign-On for LDAP mapped drives?  If so, is there something else I need to do?

Thanks,
CH

---

