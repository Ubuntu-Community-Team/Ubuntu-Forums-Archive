---
title: "Can't send mail in Kmail using Kubuntu, but can with Xubuntu"
date: 2009-11-12
forum: General Help
---

### Post by Guises on 2009-11-12
I'm using Kmail because it keeps me organized, and on my old machine, running Xubuntu, it worked fine. Got a new machine, installed openSUSE, and Kmail can receive messages fine, but can't send. It fails with a useless "Sending failed" error message. 

Fought with that for quite a while, then said "screw it, I'll just install Kubuntu." Did that, and now I'm getting the same error with Kubuntu. All of my Kmail settings are the same.

I though someone here might know - is there something different about Xubuntu? A more lax firewall or something? I'm completely lost on this because the errors aren't giving me anything to work with.

---

### Post by Guises on 2009-11-16
I'm going to bump this because it's really causing me some problems. Maybe no one knows the answer, but I've got to get this worked out somehow.

---

### Post by Giblet5 on 2009-11-16
You have misconfigured kmail. No, I don't care whether it was working before. It is misconfigured.

Check your outgoing smtp configuration, paying close attention to whether or not you must authenticate to the remote smtp server.

---

### Post by Guises on 2009-11-16
This was a curious solution: server authentication in the send tab is unchecked in Xubuntu and it works. Clicking "Check What Server Supports" in either Xubuntu or Kubuntu yields the same result - the server authentication box is unchecked and I get a "server does not support authentication" message. However, checking that box and selecting login as my authentication method fixed my problem. I can now send in Kubuntu.

Go figure.

---

