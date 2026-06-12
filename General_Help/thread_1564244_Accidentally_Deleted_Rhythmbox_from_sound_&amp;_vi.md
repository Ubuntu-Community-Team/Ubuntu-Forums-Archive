---
title: "Accidentally Deleted Rhythmbox from sound &amp; video"
date: 2010-08-30
forum: General Help
---

### Post by jameshampshire on 2010-08-30
i accidentally deleted the shortcut for rhythmbox from sound & video.
and cant restore it i don't know where the location and etc is.
i tried uninstalling it properly from the software centre and synaptic manager and reinstalling it didnt restore the shortcuts.

any help?

im using ubuntu lucid lynx 10.04 btw.

---

### Post by jameshampshire on 2010-08-30
bumping for quick assistance

---

### Post by Sam on 2010-08-30
Run in a terminal:```
rm ~/.local/share/applications/rhythmbox.desktop*
```

Please wait at least 24 hours before bumping.

---

### Post by jameshampshire on 2010-08-30
thanks mate it restored it but i dont have my icons.
the icon in the sound & video folder for it doesnt show up.
and i have a cross on the icon thats in my taskbar?

---

### Post by ean5533 on 2010-08-30
> **Sam said:**
> Run in a terminal:```
rm ~/.local/share/applications/rhythmbox.desktop*
```

Please wait at least 24 hours before bumping.

Just a curious passerby question: how does removing the rhythmbox .desktop files solve his problem? Are you suggesting that he then reinstall rhythmbox after he removes those .desktop files? Or is there something else I'm not getting here?

---

### Post by jameshampshire on 2010-08-30
oh dont worry i know what i did.
i accidentally deleted the icons from the theme pack.
il just reinstall it.

---

### Post by jameshampshire on 2010-08-30
hey guys sorry to be annoying.
but i have wii black as my theme right.
and i have ubuntustudio as my icon theme etc.
but i dont like the rhythm box icon it looks crappy.
hence why i accidentally deleted it from the menu trying to replace it with the original.
can you help me out to get the original icon.

---

### Post by Sam on 2010-08-30
> **ean5533 said:**
> Just a curious passerby question: how does removing the rhythmbox .desktop files solve his problem? Are you suggesting that he then reinstall rhythmbox after he removes those .desktop files? Or is there something else I'm not getting here?

The regular launchers are stored in /usr/share/applications

You can override them by duplicating them in your personal applications folder in ~/.local/share/applications

In the case where you hide an icon, it duplicate the default launcher, and adds in the file:```
NoDisplay=true
```

So even if you reinstall the application, the personal launcher is kept and still overrides the regular one.

---

### Post by Sam on 2010-08-30
> **jameshampshire said:**
> can you help me out to get the original icon.

Edit the launcher and set the icon file as /usr/share/app-install/icons/rhythmbox.png

---

### Post by jameshampshire on 2010-08-30
> **Sam said:**
> Edit the launcher and set the icon file as /usr/share/app-install/icons/rhythmbox.png


will that also give me the original taskbar icon?

---

### Post by jameshampshire on 2010-08-30
alright so yeah it changed the icon in the application sound and video.
but i still have the ugly icon in the up right corner.

sorry but im funny about certain things not looking right.

---

### Post by jameshampshire on 2010-08-30
or any system tray icon for that matter?

---

### Post by jameshampshire on 2010-08-30
heeeeelp me!

---

### Post by jameshampshire on 2010-08-30
still bumping for help.

---

### Post by ean5533 on 2010-08-30
> **jameshampshire said:**
> still bumping for help.

Please don't keep bumping the thread every few minutes. Someone who knows the answer will respond when they can. You should only bump a thread once a day just to make sure it doesn't get lost.

---

### Post by jameshampshire on 2010-08-30
well if someone was helping me quicker i wouldnt be bumping so often.
like that sam guy he helped me but didnt reply back to my question.
im sorry im new to this site and it isnt like 4chan in the matter of bumping doesn't matter.

---

### Post by Sam on 2010-08-30
> **jameshampshire said:**
> well if someone was helping me quicker i wouldnt be bumping so often.
like that sam guy he helped me but didnt reply back to my question.
im sorry im new to this site and it isnt like 4chan in the matter of bumping doesn't matter.

No one here is paid to provide support. We all do this on our own time. Also don't send private messages to ask for help. Please keep this in mind.

According your problem, I believe that the notification icon is set using a generic name, not a particular filename. So if you change your theme, the icon will be overriden. You may replace the theme icons manually.

---

### Post by jameshampshire on 2010-08-30
Jesus it was only a private message stress less if you don't send  messages for help what do you send it for a hook-up. all im doing is  asking for help if i bump my thread to get help quicker whats wrong with  that. its just a website stop sooking who cares i don't care if everyone takes take advantage of it and floods there thread to boost it. as long as they are getting a quicker response im happy for them. im not going to sit on a website all day acting  like im a moderator telling people off. if you're an ubuntu wiz help the damn person.

---

### Post by cariboo on 2010-08-30
Remember we are all volunteers here, we provide support for free. If your problem is that urgent, you may want to look at [paid]("http://www.canonical.com/enterprise-services/ubuntu-advantage/support") support.

I would advise you have a look at the [Forum Do's and Don'ts]("http://ubuntuforums.org/showthread.php?t=885580").

---

