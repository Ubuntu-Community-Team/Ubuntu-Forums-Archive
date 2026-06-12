---
title: "LTSP users?"
date: 2010-07-15
forum: General Help
---

### Post by Trogan87 on 2010-07-15
Hello,

I have successfully installed LTSP server with 10.04 using the Alternate CD. I immediately connected the thin client using PXE and it boots into the Ubuntu login screen - so far so good.

Now, I have two users accounts which I created in the server. However, I cannot login to either of them from the thin client. Ubuntu acts like it is loading an account but immediately goes back into the login screen. 

Am I creating the accounts in the wrong place? Any solutions?

Thanks.

---

### Post by Trogan87 on 2010-07-15
Just some more info. 

My problem is as explained in [this thread]("http://ubuntuforums.org/showthread.php?t=795652") in the first post where the person says "After entering the user's id and password on the client I get "Verifying password, please wait".  After a few minutes the prompt for a user login id reappears."

Any ideas?

---

### Post by MikeUK on 2010-07-16
I had similar problem
I would get a login screen in a relatively high resolution for my thin client, I would login, this would then after a small delay take me to my background and stall, after a couple of seconds I&#8217;d be right back at the login screen
Checking the logs showed a problem with the X-org driver
I switched to the VESA driver, I got a lower resolution login screen but everything worked
I did some homework and it seemed that the Savage driver I needed was problematic in some cases, switching off DRI seems to be the solution.
Added a line to lts.conf to switch off DRI and I&#8217;m now back to full resolution without any problems

I&#8217;d suggest setting Xserver to VESA to see if it helps, then find out any quirks about your driver

---

### Post by Trogan87 on 2010-07-16
> **MikeUK said:**
> I had similar problem
I would get a login screen in a relatively high resolution for my thin client, I would login, this would then after a small delay take me to my background and stall, after a couple of seconds I’d be right back at the login screen
I think this is relevant. My [thin client]("http://www.netvoyager.co.uk/products/lx1010.html") was (and sometimes is) complaining that my monitor is "out of range" and to change the resolution. I did not change the resolution but the login screen did eventually show on the thin client. Once the login screen showed I could not login, although it seemed as if it would login but take me back to the login screen.

I just used my laptop as a thin client and guess what? I was able to login **without much problems**. So I think using a compatible monitor is important.

Now I say "without much problems" because I was receiving the following error when using my laptop as the thin client:

(process:310) GLib-WARNING **: getpwuid_r(): failed due to unknown user  id (0)

---

