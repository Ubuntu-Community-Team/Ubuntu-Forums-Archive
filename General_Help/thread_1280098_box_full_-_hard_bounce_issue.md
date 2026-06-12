---
title: "box full - hard bounce issue"
date: 2009-10-01
forum: General Help
---

### Post by jspence on 2009-10-01
Hello,

I have some users that do not maintain there mailbox. It is always full. As a result I get a hard bounce from them all the time. They get deleted from the list and then I have to reinstate them. Is there a way to allow this 'bounce' to be ignored or reduced so that I don't have to maintain this issue?

Thanks.

---

### Post by zkriesse on 2009-10-01
What list are you referring to?

---

### Post by Giblet5 on 2009-10-01
Take a look at procmail. It's easy to configure/use.

You should be able to automatically delete these bounces based on crap in the email header like "[MAILER DAEMON]" etc.

---

