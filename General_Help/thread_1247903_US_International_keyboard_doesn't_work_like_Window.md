---
title: "US International keyboard doesn't work like Windows"
date: 2009-08-23
forum: General Help
---

### Post by Don_Nadie on 2009-08-23
***9.04 Wubi***

OK, so I suffered the long wait to get wubi downloaded at a speed much lower than my ISP provides me with, with my internet connection dropping out once at around the 98% downloaded point.

I'm a Linux noob who is curious about it. I've been using the US International keyboard layout in Windows for years as my only keyboard layout. That way, I can work in documents with more than 1 European language and not have to change _anything_.

I have tried to get the Ubuntu USA Alternative International, the USA International (AltGr dead keys) or USA International (with dead keys) to work and have had no success whatsoever. They all act _**exactly**_ like the USA keyboard.

There's a "_T_ype to test settings:" box in the Keyboard Preferences/Layout window, where it's easy to see that nothing works, even after I click on the "Apply System-Wide..." button. So if it doesn't work in this dialog box, it doesn't work, I've discovered.

What I haven't discovered is how to make it work. I've read several posts about my problem in this forum, but I haven't read what the magic trick is to get one of these other keyboard layouts to STOP acting exactly the way the USA keyboard layout does.

I don't need any flags or other fluff, I need to type** '** and see nothing, then type **a** and see the single character _accented a_ which I am now unable to type because I'm currently using wubi Ubuntu 9.04. I should have posted this from Windows, eh?

---

### Post by P4man on 2009-08-23
I dont really have your problem, as I got a french keyboard, but maybe this page helps:

[https://bugs.launchpad.net/ubuntu/+bug/231785](https://bugs.launchpad.net/ubuntu/+bug/231785)

sounds like only ç would be a "problem" (ie different combination as on windows). Dead keys apparently works otherwise ? Here is some more reading:

[http://ubuntuforums.org/showthread.php?t=408474](http://ubuntuforums.org/showthread.php?t=408474)

Still something that ought to be implemented IMHO. Especially for an OS that takes such pride in localization.

---

### Post by ceramicm on 2009-08-23
á é Hmm... Don't know if this is what you want, but this is the the method I use to insert accented characters:

1. Click System, Preferences, Keyboards. The Keyboard Preferences window will open.

2. Click the "Layouts" tab. Now, this part is kinda counter-intuitive: If you want to be able to insert non-USA characters, you don't have to change keyboard layout (in fact I use the USA layout exclusively). Instead, click the Layout Options button.

3. The Keyboard Layout Options window will open. Find an option called "Compose key position" and click it to expand it. Check "Right Alt", then click the Close button at the bottom of the Keyboard Layout Options window.

4. You should be back in the Keyboard Preferences window now. Click the Apply System-Wide button and input your password if you are prompted to do so.

You should be able to compose special characters now. Here's how it works: Let's say I wanted to write "ö". I would press and release <Alt> (the Compose Key we selected) then press <Shift>+<"> and release, and finally press <o>.

Another example (á): press/release <Alt>, press/release <'>, and finally press/release <a>.

Hope this was helpful!

---

### Post by DeMus on 2009-08-23
> **ceramicm said:**
> á é Hmm... Don't know if this is what you want, but this is the the method I use to insert accented characters:

1. Click System, Preferences, Keyboards. The Keyboard Preferences window will open.

2. Click the "Layouts" tab. Now, this part is kinda counter-intuitive: If you want to be able to insert non-USA characters, you don't have to change keyboard layout (in fact I use the USA layout exclusively). Instead, click the Layout Options button.

3. The Keyboard Layout Options window will open. Find an option called "Compose key position" and click it to expand it. Check "Right Alt", then click the Close button at the bottom of the Keyboard Layout Options window.

4. You should be back in the Keyboard Preferences window now. Click the Apply System-Wide button and input your password if you are prompted to do so.

You should be able to compose special characters now. Here's how it works: Let's say I wanted to write "ö". I would press and release <Alt> (the Compose Key we selected) then press <Shift>+<"> and release, and finally press <o>.

Another example (á): press/release <Alt>, press/release <'>, and finally press/release <a>.

Hope this was helpful!

It sure was. Thank you so much. I write a lot of e-mails in German and they use the ä, ö and ü characters a lot. Now I don't have to remember the unicodes anymore.
Thank you.
But how about the ß sign? Any ideas?

Edit: Got it: it's alt-right (Compose) with s s: that makes ß

---

