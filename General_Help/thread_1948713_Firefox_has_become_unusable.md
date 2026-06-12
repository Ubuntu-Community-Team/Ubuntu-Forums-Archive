---
title: "Firefox has become unusable"
date: 2012-03-28
forum: General Help
---

### Post by punkybouy on 2012-03-28
I am running 10.04 LTS and sometime over the last few weeks Firefox has become unusable.  So far my only work around is to use Google Chrome.  Firefox no longer displays some pictures on websites, the bookmarks toolbar opens with the browser but is empty.  I have to manually go to view/toolbars and uncheck and then recheck to get it to display bookmarks.  If I go to tools/add-ons the page never loads.
I have tried uninstalling and re-installing but nothing has worked.  Google Chrome works just fine.  Thanks in advance for all the help.

---

### Post by troymius on 2012-03-28
What happens if you rename .mozilla folder to .mozilla_backup and restart firefox?

---

### Post by punkybouy on 2012-03-29
No change, same problem.

---

### Post by pqwoerituytrueiwoq on 2012-03-29
does it work if you download it from mozilla?
just extract it and run the firefox file in it

i think i am having the same problem

---

### Post by punkybouy on 2012-03-29
I upgraded to Firefox 12 from Mozilla and it appears to have fixed it.  From a terminal:

sudo add-apt-repository ppa:mozillateam/firefox-next

and then in the same terminal type:

sudo apt-get update && sudo apt-get install -y firefox

enter your password as needed.  If you are already in a root terminal you can eliminate sudo from the command.

When I restarted I was on FF 12 instead of 11.  Seems to be fixed.

Thank for the replies.

---

### Post by lovinglinux on 2012-03-31
> **punkybouy said:**
> I upgraded to Firefox 12 from Mozilla and it appears to have fixed it.  From a terminal:

sudo add-apt-repository ppa:mozillateam/firefox-next

and then in the same terminal type:

sudo apt-get update && sudo apt-get install -y firefox

enter your password as needed.  If you are already in a root terminal you can eliminate sudo from the command.

When I restarted I was on FF 12 instead of 11.  Seems to be fixed.

Thank for the replies.

Keep in mind that with *firefox-next* ppa you will continue to upgrade Firefox to beta versions only. Once Firefox 12 is released, you can go back to stable versions by disabling that ppa.

---

