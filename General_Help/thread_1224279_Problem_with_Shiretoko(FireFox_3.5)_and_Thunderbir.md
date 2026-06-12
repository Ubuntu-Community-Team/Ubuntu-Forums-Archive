---
title: "Problem with Shiretoko(FireFox 3.5) and Thunderbird"
date: 2009-07-27
forum: General Help
---

### Post by harecanada on 2009-07-27
Since I upgraded to FireFox 3.5, if I get a live link in an e-mail and try clicking on it, it doesn't work. I have to copy and paste it. Small problem but it never worked that way with previous versions of FF. Anyone know of a solution to this?
harecanada

---

### Post by KegHead on 2009-07-27
Hi!

I'm having the sames problem.

Any help would be appreciated!

KegHead

---

### Post by credobyte on 2009-07-27
```
Preferences / Applications / mailto

```

---

### Post by nikhilk on 2009-07-27
> **harecanada said:**
> Since I upgraded to FireFox 3.5, if I get a live link in an e-mail and try clicking on it, it doesn't work. I have to copy and paste it. Small problem but it never worked that way with previous versions of FF. Anyone know of a solution to this?
harecanada

See if adding this to the "user.js" file (create it if not present) in your default Thunderbird profile directory helps (assuming The Firefox 3.5 executable is "/usr/bin/firefox")
```

user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");

```

---

### Post by redilyn on 2009-07-27
You need to change Shiretoko to be the default browser.

Open Shiretoko, Click Edit -> Preferences -> Advanced.

Click "Check Now" to make Shiretoko your default browser.

---

### Post by undeadboe on 2009-07-27
The newer releases of firefox usually have a lot of bugs. my suggestion would be to downgrade your firefox until the bugs are worked out.

---

### Post by harecanada on 2009-07-27
redilyn - I tried that but the Check Now button didn't work

nikhilk - I don't have a user.js file and don't know how to make one. I do have a prefs.js file but don't know how to add to it. i copied and pasted your code in but it didn't stay in.

credobyte - I tried that and no joy... didn't work

Thanks for the attemps so far. It is much appreciated. 
harecanada

---

### Post by nikhilk on 2009-07-28
> **harecanada said:**
> nikhilk - I don't have a user.js file and don't know how to make one. I do have a prefs.js file but don't know how to add to it. i copied and pasted your code in but it didn't stay in.

Just create an empty file with your favorite text editor and paste just those three lines in it and save it as user.js.

Yup, adding it to prefs.js won't work.

---

### Post by harecanada on 2009-07-28
nikhilk - I made the file, now where do I put it?
harecanada

---

### Post by nikhilk on 2009-07-29
> **harecanada said:**
> nikhilk - I made the file, now where do I put it?
harecanada

Put it directly under your default Thunderbird profile directory (which will have name like xxxxxxxx.default).
So the path will be ~/.mozilla-thunderbird/xxxxxxxx.default/user.js

---

### Post by CatKiller on 2009-07-29
System &#8594; Preferences &#8594; Preferred Applications &#8594; Internet. Make the preferred web browser firefox-3.5.

---

### Post by harecanada on 2009-07-30
Check this link out and see if this solution works for you.
harecanada

[http://ubuntuforums.org/showthread.php?p=7708157#post7708157](http://ubuntuforums.org/showthread.php?p=7708157#post7708157)

---

### Post by cmost on 2009-07-30
Once again, making things harder than they are.  Simply change "firefox" to "firefox-3.5" wherever you call the web browser; be it shortcuts, etc.

---

### Post by von Stalhein on 2009-10-01
<it started to work after I'd logged out and into XP - maybe it got jealous. Weird though, as I'd rebooted numerous times>

OK, it should be simple.

```
which firefox
```
gives me ```
usr/bin/firefox
```

Shiretoko is set as the default web browser.

System > Preferences > Preferred Applications is set to Open with Web Browser Default. The command displayed is ```
/usr/bin/firefox-3.5 %s
```

I have a user.js file with the following settings
```
user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox-3.5");
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox-3.5");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox-3.5");
```

In the config editor (prefs.js) I have the protocol handlers for http, ftp and https set as in the user.js file.

Still no linky open :-((


My next step please??

---

### Post by blakeatl on 2009-10-30
> **von Stalhein said:**
> 

I have a user.js file with the following settings
```
user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox-3.5");
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox-3.5");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox-3.5");
```

In the config editor (prefs.js) I have the protocol handlers for http, ftp and https set as in the user.js file.

Still no linky open :-((


My next step please??


I've found that if you apply those steps in thunderbird's about:config by creating a new string for each network protocol and apply the usr/bin as the command, firefox will open as the default browser.

---

