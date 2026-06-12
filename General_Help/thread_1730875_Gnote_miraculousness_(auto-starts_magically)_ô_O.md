---
title: "Gnote miraculousness (auto-starts magically) ô_O"
date: 2011-04-16
forum: General Help
---

### Post by Gaba_p on 2011-04-16
Hi everybody,

I've had this problem for months now and I couldn't find a way to solve it. The issue is pretty simple: '**gnote**' app auto-starts when the system is booted and I've yet to find a way to stop it.

I've checked the following folders:

[B]/home/*user*/.config/autostart/
/home/*user*/.kde/Autostart/
/home/*user*/.local/share/autostart/[/B]

and I've also checked the following apps/modules:

[B]'Boot-up Manager' (BUM)
Autostart - KDE Control Module[/B]

and NOTHING. No sign of 'gnote' anywhere.

Now, I know I could just uninstall the app and forget about this (I don't even use it anymore) The thing is that I'm *REALLY* amazed of how incredibly difficult it is to manage something as simple as the apps that start-up with the system (something that could be done in the deprecated Windows XP with 'msconfig' since it first came up, I don't know.. a **decade** ago?)

I want to understand how this works because I like Ubuntu + KDE a lot and I have **[COLOR="Red"]NO[/COLOR]** intentions of going back to Windows.

Any help would be very much appreciated.

Cheers

---

### Post by Joe of loath on 2011-04-16
Tried this? (In reverse, obviously).

[http://permalink.gmane.org/gmane.linux.redhat.fedora.testers/89378](http://permalink.gmane.org/gmane.linux.redhat.fedora.testers/89378)

---

### Post by Gaba_p on 2011-04-16
Hi Joe,

like I said, there nothing referring to 'gnote' in '~/.config/autostart/' and I'm guessing (though I'm 100% not sure) that 'gnome-session-properties' manages auto-start apps **only** in a 'Gnome' session (there's no mention of 'gnote' here either, just in case). As I mentioned before, I'm using KDE.

Thanks anyway.

Any other ideas?

Regards,
Gabriel

---

### Post by Joe of loath on 2011-04-16
Hmmm, OK. I'm assuming you've hunted for checkboxes in gnote? :p

---

### Post by Gaba_p on 2011-04-16
You assume correctly and no, there are no 'Run at startup' checkboxes or anything similar in 'gnote'.

I remember that, because of this, I had to add manually a shortcut to the 'Autostart - KDE Control Module' a long time ago(back when I actually *wanted* it to auto-start). When I got tired of 'gnote', I removed that entry but the app continued to auto-start.

By the way, I have '**Start with an empty session**' checked under '*System settings / Session management*'. I mention this because this was the reason I couldn't get 'Pidgin' to stop auto-starting. As you can see, I've been having problems with KDE's auto-start manager features (or the lack of them) for a while now :)

Thanks for your help!

---

### Post by Joe of loath on 2011-04-16
'Tis a mystery indeed.

---

### Post by Gaba_p on 2011-04-16
Ok, thanks anyway Joe.

Anyone else can think of something that might be causing this?

---

### Post by Gaba_p on 2011-04-17
bump

Anything? Anyone?

---

### Post by Gaba_p on 2011-04-17
Well, I found it.
The 'gnote.desktop' file was located (hidden) in '/usr/share/autostart'

So that makes four ([color=red]**4!!**[/color]) folders (so far) that I have to check to track down auto-starting apps. A bit ridiculous if you ask me. Anyway... solved.

---

