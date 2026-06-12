---
title: "Web Surfing - connectivity problem"
date: 2004-10-24
forum: General Help
---

### Post by theirish on 2004-10-24
Good day everyone!
Here's my problem:
I recently switched to ubuntu linux (from Fedora) and I think it's cool.
The problem appeared during web surfing... easy, some sites just do not open up.
I ran tcpdump and I found out that the request goes out smooth, but when the answer comes back, it contains no data (technically, the tcp window size is zero, **win 0** ).
Are there any known tcp stack issues?
Thanks

---

### Post by Mecallie on 2004-10-24
I have the exact same problem.
At first I thought it was a DNS problem, but entering the IP directly doesn't solve it either so that's not it.

Sometimes (very few) a page loads fine, but 99% it just takes ages. Downloading seems to work okay. Is something screwed up in the IP stack of Ubuntu?

---

