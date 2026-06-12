---
title: "Checkgmail with Google Chrome"
date: 2009-11-25
forum: General Help
---

### Post by amaz1ng on 2009-11-25
Does anyone know how to tell Checkgmail to open Google Chrome to the gmail page and not Firefox?

---

### Post by raktarok on 2009-11-25
Open the preferences dialog(right click the tray icon) and enter this on 'command to execute on clicking':
```
google-chrome mail.google.com
```

---

### Post by benjam4 on 2010-02-09
> google-chrome mail.google.com

Tried this and chrome does not open
Also tried google-chrome mail.google.com [email]emailaccount@gmail.com[/email]
and google-chrome mail.google.com %u [email]emailaccount@gmail.com[/email]

But no luck- anyone with a similar issue in not getting Chrome to open instead of Firefox???

---

### Post by giarca on 2010-02-09
The first think is if you set Google Chrome as default browser in System --> Preferences --> Preferred Applications.
After all programs related to browser will launch chrome instead of firefox.

---

### Post by benjam4 on 2010-02-09
> Google Chrome as default browser in System --> Preferences --> Preferred Applications.

Thanks for the reply- I have confirmed the above and see that Web Browser > Custom > /usr/lib/chromium-browser/chromium-browser%s

And currently I have under Check Gmail > Preferences > Command to execute on clicking tray icon = google-chrome %u  

Although I have tried other commands in this sections as noted earlier and Chrome does not open.

Any other suggestions are appreciated.
Thanks

---

### Post by giarca on 2010-02-09
> **benjam4 said:**
> Thanks for the reply- I have confirmed the above and see that Web Browser > Custom > /usr/lib/chromium-browser/chromium-browser%s

Problem found.

/usr/lib/chromium-browser/chromium-browser%s refer to Chromium. Chromium is not Google Chrome (ok, same code but different policy and, of course, different executables).

So you have to set on Web Browser --> Custom the Google Chrome application.

For your information the path of Google Chrome should be /opt/google/chrome/google-chrome.

Update: After choose the right Preferred Applications you can set the default browser (or default behaviour) in checkgmail to be sure it read the gnome setting.

---

### Post by benjam4 on 2010-02-09
Thanks for the tip.  The setup of Chrome did not work but I followed your same logic and was successful in configuring as follows:

I replaced firefox and chrome with chromium in the CheckGmail Preferences:

> Check Gmail > Preferences > Command to execute on clicking tray icon = chromium %u

This allows me to open my email messages and contained links in Chrome (ium).

Thanks for your assistance.

---

### Post by borislevalle on 2010-05-28
I choose Chromium under Preferred Applications and set the execute command to "chromium %u"

Still, nothing... It checks my mail, but when I click the [COLOR="Red"]CheckGMAil[/COLOR] tray icon nothing happens. As soon as I change "chromium %u" to "firefox %u" it works fine.

Anyone knows how I can fix this?

P.S. The weird thing is that after choosing Chromium as Pref.App. Chromium says on start-up that it is not the default browser. How's that possible?

---

### Post by kerry_s on 2010-05-28
install "desktop-webmail" set it for gmail. use "desktop-webmail" as the command in checkgmail.

lol, forgot the pic.

---

### Post by borislevalle on 2010-05-28
Thanks, that works fine. It takes me straight to the Gmail inbox. 

However, I cannot directly go to the new e-mail, although there is an option to click "[COLOR="Red"]Open[/COLOR]". Instead it takes me to the inbox...

---

### Post by kerry_s on 2010-05-28
> **borislevalle said:**
> Thanks, that works fine. It takes me straight to the Gmail inbox. 

However, I cannot directly go to the new e-mail, although there is an option to click "[COLOR="Red"]Open[/COLOR]". Instead it takes me to the inbox...

try adding that "%u" on the end.
i prefer just go to the inbox, so i never look into it.

---

### Post by /bee/ on 2010-06-03
Is this referring to the red "Open" link?

[img]http://imgur.com/h0gMM.png[/img]

---

### Post by Michael_K_Vegfruit on 2010-07-25
> **borislevalle said:**
> I choose Chromium under Preferred Applications and set the execute command to "chromium %u"

I was having the same problem.  Looking elsewhere in this thread (see banjam4's comment), it looks like Chromium is called "chromium-browser", not "chromium".

So, you need to change the entry in the preference box to:

```
chromium-browser %u
```

That seemed to do the trick for me, anyway.

---

