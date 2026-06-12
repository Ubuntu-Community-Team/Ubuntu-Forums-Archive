---
title: "Can't connect to office jabber/xmpp server"
date: 2011-05-19
forum: General Help
---

### Post by decoherence on 2011-05-19
Hi everyone,

I'm not able to connect to my work's internal xmpp server. I've confirmed with co-workers that my settings are correct. They are able to connect but I am not.

In the debug window, I get a large number of messages, though none of them show up unless I set the logging level to 'debug'. Specifically nothing shows up if I set the log level to "error."

The last message I get is

on_connection_ready: got error: WOCKY_AUTH_ERROR_STREAM (#8): host-unknown: 

I tried a Google search on "WOCKY_AUTH_ERROR_STREAM" and got zero results. That's right: ZERO! I suddenly feel like I'm using a Mac! ;)

Again, my co-workers are able to connect (though I haven't spoken to any fellow ubuntu/empathy users as they are either on vacation or in the field with me and using their blackberry) but Spark (puke!) and IM+ work fine.

Anyway, I guess I'll try pidgin for now but if anyone has any suggestions for getting empathy to work, or if there is any other information I can provide, I'm all ears!

thanks,

---

### Post by decoherence on 2011-05-19
OK I figured it out thanks to Pidgin's slightly more helpful error messages. Login ID needed to be of the format <username>@<fqdn of xmpp server>. Spark and pidgin handle this somewhat differently with 'domain' fields. Marking as solved!

---

