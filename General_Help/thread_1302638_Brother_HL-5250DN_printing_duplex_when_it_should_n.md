---
title: "Brother HL-5250DN printing duplex when it should not"
date: 2009-10-27
forum: General Help
---

### Post by wihiker on 2009-10-27
I have just finished a live upgrade to Ubuntu 9.10.

My Brother HL-5250DN printer is printing duplex when it is set to print single page.

I have deleted the printer, restarted the printer, reinstalled the printer and I get the same results.

This does not happen in OpenOffice but does in Acroread and Moneydance.

Any solutions?

---

### Post by wihiker on 2009-10-27
I have struggled with this for several hours now. 

I have deleted printer, restarted computer, reinstalled printer.
I have also reset both dsl modem and router just in case since this is a networked printer via the router.

There does not seem to be a problem with OpenOffice at this time but just about everything else, e.g, Firefox, Acroread, Xcross and others, still prints duplex even when I deselect those options.

Somewhere there is a conf file that is storing the wrong values, a file that perhaps was carried over from 9.04.

Any ideas where printer values are stored?  I have not been able to access CUPS.

---

### Post by cariboo on 2009-10-27
You can access the cups server by entering [http://localhost:631](http://localhost:631) in a web browser.

---

### Post by wihiker on 2009-10-27
CUPS asks for user name and ID.  I have tried root + PW, sudo + PW, my name + PW all to no avail.

I have reset printer to factory defaults and I still am having issues with it printing duplex.

---

### Post by wihiker on 2009-10-27
Resolved (at least for the moment)

I managed access to CUPS by entering user name + user PW.  Changed printer driver to Foomatic/postscript and all seems well.

Keeping my fingers crossed...

---

