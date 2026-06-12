---
title: "Striata reader"
date: 2012-09-23
forum: General Help
---

### Post by Ghost_Mazal on 2012-09-23
Lo all ,

I have a problem to get striata reader installed. When I tried to install it , it broke my system. Both package manager and software system is broken and can't install anything anymore. It looks like the problem is that striata is build for 32bit.

Does anybody know how to safely get striata reader installed on 64bit ? I need it for bank statements viewing.

Thanx

Ubuntu 64bit with all updates.

---

### Post by Wim Sturkenboom on 2012-09-23
Thank God I still have a Windows machine. My last attempt on 10.04 did not work (missing library or so) so I could easily give up.

If it's Standard Bank, it just gives a false feeling of security. Everybody can intercept the email, install the reader and read your statement; the post is more secure (at least if it arrives) :) No experience with the other banks that send encrypted statements.

---

### Post by jerrrys on 2012-09-23
Is this what you did?

[http://www.striata.com/community/customer-support/striata-reader-64-bit-deb.html](http://www.striata.com/community/customer-support/striata-reader-64-bit-deb.html)

Did [FONT=Arial]ia32-libs install without error?

Package manager is broke?  Which package manager are you using and what errors are you getting?
[/FONT]

---

### Post by Wim Sturkenboom on 2012-09-23
> **jerrrys said:**
> [http://www.striata.com/community/customer-support/striata-reader-64-bit-deb.html](http://www.striata.com/community/customer-support/striata-reader-64-bit-deb.html)

Thanks for that pointer; it now works for me in Ubuntu 12.04. One windows dependency less ;)

---

### Post by jerrrys on 2012-09-23
Congratulations :)

Solved then?

---

### Post by Wim Sturkenboom on 2012-09-24
Hey, I'm not the OP ;) For me it's solved.

OP has a more serious problem as his/her package management is broken.

---

### Post by Ghost_Mazal on 2012-09-24
I found a much safer way than that one suggested on site installing 32bit libs.

I installed the libc6 tarball. You have to run it in cli but it works 100% and is safer than
fiddling with 32bit libs on 64bit. That makes me just plain nervous and after having to
re-install once already not gonna fiddle with that again.

So my suggestion would be the libc6 tarball for others having this issue.

Credit for the solution goes to Johan from the ZA mailing list.

---

### Post by jerrrys on 2012-09-24
Congratulations :)

---

### Post by StriataSupport on 2012-09-25
Thanks for pointing out your issues with regards to the Striata Reader on 64-bit Ubuntu. We are in the process of testing a new build of the application that will resolve the issue mentioned.We will have a new version of the reader on our website ([http://www.striatareader.com]("http://www.striatareader.com")) for download in the next few days. We will post an update to this forum thread as soon as the new installer is available.

---

### Post by Ghost_Mazal on 2012-09-25
> **StriataSupport said:**
> Thanks for pointing out your issues with regards to the Striata Reader on 64-bit Ubuntu. We are in the process of testing a new build of the application that will resolve the issue mentioned.We will have a new version of the reader on our website ([http://www.striatareader.com](http://www.striatareader.com)) for download in the next few days. We will post an update to this forum thread as soon as the new installer is available.

Very glad to hear that something is being done about it.

Thank you for the info.

---

### Post by StriataSupport on 2012-10-04
The new 64-bit Ubuntu build has been uploaded onto our website and can be downloaded form the link below:
[http://www.striata.com/striata-reader/download.php?version=linux](http://www.striata.com/striata-reader/download.php?version=linux)

---

### Post by Ghost_Mazal on 2012-10-04
> **StriataSupport said:**
> The new 64-bit Ubuntu build has been uploaded onto our website and can be downloaded form the link below:
[http://www.striata.com/striata-reader/download.php?version=linux](http://www.striata.com/striata-reader/download.php?version=linux)

Thank you :p

---

