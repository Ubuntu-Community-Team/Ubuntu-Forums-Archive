---
title: "Firefox:  Start Page can't be changed!"
date: 2006-01-27
forum: General Help
---

### Post by tnichols on 2006-01-27
This is an odd problem.  Maybe an easy fix, but I have only been using Linux for about 6 months now and can't figure this out.

Today, I logged onto my computer and opened Firefox, and my start page was set to [www.arizona.edu](www.arizona.edu) (University of Arizona).  I have no idea why.  I went into Preferences to set the start page back, and it is showing the right start page.  I tried changing this to [www.google.com](www.google.com) and saving it just to see if that was the problem, and when I started it up again...there was University of Arizona!

So does anyone know what this is all about?  This is reminiscent of Windows and the spyware/browser hijacks that convinced me to give Linux a try in the first place.  Could it be that my computer is infected with some extremely rare virus or something?  

Any help would be greatly appreciated.

-Tim

---

### Post by o_fortuna on 2006-01-27
[QUOTE=tnichols]This is an odd problem.  Maybe an easy fix, but I have only been using Linux for about 6 months now and can't figure this out.

Today, I logged onto my computer and opened Firefox, and my start page was set to [www.arizona.edu](www.arizona.edu) (University of Arizona).  I have no idea why.  I went into Preferences to set the start page back, and it is showing the right start page.  I tried changing this to [www.google.com](www.google.com) and saving it just to see if that was the problem, and when I started it up again...there was University of Arizona!

So does anyone know what this is all about?  This is reminiscent of Windows and the spyware/browser hijacks that convinced me to give Linux a try in the first place.  Could it be that my computer is infected with some extremely rare virus or something?  

Any help would be greatly appreciated.

-Tim[/QUOTE]
Hmm... I don't know what could be causing this. What extensions do you have? Try listing them here. Maybe one is acting up?

Also... have you tried changing the homepage, closing the preferences dialogue, and selecting "home" from the Go menu (ie, without shutting firefox down). It might be that firefox isn't saving the settings, though that seems odd.

By the way, are you using the version that comes with Ubuntu (1.0.7) or the new version (1.5)?

---

### Post by tnichols on 2006-01-27
I can click on the Home button anyway and it goes to the right start page.  It is only during startup of Firefox that it brings up the University of Arizona page.

I am using Firefox 1.0.7.

Excuse my newbie-ness, but how do I find out my extensions?  Is this the same as plugins?

---

### Post by tnichols on 2006-01-27
FYI- I did a Tools - Extensions and saw English Language Pack 1.0.1 listed.  That's it.

---

### Post by astoltz on 2006-01-27
I'm not positive this is the problem but try typing "about:config" in the address bar.  There is a filter box at the top - filter on "homepage".  My Firefox has three settings:

browser.startup.homepage
browser.startup.homepage_override.mstone
startup.homepage_override_url

Maybe one of those is screwed up?

---

### Post by cjm5229 on 2006-01-27
That's the right place for extensions. That would be the only extension you have installed. I had that problem withh FF1.07 once too, don't remember if I fixed it or not.
   Go to Ubuntu Forums>Customization Tips and Tricks, Right at the top of the forums is a sticky for Automatix. Go there follow the instructions to install Automatix, Then install FF1.5 and I don't think you will have any more problems.

---

### Post by omegamike on 2006-01-27
I had a similar problem where when I opened firefox the University of Minnesota webpage opened up automatically. Mine was actually a problem with the preinstalled launcher. I simply opened up the menu editor and changed the command on the launcher from "firefox *some modifiers*" to simply "firefox" minus the quotes of course. It worked like a charm. It seems simple, but you might check what launch command is being executed and change it to just firefox.

---

### Post by AmboyGuy on 2006-01-27
[omegamike]("http://ubuntuforums.org/member.php?u=24992") is right. If I remember correctly deleting the %u in the command got rid of the University of Arizona stuff when it happened to me

---

### Post by cooldudejz on 2006-01-27
i once had this same problem, i just made a new launcher and it went away

---

### Post by Sparkalo on 2006-01-27
I had this problem a while ago...I fixed it using some override in one of my prefs files...of course, it's a horrible fix because it totally overrides the homepage option in the browser.

A better fix is removing the %u flag from the command : P.  I had University Of Arizona as well : P

---

### Post by tnichols on 2006-01-28
Removing the %u from the launcher fixed it.

MANY THANKS!!!

---

