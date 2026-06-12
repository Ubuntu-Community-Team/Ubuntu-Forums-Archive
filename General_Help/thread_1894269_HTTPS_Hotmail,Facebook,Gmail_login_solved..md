---
title: "HTTPS Hotmail,Facebook,Gmail login solved."
date: 2011-12-12
forum: General Help
---

### Post by sozo on 2011-12-12
Hello everyone this is my first and hopefully a very helpful post.

I have struggled for over a year now trying to get Ubuntu to log into my Hotmail, Facebook, Ebay, Gmail accounts etc, through my web browser, while connecting via my wireless network. My connections to these were just freezing and would not be able to complete the connection,and so, not enabling them to log in, regardless of which browser i was using. This would continue until a time out error was shown.

Now after constant reading and searching i have found a permanent solution for me, all my accounts now log in in seconds, and no more time outs. I was reading on my 3UK mobile network support docs and noticed it mentioned about the possibility of the MTU settings being too high in my connection settings, and this causing possible connection problems. so i tried it and it has worked.

So onto what i did.

Apparently the default is set allot of the time too high in the network settings.

They recommended MTU settings starting at 1300 and then working your way lower until successful connection is achieved

So in Ubuntu (NOTE * my current Ubuntu is 11.10 but the same issue occured in all versions i installed) Where you have your network connections icon at the top right of the Ubuntu screen, click that then go down to edit connections.

Then select wireless connections. At the bottom is MTU. This was originally set to automatic. So i changed this setting to the first one recommended by my isp. MTU 1300

That is all i did. I saved this available for all users. rebooted the laptop. opened the browser ( default Ubuntu 11.10 Firefox) and hey presto, all is solved.

So it would seem that all this time nearly 1 1/2 yrs, ive been struggling with this, all i had to do was reduce the MTU to solve the issue.

Believe me i have tried everything ese, firewalls etc and nothing else solved the problem. Im not highly technical and do not fully understand the implications of why this has worked but it has. So here is my post to tell you of my solution to my issue.

Just start at 1300 and work your way down until you get your connection, also lowering the mtu seems to have made general browsing a smoother experience too, with pages loading a little faster.

ok so thats it. Have a go and see if it resolves your issue if your having the same problems i did.

My first post, and i hope its been a helpful one. i will no doubt post again if i have a positive contribution to make in the future.

Take care all.

Regards
Sozo

---

### Post by kubilay@xanadu on 2012-05-25
> **sozo said:**
> Hello everyone this is my first and hopefully a very helpful post.

I have struggled for over a year now trying to get Ubuntu to log into my Hotmail, Facebook, Ebay, Gmail accounts etc, through my web browser, while connecting via my wireless network. My connections to these were just freezing and would not be able to complete the connection,and so, not enabling them to log in, regardless of which browser i was using. This would continue until a time out error was shown.

Now after constant reading and searching i have found a permanent solution for me, all my accounts now log in in seconds, and no more time outs. I was reading on my 3UK mobile network support docs and noticed it mentioned about the possibility of the MTU settings being too high in my connection settings, and this causing possible connection problems. so i tried it and it has worked.

So onto what i did.

Apparently the default is set allot of the time too high in the network settings.

They recommended MTU settings starting at 1300 and then working your way lower until successful connection is achieved

So in Ubuntu (NOTE * my current Ubuntu is 11.10 but the same issue occured in all versions i installed) Where you have your network connections icon at the top right of the Ubuntu screen, click that then go down to edit connections.

Then select wireless connections. At the bottom is MTU. This was originally set to automatic. So i changed this setting to the first one recommended by my isp. MTU 1300

That is all i did. I saved this available for all users. rebooted the laptop. opened the browser ( default Ubuntu 11.10 Firefox) and hey presto, all is solved.

So it would seem that all this time nearly 1 1/2 yrs, ive been struggling with this, all i had to do was reduce the MTU to solve the issue.

Believe me i have tried everything ese, firewalls etc and nothing else solved the problem. Im not highly technical and do not fully understand the implications of why this has worked but it has. So here is my post to tell you of my solution to my issue.

Just start at 1300 and work your way down until you get your connection, also lowering the mtu seems to have made general browsing a smoother experience too, with pages loading a little faster.

ok so thats it. Have a go and see if it resolves your issue if your having the same problems i did.

My first post, and i hope its been a helpful one. i will no doubt post again if i have a positive contribution to make in the future.

Take care all.

Regards
Sozo
This is brilliant! Thanks for the tip! I had the same after upgrading into 12.04, suddenly I couldn't login to my gmail account, and I use it at work. This message saved me! Well done and many thanks!

---

