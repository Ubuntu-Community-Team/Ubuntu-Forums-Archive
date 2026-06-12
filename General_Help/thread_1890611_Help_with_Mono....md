---
title: "Help with Mono..."
date: 2011-12-03
forum: General Help
---

### Post by SuperSpyCE on 2011-12-03
I need help installing a older version of Mono, could anyone help me install the version 2.10?  I can't use the latest due to the fact that it does not have support for older .NET which I need..  I have just used a script to install 2.8 whcih would also work for me, but I watch it install but when I go to type "mono" in the terminal it tells me that it's not installed...  I'm completely lost and have been trying to fix this the entire day, and it's very frustrating.. D: Hope someone is able to help! :)

Thanks in advance!

---

### Post by directhex on 2011-12-04
> **SuperSpyCE said:**
> I need help installing a older version of Mono, could anyone help me install the version 2.10?  I can't use the latest due to the fact that it does not have support for older .NET which I need..  I have just used a script to install 2.8 whcih would also work for me, but I watch it install but when I go to type "mono" in the terminal it tells me that it's not installed...  I'm completely lost and have been trying to fix this the entire day, and it's very frustrating.. D: Hope someone is able to help! :)

Thanks in advance!
2.8 and above only support .NET 2.0 and 4.0 - you need 2.6.7 or below for .NET 1.1.

However, you can force 1.1 apps to run as 2.0 or 4.0 with a command line flag. What EXACTLY are you trying to achieve? If you really have a need to use an old release, use pre-Oneiric Ubuntu, or compile into /opt

---

