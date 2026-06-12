---
title: "Copy configuration from one Server to another"
date: 2012-09-08
forum: General Help
---

### Post by ChouMaKen on 2012-09-08
Hello everyone,

First post here so take it easy on me :guitar:

I am totally new to Linux but not to computers at all.

Anyway I have 2 ubuntu VPS 128 RAM each, one is considerably faster than the other however (same connection speed)

[LIST]
[*]free -m on one shows a total of 128 RAM on the other 110.
[*]Top on the first (128 RAM) shows only a couple of running stuff on the second much more
[/LIST]


Is there a way to make them both an exact copy of each others ? I make copy the config of one to the second ?

thank you

---

### Post by SeijiSensei on 2012-09-08
Well they cannot be entirely identical as they need to have separate IP address and hostname configurations.  

Next there is the question of what you mean by identical.  As in each machine is constantly updated to match the other?  That's possible but it's tricky.

If I were you, I'd just get more memory from your VPS provider.  128 MB is pretty much the bare minimum these days to build a decent server.   I use [Linode]("http://www.linode.com/"), where a 512 MB machine costs just $20/month, and they have excellent support.

---

### Post by ChouMaKen on 2012-09-08
Thanks for the quick reply

Maybe I didn't express myself correctly, these are test VPS, I have them just for testing nothing will really run on them.

I guess what I am looking for is 
1) why one is faster than the other since both are 128 RAM
2) why one is showing 128 RAM total if free -m and the other 110
3) how can i get the same set of applications/packages things running on the first (fast) on to the second (slow)

both have been just reimaged and not touched

---

