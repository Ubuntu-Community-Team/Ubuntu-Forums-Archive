---
title: "Google Buzz in Gwibber"
date: 2010-12-13
forum: General Help
---

### Post by OpenTangent on 2010-12-13
What happened to Google Buzz in Gwibber? It's been "supported" for ages now but it still doesn't work. It says authenticated but it neither receives nor sends anything for Google Buzz.

---

### Post by khish on 2010-12-14
Same thing here

---

### Post by joshuapurcell on 2010-12-14
Same thing here... I wish it would start working. I honestly can't say if it has ever worked but the reason why I'm now using this tool is to post easily to all social networking sites that I'm interested in... Google Buzz being one of them.

---

### Post by joshuapurcell on 2010-12-14
Think I found the bug report:
[https://bugs.edge.launchpad.net/gwibber/+bug/626023](https://bugs.edge.launchpad.net/gwibber/+bug/626023)

---

### Post by OpenTangent on 2010-12-14
It has never worked, it's the one feature that would make Gwibber useful to me.

---

### Post by khish on 2010-12-15
hey guys try this it work for me 
open this link in your browser 
[https://www.google.com/buzz/api/auth/OAuthAuthorizeToken?oauth_token=1%2FmMb9FwDmngHcuz4mqSBwlPRp3ArndpyO6HlTPSTiPcs&domain=anonymous&scope=https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fbuzz](https://www.google.com/buzz/api/auth/OAuthAuthorizeToken?oauth_token=1%2FmMb9FwDmngHcuz4mqSBwlPRp3ArndpyO6HlTPSTiPcs&domain=anonymous&scope=https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fbuzz)

then log in to your gmail account it will ask you if you wont to let anonymous users to see your buzzs, accept it 

then return your gwibber and refresh it you see the buzz 
and I try to post a new buzz it is work :D

---

### Post by OpenTangent on 2011-01-07
Is there an update on this or will Buzz remain an unrealised "feature"

---

### Post by dox_drum on 2011-02-07
ISSUE SOLVED.

[LIST=1]
[*]Add the ppa repository. sudo add-apt-repository ppa:gwibber-daily/ppa
[*]Update the repository list. sudo apt-get update
[*]Upgrade your system. sudo apt-get dist-upgrade
[*]install the buzz service. sudo apt-get install gwibber-servise-buzz
[*]Use the link from two post above this to grant access to Gwibber. (It works for me even when it said Token Invaled)
[/LIST]

THX all,

DOX

---

