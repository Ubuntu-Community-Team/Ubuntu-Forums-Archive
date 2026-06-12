---
title: "Error: failed to connect to local store proxy.  Is it installed?"
date: 2010-06-03
forum: General Help
---

### Post by dragos2 on 2010-06-03
I am seting up a cloud with Ubuntu Enterprise Cloud from 10.04 and installed the controller with no nodes.
 
When I login into the controller on [https://controllerip:8443](https://controllerip:8443) and I click the 'Store' tab I get this error:
```

Error: failed to connect to local store proxy.  Is it installed?


```
 
What does that mean ?

---

### Post by thesheff17 on 2010-06-12
I'm also having this problem.  Did you ever fix it?

---

### Post by dragos2 on 2010-06-15
> **thesheff17 said:**
> I'm also having this problem.  Did you ever fix it?

Update on this:
The problem is when you click on the 'Store' tab, it says:
```

Error 35: gnutls_handshake() failed: A TLS packet with unexpected length was received.

```

and checking the logs it reports this:
```

cloud.output.log.1:17:42:53 DEBUG content | Wire.java:84 << "{"error-message": "Error 35: gnutls_handshake() failed: A TLS packet with unexpected length was received."}"

```

This is happening on a fresh 10.04 UEC Controller install. The installation went well, except Postfix needed some manual adjustments.

Maybe I should fill a bug.

---

