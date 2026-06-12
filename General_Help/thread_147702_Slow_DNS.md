---
title: "Slow DNS"
date: 2006-03-20
forum: General Help
---

### Post by IYY on 2006-03-20
I am not sure if this is a problem with Ubuntu, but I'll ask anyway. My DNS seems to be very slow. Whenever I go to a website it takes a couple of seconds to solve the domain name, and then the page loads instantly. 

If I try to ping [www.google.com](www.google.com), it takes a couple of seconds to start, but then pings it very fast. If I ping Google's IP address, the result is instant.

Anybody knows how to make this work faster? Maybe some sort of cache to associate IP's with names?

---

### Post by dbw on 2006-03-21
have you disabled ipv6 yet?

---

### Post by frodon on 2006-03-21
You should try that : [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

---

### Post by IYY on 2006-03-21
I tried that, but I don't think it worked. 

**ip a | grep inet6** still gives me an output.

---

### Post by Bradl3yJ on 2006-03-21
All 3 of these lines are present in your aliases file? and the original ipv6 line is commented out?

> alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

Worked for me, be sure to reboot.

---

### Post by IYY on 2006-03-21
Yes, I added all of those lines and rebooted.

By the way, I didn't realize I posted in the wrong forum. I'm using Dapper. This could be the problem, since my other machine running Breezy doesn't have any problems.

---

