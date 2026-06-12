---
title: "Evolution link to web client"
date: 2010-03-22
forum: General Help
---

### Post by mynot on 2010-03-22
An odd problem:
I receive emails which have web links in them. When I click on the link, the GET part of the link is truncated.

Email is Evolution 2.28.1 (which I've re-installed).

Web client is Firefox 3.5.8, but problem also arises if I Use Seamonkey or Epiphany as the preferred client.

Problem doesn't occur on another machine using Seamonkey email and Firefox web.

Problem also doesn't occur with Win 2000 or Win 7.

Problem has only arisen since I've upgraded from 8.04 to 9.10.

The odd bit: the emails are regular postings from realestate.com. They have lots of links in them. The only links that give the problem are those which refer to the property listing. These links have very long GET data, but they are truncated to about 10 characters. Other links have more than 10 characters of GET data and they are ok.

So: problem occurs with particular links from a particular sender when I use Evolution as the mail client after upgrading to Ubuntu 9.10 but doesn't occur on this machine with a different o.s. or another machine with a different o.s.

Any takers?
Thanks
Tony

---

### Post by mynot on 2010-03-22
Another thing I've just discovered: If I use "Copy Link Location" to cut and paste the link, it works OK. So the problem isn't with the link itself.
Tony

---

### Post by mynot on 2010-03-27
I'll ask it another way:
Can anyone suggest any configuration, setting or other reason why urls like this in email messages:

[http://www.realestate.com.au/cgi-bin/rsearch?a=redirect&o=reaemailalert&to=http://www.realestate.com.au/cgi-bin/rsearch%3fa%3do%26id%3d106384019%26rsf%3demailalert-propdetails](http://www.realestate.com.au/cgi-bin/rsearch?a=redirect&o=reaemailalert&to=http://www.realestate.com.au/cgi-bin/rsearch%3fa%3do%26id%3d106384019%26rsf%3demailalert-propdetails)

would become this:

[http://www.realestate.com.au/cgi-bin/rsearch?a=o](http://www.realestate.com.au/cgi-bin/rsearch?a=o)

in Firefox, when the link is clicked in the email, in Evolution but not other email clients?
Thanks,
Tony

---

