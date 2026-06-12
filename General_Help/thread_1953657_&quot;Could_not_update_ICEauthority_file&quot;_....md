---
title: "&quot;Could not update ICEauthority file&quot; ..."
date: 2012-04-06
forum: General Help
---

### Post by sirriffsalot on 2012-04-06
Hello!

   I was about to hand over a laptop with Ubuntu 11.04 (I think, let me know if it matters) to someone, but before I did I felt like going fancy and changing the password. Long story short I typed a wrong password right twice, apparently, and could therefore not get access. So I went to the recovery mode and selected the root option and typed in "#passwd thor" and enter and following that my desired password.

   After that, these two curious messages have been coming my way right after one another... "Could not update ICE.authority file" and "There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)" and on top of this a few moments later "Nautilus could not create the following required folders: /home:thor/Desktop,/home/thor/.nautilus. Before running Nautilus, please create these folder, or set permissions such that Nautilus can create them."

   If I press "OK" to that, an update information window pops up telling me to "Record your encryption passphrase" and a lot of further text... After THIS (having pressed "Close") my panels are gone and only my desktop background is on display, however I can get to a terminal.. Didn't want to take any chances with the different suggestions out there, which are mostly only for these problems in singular, not added together, so I would really appreciate some help!

   --> Leo

   Thanks for your time!

---

### Post by sirriffsalot on 2012-04-06
bump!:)

---

### Post by Yellow Pasque on 2012-04-06
Check the permissions. I'm guessing root owns your user's folder or at least the files/directories in question:
```
cd /home
ls -la
cd ~/
ls -la
```

---

### Post by sirriffsalot on 2012-04-06
Well, I did those commands, and the outputs are fairly "rooty", haha:) Problem is I have no access to my panels, so copying the outputs over was rather tiring. How would I go about opening a usb stick's folder via terminal? And move a document file to it so I can post the outputs to you?:)

--> Leo

Edit: 

```
 sudo chown thor:thor /home/thor 
```

this did not succeed either ...:-(

---

### Post by Yellow Pasque on 2012-04-06
I don't need to see the output. You probably want everything owned by your user (so assuming your user is named 'thor'):
```
sudo chown -R thor:thor /home/thor/
```

---

### Post by sirriffsalot on 2012-04-06
I just said above that that did not do the trick :-D You just as tired as I am?:) Or, perhaps it did do a part of the trick, but the error message still appears when I've rebooted. Did this as a root command in recovery mode as well.. no dice=(

---

### Post by Yellow Pasque on 2012-04-06
> **LeoTB said:**
> I just said above that that did not do the trick

While I may be somewhat drunk/tired, I can see that you didn't use the -R (recursive) option to change all of the files within the directory (no -R means only the directory itself).

Are you drunk too?:lolflag:

---

### Post by sirriffsalot on 2012-04-06
Forgot to add it I admit (to the forum post), but however I know I did do that. I did it again however, but this simply does not change anything. Would it help to mention that there are other errors after the "ICEauthority" one? The follow-up error goes like this: "There is a problem with the configuration server. (/usr/lib/libconf-sanity-check-2 exited with status 256)"

After this comes: "Nautilus could not create the following required folders: /home/thor/Desktop,/home/thor/.nautilus."

Peace:D

---

### Post by sirriffsalot on 2012-04-07
bump:)

---

