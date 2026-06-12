---
title: "https connection was refused"
date: 2009-07-24
forum: General Help
---

### Post by ExemplarUbuntu on 2009-07-24
We have had an https server on Apache2 running for over a year. A few weeks ago and then again today something odd happened.

We can access the https web page over the internal net 192.168 but when we try to access the page via our external static ip we see:

```
Failed to Connect
The connection was refused when attempting to contact
```

On the previous occasion the only thing that seemed to fix it was restarting the BTelecom adsl box but today that has made no difference. The ssl_access_log only shows internal net connections.

Other than the usual minor updates to Ibex I can't see what else could have changed unless BT has started blocking port 443.

---

### Post by ExemplarUbuntu on 2009-08-06
Anyone have any ideas ?

---

### Post by dcstar on 2009-08-07
> **ExemplarUbuntu said:**
> Anyone have any ideas ?

You don't give the URL so no one can test if they can connect to it.

Install the tcptraceroute package on a machine outside of your network and see what happens to packets addressed to port 443.

---

