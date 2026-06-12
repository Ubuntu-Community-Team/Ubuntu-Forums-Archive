---
title: "Finding user name of a remote computer"
date: 2011-05-18
forum: General Help
---

### Post by Linux_buddy on 2011-05-18
How can i find the username of a remote computer if the ip is given vice versa through terminal.

---

### Post by noah++ on 2011-05-18
I think you mean its *hostname*. To find a hostname from a known IP address, you perform a reverse DNS lookup. To do a reverse lookup on 91.189.94.156, for example:
> dig -x 91.189.94.156The server's response will follow. If successful, you'll see two lines of this form:
> 
;; ANSWER SECTION:
_ubuntu.com_.        600    IN    A    91.189.94.156I underlined the hostname.

---

