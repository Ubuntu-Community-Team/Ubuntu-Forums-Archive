---
title: "Problem with thunderbird, firefox and flash"
date: 2012-01-17
forum: General Help
---

### Post by one-up on 2012-01-17
Hi everyone,

I have a strange problem with Thunderbird, Firefox and the Adobe flash player. When I simply open Firefox and navigate to a page containing a flash player, say, a youtube video, everything works as it is supposed to.

However, when I click on a link in an email message in thunderbird that takes me to a page containing a flash player, it doesn't work! In the case of youtube the "video" is just a black box. Also when I then go to the youtube homepage and look up the video from there it still won't do it.

It seems that when Firefox is spawned by Thunderbird, flash player doesn't work in it.

Any ideas? Thanks in advance.

EDIT: I've already tried reinstalling the flash player using the software center, and as you might guess or I wouldn't be posting this, without any result.

---

### Post by KingYaba on 2012-01-17
Do you have more than one Firefox application installed on your system?

---

### Post by one-up on 2012-01-17
Thanks for your response.
No, I don't. At least not that I'm aware of.

"whereis firefox" puts out:
```
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/man/man1/firefox.1.gz
```

EDIT: And it also doesn't say that flash isn't installed or something, which it does when I remove it. It's loading something but... ??

---

### Post by guestolo on 2012-01-17
Do you have an addon in Thunderbird installed called Thunderbrowse?

What happens if you right click on the link in email and choose to Open in Browser?

---

### Post by one-up on 2012-01-18
No, I don't have that plugin installed. Using "Open Link In Browser" doesn't work either.
I also found an option in the menu's called "Restart with Add-ons disabled", no luck with that either.

---

### Post by aladoinsano on 2012-01-18
I have the exact same problem, it started just now, or more likely a few hours ago because then ubuntu did some updates, i guess something got messed up with Firefox then. I dont remember exactly what was updated though, the only thing i remember seeing in the update window was some ffshow update, among others.   the funny thing is that flash works fine on youtube, but not on many other places, like some newspapers im reading.  I also have disabled all addons to no avail. I guess we will see more of these complaints in the next few hours if it indeed was an ubuntu update that broke it.

---

### Post by one-up on 2012-01-18
> **aladoinsano said:**
> I have the exact same problem, it started just now, or more likely a few hours ago because then ubuntu did some updates, i guess something got messed up with Firefox then. I dont remember exactly what was updated though, the only thing i remember seeing in the update window was some **ffshow** update, among others.

Hey, I remember seeing that one flash by too.

---

### Post by aladoinsano on 2012-01-18
I was a bit trigger happy here it seems... I dont have the same problem, and it was not due to an ubuntu update.. It was Wikipedia's fault!

I forgot that I disabled Java Script earlier today to view wikipedia (they used a java script to block their site).

But I wish you good luck with your problem! :)

---

### Post by one-up on 2012-01-18
> I forgot that I disabled Java Script earlier today to view wikipedia (they used a java script to block their site).
LOL

> **aladoinsano said:**
> But I wish you good luck with your problem! :)

Thanks :)

---

### Post by guestolo on 2012-01-18
one-up
How many email accounts do you have set up in Tbird?
If more than one, does it happen in all accounts?

Edit>>you are using Thunderbird 8.0 correct?

---

### Post by one-up on 2012-01-18
> **guestolo said:**
> one-up
How many email accounts do you have set up in Tbird?
If more than one, does it happen in all accounts?

Edit>>you are using Thunderbird 8.0 correct?

I have only one account, which is a GMail account. I'm indeed using 8.0.

---

### Post by guestolo on 2012-01-18
This may not be your problem, can't remember where I read this
But take a look anyways

Gmail, since it's your only account in T.Bird, should be set to default
Just double check that it is
In T.Bird, open "View Settings for this account"
At the bottom of the new window, select the drop down arrow beside 
"Account Actions"

If "Set as Default" IS selectable, Select it then restart T.bird
If it's not selectable, then it already knows it's default
Any help?

---

### Post by one-up on 2012-01-18
Thanks. No, that option is grayed out.

---

### Post by guestolo on 2012-01-18
Strange one
If you right click a link in email and Copy link location
Close Thunderbird 
Open Firefox and paste link in Address bar 
Does it work?

You could try Thunderbrowse in Thunderbird and see if it works
In T.Bird click on TOOLS>>Addons>>Get Addons
Search for **ThunderBrowse 3.8**

---

### Post by one-up on 2012-01-20
> **guestolo said:**
> 
Strange one

Innit?

> **guestolo said:**
> 
If you right click a link in email and Copy link location
Close Thunderbird 
Open Firefox and paste link in Address bar 
Does it work?

Yes, than it does, as I said in my OP only when firefox is spawned by Thunderbird does the problem occur. Copying the link from thunderbird into an already open firefox window does work. Even clicking on a link in thunderbird that doesn't point to a page containing flash, but then navigating from a page that does from there makes the problem occur.

