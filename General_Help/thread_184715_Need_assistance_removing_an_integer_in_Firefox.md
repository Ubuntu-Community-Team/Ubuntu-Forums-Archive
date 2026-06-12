---
title: "Need assistance removing an integer in Firefox"
date: 2006-05-30
forum: General Help
---

### Post by cajunaggie on 2006-05-30
I added a flash-pop-up-blocking integer to Firefox in about:config. Unfortunately I gave it the wrong name and all Firefox lets me modify is the value for the integer. Is there a way I can delete this integer? If I can't, will have an extraneous integer in my about:config screw with Firefox?

---

### Post by aysiu on 2006-05-30
I think you can delete it from the ~/.mozilla/firefox/*profilename*/prefs.js file.

---

### Post by cajunaggie on 2006-05-30
I found that file but I can't find the particular integer I'm looking for. Any ideas?

---

### Post by aysiu on 2006-05-30
What's the integer you're looking for?

I'll give you an example of how to find it. So, I'm looking for the boolean (it'll work for an integer, too) that has ipv6 in it: ```
username@ubuntu:~$ grep -i -n -r ipv6 ~/.mozilla/firefox/
pluginreg.dat     profiles.ini      shgor6iz.default/
username@ubuntu:~$ grep -i -n -r ipv6 ~/.mozilla/firefox/shgor6iz.default/prefs.js
100:user_pref("network.dns.disableIPv6", true);
username@ubuntu:~$
``` What I did after that first line was press Tab twice, as there's no way in hell I'd remember *shgor6iz.default*. Then I typed *shg* and pressed Tab twice again, and the full name filled in.

Then I see that it's in line #100 of my *prefs.js* file.

When I go to line #100 in Kate (see attached screenshot)--there it is.

---

### Post by cajunaggie on 2006-05-30
Interestingly enough the integer has disappeared. I had deleted its value from the about:config just in case and when I fired up about:config earlier today to look for it, it was gone. All that remains is the integer I wanted in the first place. 
:-k Fascinating

---

