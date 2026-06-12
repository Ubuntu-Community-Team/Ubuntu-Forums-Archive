---
title: "noscripts still blocking but uninstalled! Firefox screwed ..."
date: 2011-06-08
forum: General Help
---

### Post by Bucky Ball on 2011-06-08
Hi all,

Thought I'd try the Firefox add on NoScripts. Didn't like it, uninstalled. Now it is blocking things regardless and seemingly randomly. The forums for instance are a dog's breakfast. 

Why is this thing still ambling around like an aimless zombie? Occasionally Firefox just locks up and all I can do is shut it down. When I restart the machine or logout it makes no diff. The aimless NoScripts zombie still lurks, playing havoc with my web experience.

Any suggestions on how to completely kill this beast would be more than welcome. This machine runs smooth as and rock solid generally. The last thing I expected was some add-on bomb completely screwing things over. Cheers. ;)

EDIT: Hmm, just had a thought. Seems like Java is not working so I look in add-ons and Java add-ons seem to be uninstalled also. I'll have a tweak and get back ...

EDIT 2: When I go to Youtube, there are no thumbnails of the vids, just white squares and text, yet when I click a vid it plays without a problem. What the heck is happening? I don't believe that add-on could create so much havoc ... I didn't even make any changes to noscripts! Installed it and visited about five websites then uninstalled. Sheesh.

---

### Post by Thewhistlingwind on 2011-06-08
Try enabling java from preferences/security (Wherever it is.)

---

### Post by Bucky Ball on 2011-06-08
Thanks. It is in Preferences>Content>Enable Javascript.

No different and it was enabled. 

I have tried shutting down the machine and rebooting afresh but no different. Websites still a mess. Instead of uninstalling NoScripts I first disabled it. I then uninstalled. Just for the hell of it I am going to install it and then uninstall it without disabling. Shot in the dark ...

---

### Post by Bucky Ball on 2011-06-08
Seems to be killing some graphics. Really odd. A couple of screenshots for example. One is the Wikipedia homepage devoid of a logo or any graphics at all. The other shows Youtube with the selected video running fine (random choice incidentally!) and the thumbnails blank.

What is going on here? How can installing and uninstalling a teeny add-on cause this? This has the eerie feeling of a Windows waste of time over some weird anomoly. Never had this happen to me in Linux before.

Should I blame it on the IPv6 testing that's currently going on??? lol. I think not but I can't explain it any other way ... yet. 

The forums have no icons or avatars. There is only text. I can't attach any images after all because there is no paperclip, naturally, and no text saying 'paperclip'. Truly bamboozled on this one.

---

### Post by Irihapeti on 2011-06-08
You could set up a new profile. Leave the old one there for the moment.

Enter ```
firefox -P
``` in a terminal and follow the instructions to create a new profile.

Once you have a new profile, you can copy your bookmarks and passwords from the old one.

---

### Post by Bucky Ball on 2011-06-08
Thanks Irihapeti, a new profile indeed restored everything to normal. But I want to rectify the existing default profile rather than waste time creating a new one then copying everything over and finding the needle in a haystack file in the old profile that could be causing the problem (although this would be a last resort). Thanks for the tip with Firefox profiles. Never knew I could do that.

Looking in the default profile folder I discovered a file called:

NoScriptsSTS.db

... which I thought might be causing some problems. I haven't experienced this kind of littering in Linux before. I deleted that, logged out and in again, but no different.

Wonder how I can locate and change the file in the default profile folder that is causing this problem? I'll keep digging. A time wasting little exercise caused by three minutes of curiousity ...

---

### Post by Bucky Ball on 2011-06-08
I made a new profile and copied everything from the old one without replacing the new files with the old where applicable. It was all pretty random and I allowed some to replace and other not. I have found myself with a functioning Firefox and the only thing missing is the tabs I had open in the old profile. That's no biggie.

Cheers, I'll consider this solved, even though I never really got to the bottom of the problem. Still keen to know what the hell happened there if anyone has any clues. All I know is I won't be installing and uninstalling NoScript again any time soon. Eight hour nightmare!

* EDIT: To be precise: After much more stuffing about making new profiles and experimenting with copying files back and forth and checking the effect, I had a bright idea.

I created a new profile and copied prefs.js to the old profile. It worked and everything is back to normal using the old 'default' profile.

---

### Post by Irihapeti on 2011-06-08
Sometimes there are curious interactions between addons. I've had this happen a few times myself, though NoScript wasn't the culprit. (I have used it for a few years now.) Other times, something weird just happens and there doesn't seem to be any logical explanation for it. Hence the value of a recent backup.

For anyone else reading this, places.sqlite has the bookmarks, and key3.db and signons.sqlite are needed for the passwords.

Anyway, I'm glad it's solved.

---

### Post by Bucky Ball on 2011-06-08
Cheers. This page gives a good description of the essential files and what they do.

[http://support.mozilla.com/en-US/kb/Recovering%20important%20data%20from%20an%20old%20profile#w_copying-files-between-profile-folders](http://support.mozilla.com/en-US/kb/Recovering%20important%20data%20from%20an%20old%20profile#w_copying-files-between-profile-folders)

---

### Post by lite1979 on 2012-02-20
Thank you. This was driving me nuts.

---

