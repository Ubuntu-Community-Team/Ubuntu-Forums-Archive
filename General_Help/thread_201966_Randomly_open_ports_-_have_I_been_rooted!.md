---
title: "Randomly open ports - have I been rooted?!"
date: 2006-06-22
forum: General Help
---

### Post by hornett on 2006-06-22
When I run NetworkTools port scan on localhost, I sometimes get randomly open ports.

Sometimes when I click scan I get nothing, a second later I get 4 or 5! (see screencaps!)

Anybody know what's going on? (AFAIK I have no services which should have open ports - process list attached)

---

### Post by lamego on 2006-06-22
You can use "sudo netstat -lp" to see which programs are listing on which ports.

---

### Post by hornett on 2006-06-22
Thanks, unfortunately netstat never shows any listening TCP ports ... so I'm none the wiser...

this is really odd!

---

### Post by bruce89 on 2006-06-22
Try [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) the "All Service Ports" scan, and see if the internet sees any.

---

### Post by mlind on 2006-06-22
how about simple nmap -A -v localhost ?
you could also install chkrootkit or rkhunter if you feel paranoid.

---

