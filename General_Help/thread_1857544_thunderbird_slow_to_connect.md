---
title: "thunderbird slow to connect"
date: 2011-10-10
forum: General Help
---

### Post by Mickser_52 on 2011-10-10
I have finally upgraded to Ubuntu 11.04 and getting used to the new setup. One problem which I now have is that Thunderbird email is taking up to 30 seconds to connect to the server. I may have had a similar problem before but cannot remember how I solved it. 

I found a post which said to disable ipv6 which sounded familiar and I edited sysctl.conf as the post recommended. This has made no difference and there is still a large delay connecting.

Any help would be appreciated.

---

### Post by TeoBigusGeekus on 2011-10-10
Have you tested it for some time?
Could your email server be busy at the moment?

---

### Post by Mickser_52 on 2011-10-10
Thanks for the reply. The problem is not with the server I can connect through Windows without any delay.

---

### Post by Mickser_52 on 2011-10-10
I have found the solution and everything is working normally again.

I clicked on advanced tab in Thunderbird preferences and then edit config. Set disableipv6 to true as with Firefox and thunderbird connects straight away. Now how do I set this thread to solved?

---

### Post by TeoBigusGeekus on 2011-10-10
I think it's in the thread tools.

PS: Good to know you've solved it.

---

### Post by Mickser_52 on 2011-10-10
Yes it is:)

Thanks again.

---

