---
title: "Autologin &amp; Unlock Keyring"
date: 2010-01-25
forum: General Help
---

### Post by Scunnered on 2010-01-25
Currently I can by using autologin access my wireless connection at start up.  Yesterday I decided to download the BBC iPlayer Desktop as it would let me view programmes whilst offline.  

What I now find when I startup is that the autologin works OK but I am then confronted with a display advising that I have to **Unlock Keyring**.  I have had a look at the passwords and encrypted keys but am unable to see what I need to do to automate the request to unlock keyring.

Is it possible to have this run in tandem with my autologin and could you please guide me how to achieve this.

Thanking you in anticipation

---

### Post by andersja on 2010-01-25
Well, I'm not sure why the iPlayer application trigger the keyring (unless you registered a set of BBC iplayer credentials as part of configuring it?)

Regardless, the quick fix is to blank our your keyring password, i.e. go to the change keyring password dialogue and set the new password blank. Combined with autologin this will make your PC less secure, but it will never again ask for keyring password...

---

### Post by Scunnered on 2010-01-26
**andersja**

Many thanks for your reply. Please accept my apology for the delay in replying but I have been attempting to work out why I am being asked for a password without any luck.

When downloaded the player it automatically loaded Adobe Air which I have deleted but am unable to find how I can delete the iPlayer.  Can you offer guidance on that.

I was happy use the iPlayer offline but if it is going to cause security problems by leaving the system open then I would prefer not to do so.  I when taking the laptop out of the house disable the auto login to ensure the system is secure.

If you can further assist it will be appreciated

---

### Post by Scunnered on 2010-01-27
Slight progress made. I was totally unable to find any way to delete the iPlayer so I downloaded in an attempt to overwrite the programme.  This seemed to work as having altered some of the settings I can avoid having the password request confront me on startup.  I was able to avoid the iPlayer starting up at boot however when I select it from the menu I still have to enter a password and it then displays an icon on the panel next to my sound & network symbols.

It would appear the BBC call for a password automatically during the download and Karmic will not let me use a blank.  At the very least I can now pick and choose when I wish to activate the iPlayer.

This looks like the best I am going to get and unless anyone knows better I will accept this as such.

---

