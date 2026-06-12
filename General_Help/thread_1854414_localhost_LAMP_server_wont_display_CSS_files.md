---
title: "localhost LAMP server wont display CSS files"
date: 2011-10-04
forum: General Help
---

### Post by Swerve1000 on 2011-10-04
Hi,

I have installed php, mysql and apache and have it seemingly running fine. I can execute php scripts, create mysql databases and view html web pages, everything.

When I view .html and .php files, hosted on the local LAMP stack, non of the CSS markeup is rendered though. The css file is there, but when the server loads the page, the browser seems to not see it.

I have used both chrome and firefox, neither render the css.

The firebug browser extension shows the css code in the 'code view' window, but then reports "the element has no style rules".

I have tried both on page css markup and externally linked style sheets.

Can anyone think why this could be? Really stuck with this.

Thanks a lot.

---

### Post by lcman on 2011-10-04
> **Swerve1000 said:**
> Hi,

I have installed php, mysql and apache and have it seemingly running fine. I can execute php scripts, create mysql databases and view html web pages, everything.

When I view .html and .php files, hosted on the local LAMP stack, non of the CSS markeup is rendered though. The css file is there, but when the server loads the page, the browser seems to not see it.

I have used both chrome and firefox, neither render the css.

The firebug browser extension shows the css code in the 'code view' window, but then reports "the element has no style rules".

I have tried both on page css markup and externally linked style sheets.

Can anyone think why this could be? Really stuck with this.

Thanks a lot.

This is usually a simple permission problem. Mess around with chmod and chown a little bit and it shoudl get fixed. I usually do that myself.

---

