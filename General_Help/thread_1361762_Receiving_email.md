---
title: "Receiving email"
date: 2009-12-22
forum: General Help
---

### Post by gpetris on 2009-12-22
Hi everybody,

I would like to use my computer to get/send email. I installed sendmail, which takes care of outgoing email just fine, but apparently I cannot receive email. Which program/package should I install? Do I need to check/modify any configuration files?

Thank you in advance,
Giovanni

---

### Post by gpetris on 2009-12-22
Ok, I figured out that if I send email to myself locally, i.e., from the same computer, I do get it. So, I guess it is a matter of configuring some files appropriately. Does anybody have any idea of where I should look and what I should do?? 

Thanks in advance!

---

### Post by StuartN on 2009-12-22
> **gpetris said:**
> Does anybody have any idea of where I should look and what I should do??

I think you need to install exim or mutt to be able to manage external email from the command line. Then you need to set the appropriate parameters in the ~/.mutt/muttrc or ~/.exim/ configuration file with the name of your incoming and outgoing mail server (i.e. the ones you would use in Evolution or Thunderbird graphical email packages).

---

### Post by gpetris on 2009-12-22
Even if I plan to use something like emacs + mh-e? I would like to have my email forwarded from my company mail server to my desktop, so I can manage my email with my desktop, save messages locally etc.

Thanks

---

### Post by StuartN on 2009-12-22
> **gpetris said:**
> Even if I plan to use something like emacs + mh-e?

You probably need to set it in the MH configuration file then, and install MH.

---

