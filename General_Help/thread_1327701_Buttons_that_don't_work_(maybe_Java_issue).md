---
title: "Buttons that don't work (maybe Java issue)"
date: 2009-11-15
forum: General Help
---

### Post by Eathray on 2009-11-15
I have some buttons that don't seem to function on my kid's school website. Just a few of them, but the rest work, and all buttons work in windows. I have some screen shots. The first shot is what the page looks like, and all the rest are the source code of the page, in case that helps anybody.

The broken button on the first page is the "Save" button. 

Thx.

Eathray

---

### Post by Eathray on 2009-11-15
Screenshots of source code for page continued:

Thx.

eathray

---

### Post by Eathray on 2009-11-15
And the last snapshot of the source code:

Thx.

Eathray

---

### Post by Pjotr123 on 2009-11-15
Try if installing Sun Java6 JRE helps:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

If it's not JRE related, but purely a matter of Javascript, you might try the fine alternative browsers epiphany-browser or Opera. Epiphany-browser is in the repositories, so easily installable. 

For Opera you need to download the installer from here:
[http://www.opera.com/download/](http://www.opera.com/download/)
Simply double-click the .deb file, just like you would a Windows installer.

---

### Post by Eathray on 2009-11-16
Thx, Pjotr123,

I know I have java6 16, and I know java6 17 is out. Do you think there's that big of a leap between update 16 and 17 that buttons won't work? The reason I ask is that the school site is far beneath 'cutting edge.' I had for example a heck of a time getting video to run properly on this site because they're using .asf crap.

Does the link you gave to the instructions include removing 6 16, or does that take place automatically? I have thought at times I might have a conflict...?

Thx.

Eathray

I ask a lot of questions first before I do anything. Fear of screwing stuff up :)

---

### Post by Pjotr123 on 2009-11-17
Upgrading from JRE 6 update 16 to JRE 6 update 17, most certainly won't fix your problem.... That's predominantly a security fix for you then. 

Most likely, the website you encounter problems with, has crappy code. Or you have an active Firefox add-on that blocks Javascript, like NoScript (solution: turn it off).

Anyway, it's most certainly worthwhile to try the two alternative browsers that I mentioned to you in my previous message.

If you want to upgrade your JRE to update 17 (which would be wise, considering the amount of security fixes), you have to remove JRE update 16 first. Using Synaptic Package Manager.

---

### Post by Eathray on 2009-11-17
I'm kind-of stuck with Firefox because it's one of only two browsers my kid's school site will accept (you guessed it, the other is IE), so I have firefox with their 'user agent switcher.' I guess I could check out Epiphany to see if it has a user agent switcher as well (I try to stick with the stuff in the synoptic package manager... the rest of cyber-world scares me:)).

I'm not sure I have 'NoScript' but I do have a flash blocker for those idiotic animated ads, so maybe that's a problem with this site. I'll play with that and get back to you.

Thanks for your help.

Eathray

---

### Post by Eathray on 2009-11-17
Alrighty then, now I'm making progress.

I started disabling and re-enabling plug-ins just to test these buttons, and the culprit is...

'user agent switcher.'

I have to use it to get into my kid's school site, but once I'm in, I seem to be able to turn it off and do anything I need to. My kid described it this way: "It's like the walls of a city. Once you get inside, you can go anywhere you want."

Thanks for the help. I wasn't even thinking plug-ins. I was thinking Java (although I guess it's still some kind of Javascript issue, isn't it?).

I will let the plug-in people know about the problem, and I will report back here so other people with the same issue can have a solution.

Thanks Pjotr123,

Eathray

---

### Post by Eathray on 2009-11-17
I posted the bug at the developer's site, and the solution I found, which is, setting the user agent switcher to IE7 for signing in, then once in the site just switching back to default. I don't know if that will work for everybody's issues, but it works for using Linux in Connections Academy, for any other fellow C.A. parents out there.

Thanks again to Pjotr123.

Eathray

---