> **guestolo said:**
> 
You could try Thunderbrowse in Thunderbird and see if it works
In T.Bird click on TOOLS>>Addons>>Get Addons
Search for **ThunderBrowse 3.8**

Yes I'll have a look at that, but that isn't really a solution is it? Its not that this problem is so extremely annoying; I can view the flash using a workaround. It's the sheer strangeness of the problem that made me think it was worth posting :P

---

### Post by one-up on 2012-01-21
Any brilliant minds?

---

### Post by myoldhouse on 2012-01-23
I know your pain:(  Ubuntu 64 11.10, Firefox 9 and Thunderbird 8 and I have the same problem. I have multiple Thunderbird email accounts so I don't think that has anything to do with the issue. If I make Google Chrome the default browser, the problem doesn't occur - a Thunderbird 8 spawned Chrome browser window plays flash OK. Oh, one other thing, I am using the latest beta Flash 11.2 r202.

No cure yet, just commiseration ...

---

### Post by myoldhouse on 2012-01-23
Oh, I almost forgot, another work around seems to be to ALWAYS open a Firefox browser before you open Thunderbird. When Thunderbird 8 spawns a new tab in the open instance of Firefox 9, Flash seems to work OK.

---

### Post by peloy on 2012-01-24
I am also affected by this... Well, it's actually a bit worse: my own PC is not affected but my wife's PC is affected. They are both running 11.10. She had been complaining about this but I was checking on my PC and since it was working for me I didn't pay much attention. Until today when I sat down to see what was going on. I was able to figure out the workaround of pasting into Firefox the link received via email. This made Flash objects work, as one of the posters in this thread indicated.

I see a bunch of messages in .xsession-errors when trying to open a page by clicking on a link in a Thunderbird message. The messages are like these:

WARNING: FileDescriptorSet destroyed with unconsumed descriptors: file /build/buildd/firefox-9.0.1+build1/build-tree/mozilla/ipc/chromium/s
rc/chrome/common/file_descriptor_set_posix.cc, line 20

###!!! ABORT: [PPluginInstanceChild] abort()ing as a result: file /build/buildd/thunderbird-8.0+build1/build-tree/mozilla/mozilla/obj-i68
6-linux-gnu/mozilla/ipc/ipdl/PPluginInstanceChild.cpp, line 2367

I think these messages might be related to the problem but am not 100% sure.

---

### Post by one-up on 2012-01-26
> **peloy said:**
> I am also affected by this... Well, it's actually a bit worse: my own PC is not affected but my wife's PC is affected. They are both running 11.10. 

Perhaps the unaffected PC is x86?

I find this problem baffling... Whether firefox is spawned by thunderbird or whether you open it manually it's the same executable right? The same code oughta run?

---

### Post by peloy on 2012-01-26
> **one-up said:**
> Perhaps the unaffected PC is x86?

I find this problem baffling... Whether firefox is spawned by thunderbird or whether you open it manually it's the same executable right? The same code oughta run?

Actually, my own PC is also affected, and I figured out why I did not notice before: it turns out that when I was checking the problem that my wife was experiencing, I already had Firefox open, and it had been opened *before* clicking on an URL in an email message in Thunderbird. This is the workaround that others have mentioned in this thread.

To answer your questions -- both PCs are x86, and the Firefox binary is the same in both cases (manually run or spawned by Thunderbird).

Based on the .xsession-errors messages I mentioned, I suspect that Thunderbird is spawning Firefox a bit differently than the way it is spawned when Firefox is run manually. This difference causes the Flash plugin initialization to fail when Firefox is spawned by Thunderbird. But this is just conjecture on my part at this time.

---

### Post by peloy on 2012-01-26
Another data point: when Thunderbird spawns Firefox to open an URL, it shows like this in ps aux's output:

$ ps aux | grep firefox
peloy   5006  5.5  6.1 554864 215876 ?       Sl   10:54   1:01 /usr/lib/firefox-9.0.1/firefox [http://www.example.com/page-with-flash/](http://www.example.com/page-with-flash/)

that Firefox instance won't show Flash objects.

However, if I manually run Firefox like this:

$ firefox [http://www.example.com/page-with-flash/](http://www.example.com/page-with-flash/)

the Flash plugin initializes and everything works fine.

So, I think there is an issue with the way Thunderbird is spawning Firefox.

---

### Post by peloy on 2012-01-26
Thunderbird 9, now officially available in Ubuntu 11.10, seems to have fixed this issue -- today's package updates brought a Thunderbird upgrade from 8 to 9 and the issue seems to be gone.

---

### Post by one-up on 2012-01-30
I can confirm the update has indeed fixed the issue. Thanks developers! :)

---

### Post by myoldhouse on 2012-01-31
Same for me. Thunderbird 9 update seems to have fixed the 'flash not working' spawned Firefox issue.

---

### Post by cybergalvez on 2012-02-04
> **myoldhouse said:**
> Same for me. Thunderbird 9 update seems to have fixed the 'flash not working' spawned Firefox issue.

I amd still having this problem :( I have TB9 and FF10 all from the repos.  

Any more help with this?

---

