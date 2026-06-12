---
title: "How do I view a current process in the terminal?"
date: 2009-12-17
forum: General Help
---

### Post by marshmallow1304 on 2009-12-17
I (rather foolishly) started a kernel compilation on my server via ssh.  Now I want to shut down my ssh client, but then I will be unable to see the status of the operations.  Is there a way to see on the server itself what I can see in the ssh session?



Edit: Well, it's after 5 AM, so I will go to bed and leave two machines running instead of one.  I'd still like to know though.

---

### Post by wojox on 2009-12-17
By the time you wake back up, your ssh session will have expired.

---

### Post by Grenage on 2009-12-17
For future reference, screen or dtach are your friends.

---

### Post by kjohri on 2009-12-17
If you wish to have a process running even after logout, try,

nohup process &

---

### Post by marshmallow1304 on 2009-12-17
Thanks.  screen looks like just what I needed.

---

