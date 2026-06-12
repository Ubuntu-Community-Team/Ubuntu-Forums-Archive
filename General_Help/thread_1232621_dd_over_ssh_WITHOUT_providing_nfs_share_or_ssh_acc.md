---
title: "dd over ssh WITHOUT providing nfs share or ssh account to server."
date: 2009-08-05
forum: General Help
---

### Post by r0g on 2009-08-05
Hi there,

I wonder if any of you ssh gurus can help an ssh n00b please?

I know I can ssh into a remote server to run dd and pipe the output back to an ssh enabled account or nfs share somewhere else BUT...

Is there a way I can run dd on the remote box without having to provide an ssh enabled account or nfs share which is visible to the rest of the network? i.e. can I use the connection I have already established by logging in to funnel the output of dd back to a file on my machine? I really do not want to run nfs or sshd on the client machine at all if possible.
 
Please don't simply suggest I do it the former way or ask me why I would even want to, I do want to and I have my reasons for not wanting to. I'd just like to know if the latter is possible and, if so, what the syntax would be please (and/or what other software I might need)

Many thanks for any help you can offer,

Roger.

---

### Post by r0g on 2009-08-05
Ah, the following seems to be working although I'll have to wait a while before I can mount the image to verify it...

ssh user@192.168.0.X 'dd if=/dev/sda1' > sda1.dump

Gotta love linux :D

---

