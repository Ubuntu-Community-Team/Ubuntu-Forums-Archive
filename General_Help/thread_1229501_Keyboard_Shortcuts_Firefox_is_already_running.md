---
title: "Keyboard Shortcuts: Firefox is already running?"
date: 2009-08-02
forum: General Help
---

### Post by Inferiority Complex on 2009-08-02
I have assigned a keyboard shortcut to launch Firefox.

I currently have is mapped to "Super+Z" since these keys are beside each other on my keyboard.

Unfortunately, whenever I launch Firefox from this shortcut, I receive an error about Firefox is already running and I should close all other windows before launching it again.  Whilst this error displays on screen, Firefox opens in it's own regular window.  I suspect that the keyboard shortcut is launching two instances of Firefox.

Currently, the command I have specified in the Keyboard Shortcuts manager is "firefox".  When I checked with Menu Editor to see what command it used, I find I should have it as "firefox %u" but when I use this, I get two Firefox windows.  One opens with the regular Firefox homepage, and the other opens with [www.%u.com](www.%u.com) in the address bar and an Address Not Found error: "www.%u.com could not be found. Please check the name and try again."

I also configured "Super+I" for Thunderbird which also attempts to launch two instance of Thunderbird which gives the same error as Firefox.  I configured "Super+Space" to launch AisleRiot Solitaire which launches with only one instance perfectly well.  I tried re-configuring the shortcuts so that Firefox launched with "Super+Space" but received the same error.

Can anyone help me so "Super+Z" launches only *one* instance of Firefox?

---

### Post by Inferiority Complex on 2009-08-04
I'm still playing around with the command line for the keyboard shortcut and have tried adjusting the "Repeat Keys" settings but I still get the error I mentioned above.

Can anyone help?

(Yes, I know I'm unashamedly bumping my own thread here...)

---

### Post by septekin on 2009-08-04
The command to start Firefox is simply "firefox". In case you want it to start at a given url the command is followed by the url:
"firefox www.google.com" will open the browser and take you straight to Google page.

As for the "already running" error, you may wish to check the following:
In your home/user folder there is a hidden folder named .mozilla. (To list the hidden folders you may need to hit "Control+H" combination). Under .mozilla, there should be a folder named "firefox" and in it a folder named "xxxxxxxx.default" where the xxxxxxxx is a random set of 8 characters. In the same folder there should be a file named "profiles.ini" with an entry "Path=xxxxxxxx.default". You may wish to confirm that the random characters in two are identical, if not change one or the other to make them so.

---

### Post by Inferiority Complex on 2009-08-04
> **septekin said:**
> The command to start Firefox is simply "firefox". In case you want it to start at a given url the command is followed by the url:
"firefox www.google.com" will open the browser and take you straight to Google page.

> **Inferiority Complex said:**
> Currently, the command I have specified in the Keyboard Shortcuts manager is "firefox".

Yes, Ihave "firefox" as my launcher command.  It causes the already running error & a normal firefox window to appear.

> **septekin said:**
> As for the "already running" error, you may wish to check the following:
In your home/user folder there is a hidden folder named .mozilla. (To list the hidden folders you may need to hit "Control+H" combination). Under .mozilla, there should be a folder named "firefox" and in it a folder named "xxxxxxxx.default" where the xxxxxxxx is a random set of 8 characters. In the same folder there should be a file named "profiles.ini" with an entry "Path=xxxxxxxx.default". You may wish to confirm that the random characters in two are identical, if not change one or the other to make them so.

Good idea, never thought of that.  Fortunately, they are the same so we can rule out that.

Thanks for trying...

I was hoping to transfer all my Winkey shortcuts (Copernic Winkey allowed keyboard shortcuts with the winkey) I used in Windows since I now want to have Linux as my main OS rather than the second one.

---

### Post by Inferiority Complex on 2009-08-04
Woah!  Got it!  SOLVED!!!

In the Keyboard Shortcuts proggie, the Desktop section has "<Super>+Z" listed under "Launch Web Browser" too.  So when I press the keys, Firefox is loaded twice!

Same for Thunderbird.

I removed one of the shortcuts for each one and everything works fine now, but I had to reboot for the new shortcuts to take effect.

Woohoo!

---

### Post by septekin on 2009-08-04
Good for you!

---

