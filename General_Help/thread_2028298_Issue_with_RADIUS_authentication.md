---
title: "Issue with RADIUS authentication"
date: 2012-07-17
forum: General Help
---

### Post by ppv on 2012-07-17
Greetings Fellas,

Can anyone shed some light on how to go about this issue with Radius authentication.

- I already have the system setup with both Radius server and client running properly and communicating with each other.

- The issue is that authentication using Radius fails. It is so because for any password used when doing ssh to the system which is running Radius client, the Radius server receives the password as string "INCORRECT", and thus it fails authentication.

- It seems that "something" is already trying to authenticate before it goes to Radius, but fails and sets the password as string "INCORRECT"

Any pointers will be much appreciated.
Thanks.

P.S. This is not a Ubuntu based system. But probably the question pertains to general Linux.

---

### Post by ppv on 2012-07-18
Anyone?

It seems that the "something" in my previous post is sshd.
Does anyone know how can I get sshd to pass on the password it has received to the next authentication level (PAM in this case). Thanks.

---

### Post by ppv on 2012-07-26
bump.

---

