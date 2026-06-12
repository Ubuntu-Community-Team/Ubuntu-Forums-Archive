---
title: "Ubuntu 9.10 not prompting for password in any mail client"
date: 2010-04-05
forum: General Help
---

### Post by amnoaweegie on 2010-04-05
I'm new to Ubuntu being a recent convert from XP/Vista.  I'm having problems setting up an email client.  Tried both Evolution (which looks good) and Thunderbird but both of them will not prompt for my password when connecting to my mail servers.  I've quadruple checked my settings and everything looks OK however I do not get the password prompt.

Creating an account in Evolution is almost the same as that shown in the documentation but I do not get prompted for the time zone.  Checking where Evolution stores the passwords also comes up with different results on my computer as the location specified does exist but is empty.

Evolution is running at 2.28.1 and Thunderbird is 2.0.0.24

Thanks in advance for any help you can give me.

---

### Post by NT4usB on 2010-04-05
Have you used Thunderbird on your windows machines?
You can avoid a bunch of configging by copying your profile folder off the winbox and using it on the Linux box.
Rename the win profile folder whatever the profile folder is on the linbox (after renaming the original, of course) then fire up Thunderbird. 
Everything should be just like it was on the winbox.

Anything in the saved passwords? Remember to check the Passwords never saved tab.
Remove any that are there.
Now does it prompt?

Account settings, way at the bottom. SMTP settings. Edit and check is the Security and Authertication>Use name and password checked? Check it.
Anything?

I know nothing about evolution.

---

### Post by amnoaweegie on 2010-04-06
Thanks for the prompt reply.  I've got all the settings as you suggest already but no prompt for password.  I think the problem is with Ubuntu rather than either of the mail programs though, something not set right.

Will try copying over my Windows settings as you suggest but have no idea where to save it on Ubuntu as the file structure on my computer does not seem to reflect that shown in the documentation.  Does it go into $Home/<User>/.mozilla-thunderbird somewhere or am I barking up the wrong tree?

---

### Post by dcstar on 2010-04-06
> **amnoaweegie said:**
> I'm new to Ubuntu being a recent convert from XP/Vista.  I'm having problems setting up an email client.  Tried both Evolution (which looks good) and Thunderbird but both of them will not prompt for my password when connecting to my mail servers.  I've quadruple checked my settings and everything looks OK however I do not get the password prompt.
......

So **exactly** what happens when you use the Evolution "Send/Receive" function?

---

### Post by amnoaweegie on 2010-04-06
Thanks to you both for your suggestions :KS

Even though I hadn't installed any firewall software my computer was blocking both POP3 and SMTP traffic.  Installed Guarddog and problem now resolved.

---

### Post by NT4usB on 2010-04-07
> **amnoaweegie said:**
> ...Will try copying over my Windows settings as you suggest but have no idea where to save it on Ubuntu as the file structure on my computer does not seem to reflect that shown in the documentation.  Does it go into $Home/<User>/.mozilla-thunderbird somewhere or am I barking up the wrong tree?

That's exactly where it goes (if you already haven't figured it out.) There is a 'profiles' folder in there with your profile folder(s) in it.
Pretty sweet how the Thunderbird profile will work cross platform like that.

---

