---
title: "Addons and other stuff gradually failing"
date: 2011-06-02
forum: General Help
---

### Post by tiggsy on 2011-06-02
This is all a bit strange. Using Lucid.

A few days ago, feedly (which is a firefox add-on) stopped working. I tried reinstalling the add-on, but this didn't make any difference. Then yesterday, the zynga toolbar disappeared not just from the browser, but from the list of toolbars - though it's still listed as an addon. Neither of these is particularly vital, so I didn't worry about it.

Now today, LastPass password manager isn't loading up, which is a real pain, and also Tweetdeck (which runs under Air) is not going to full load (it says loading columns and then hangs).

Has anybody any ideas?

---

### Post by LowSky on 2011-06-02
have you upgraded to the firefox 4? I'm guessing many of the addons could not work with the older version.

you can also back up your bookmarks then delete the /home/user/.mozilla folder to see if that fixes everything...

---

### Post by tiggsy on 2011-06-03
No. I'm just getting the updates that come by themselves, and with the distro I'm using, it's currently Firefox 3.6.17.

However, it seems as if javascript is only working for some stuff, and not others. This has happened before and I went onto Chrome for a bit, but it is not good for the work I do all day, every day, so I reverted and was pleased to find it was back to normal... until now.

I am going to try and do a reinstall first of Tweetdeck. If this sorts the problem (as the feedly reinstall didn't), then I will probably do firefox as well.

In the meantime, if anyone else has any ideas...

---

### Post by tiggsy on 2011-06-03
Woops. Just had another wierd firefox thing... ended up with a duplicate post.

Go figure.

---

### Post by tiggsy on 2011-06-06
Reinstalling Tweetdeck didn't seem to work, so I did a reinstall of Air, again with no apparent effect until I started up this morning, when TD is working again.

I'm reluctant to reinstall ff, but I guess I will have to bite the bullet and go for it if no other ideas are suggested...

---

### Post by linuxinstalledfromhdd on 2011-06-06
Install Firefox 4 PPA and upgrade your browser to stop this from occurring.

In your Terminal cut and paste the following:

```

sudo add-apt-repository ppa:mozillateam/firefox-stable 
sudo apt-get update 
sudo apt-get upgrade

```

---

### Post by tiggsy on 2011-06-06
Excellent. LastPass is now working! But tabkit or whatever I'm using now isn't. The tabs are sliding off the screen, which is not good. Still, hopefully a new version will come out at some point...

---

### Post by linuxinstalledfromhdd on 2011-06-06
Try reinstalling any plugins that fail to operate.

---

### Post by tiggsy on 2011-06-06
Tabkit is pretty old "not expected to be updated" and there seems to be nothing like it. Shame. It's really useful. Oh well.

At least there's a new version of fireftp.

---

