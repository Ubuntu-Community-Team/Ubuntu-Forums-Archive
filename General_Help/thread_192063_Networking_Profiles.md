---
title: "Networking Profiles"
date: 2006-06-08
forum: General Help
---

### Post by sparty2809 on 2006-06-08
I have a laptop so I bring it to work and home.  I want to setup different profiles so that when I go to work, it loads all the correct networking settings and same when I go home.  However, every time I create a location, it keeps the previous/overwrites it if I modify it.  Any ideas on what I am doing wrong?

Thanks,
sparty2809

---

### Post by xtacocorex on 2006-06-08
I recommend wifi-radar instead of the Gnome panel thing or KWifiManager.
```
sudo aptitude install wifi-radar
```

wifi-radar starts up during the boot process, after networking, and will auto connect to any one of the closest configured access points.

To set up a new location:
```
sudo wifi-radar
```

Click on your AP and then click connect. It will ask if you want to create a profile and answer yes. Fill in the relevant options and it should be fine as long as they are correct.

Do the same when you get to work.

---

### Post by sparty2809 on 2006-06-08
That would work if it was WiFi, but I am not using WiFi.  Any other ideas?

---

### Post by xtacocorex on 2006-06-08
My bad, I automatically assumed you were using it since you mentioned laptop.

Now I'm sorta at a loss since I don't have my wired connection port enabled.

---

### Post by sparty2809 on 2006-06-08
Well, I would love to use WiFi, but I can't get it to work with my Inspiron 6000.  Once I figure that out, that program should work great!

---

### Post by karthik085 on 2006-06-09
[QUOTE=sparty2809]Well, I would love to use WiFi, but I can't get it to work with my Inspiron 6000.  Once I figure that out, that program should work great![/QUOTE]
If you have problems setting WiFi up on your laptop, please refer to
[http://www.ubuntuforums.org/showpost.php?p=1074910&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1074910&postcount=1)

When you say, you created a different profile, what do you mean by that? Let me know how you did it.

---

### Post by sparty2809 on 2006-06-11
I open up network-admin and click new location.  Set up all the settings and click ok.  Then I open it back up, click new location give it a different name and set it up.  The DNS won't save.  Am I doing it wrong?

---

### Post by 23meg on 2006-06-11
Did you try Network Manager? Maybe you should; it's in the repositories.

---

### Post by sparty2809 on 2006-06-12
How do you startup network-manager after you install it?

---

### Post by stimpsonjcat on 2006-06-12
the way network-admin works is a little counter-intuitive: [http://bugzilla.gnome.org/show_bug.cgi?id=170663]("http://bugzilla.gnome.org/show_bug.cgi?id=170663")

---

