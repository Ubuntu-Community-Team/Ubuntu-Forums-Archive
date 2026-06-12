---
title: "finding this file"
date: 2009-10-06
forum: General Help
---

### Post by ub9876 on 2009-10-06
I cant find this file in home/user/    etc


home/<your_user>/.config/chromium/Default/Preferences

there is no config that I can see....

anyone in the know
9.04
trying out Google browser...not too bad...

---

### Post by Giblet5 on 2009-10-06
I assume you've tried ```
locate -i preferences | less
```

That'll be case-insensitive and will probably return a lot of hits...

---

### Post by Giblet5 on 2009-10-06
Most prefs are stored in .gconf

---

### Post by ub9876 on 2009-10-06
I'll try those
 I did manage to find libchrome stuff in usr/lib

If I use the terminal, and change some pref code, what is the correct way to save so it doesnt revert back...
this is about font prefs in Chrome browser....some idiot made them way too small for ANyones preferences....
dork ***

---

### Post by Giblet5 on 2009-10-06
> **ub9876 said:**
> I'll try those
 I did manage to find libchrome stuff in usr/lib

If I use the terminal, and change some pref code, what is the correct way to save so it doesnt revert back...
this is about font prefs in Chrome browser....some idiot made them way too small for ANyones preferences....
dork ***


Maybe he has a 640x480 display.... ;)

You probably DON'T want to change any files outside of your user directory.

I would ask the author or [look here]("http://dev.chromium.org/") for tips.

---

### Post by dhughes on 2009-10-06
On my system in my /home I have a hidden .cxchromium folder with subfolders such as cxmenu.conf, cxbottle.conf etc.

---

### Post by ub9876 on 2009-10-06
everyone hates this problem...its not my system..
it works perfectly on everything else...
its interesting to see where some peoples thinking goes...
 How do I use a text editor to bring up this file..?
exactly...in 9.04...I could not find the .config file..
only some stuff for chrome that said libchromeXvmc or similar.




Using text editor to open "Documents and Settings\User_Name\Local Settings\Application Data\Google\Chrome\User Data\Default\Preferences"
You will find the "webkit": {  "webprefs": { in the file. Those settings are for WebKit.
In my setting example:
   "webkit": {
      "webprefs": {
         "default_fixed_font_size": 11,
         "default_font_size": 12,
         "fixed_font_family": "Bitstream Vera Sans Mono",
         "minimum_font_size": 12,
         "minimum_logical_font_siz": 12,
         "sansserif_font_family": "Times New Roman",
         "serif_font_family": "Arial",
         "standard_font_is_serif": false,
         "text_areas_are_resizable": true
      }
   }

The minimum_font_size and minimum_logical_font_size prevent Chrome to use very small font size for display.

Remember to close Chrome first before you edit the file, or the file you saved will be overwritten by Chome after exiting.

---

### Post by kanikilu on 2009-10-06
> **ub9876 said:**
> I cant find this file in home/user/    etc


home/<your_user>/.config/chromium/Default/Preferences

there is no config that I can see....

anyone in the know
9.04
trying out Google browser...not too bad... Where did you install from? I'm using the [PPA for Ubuntu Chromium Daily Builds](https://launchpad.net/~chromium-daily/+archive/ppa), and the file /home/<username>/.config/chromium/Default/Preferences definitely exists (only after running Chromium the first time, of course).

Maybe it's just that you don't see the entire .config directory. Open Nautilus or go to Places > Home Folder in the menu. Then select View > Show Hidden Files (or press CTRL+H). You should now be able to see and browse into the .config directory. Right-click on the Preferences file if you find it, and select "Open with gedit".

However, in this version of Chromium, you don't need to mess with a preferences file to change the default font. I just go to Option > Under the Hood > Change font and language settings, and the changes take effect immediately (and are written to the config file you mentioned).

---

### Post by ub9876 on 2009-10-06
I found it in hidden files, Google Chrome/defaults,the font tool thing does Not change it permanently,
Please look at the end of this file... should I insert this code in the brackets.. I will show you the file code and the modified pref code..you will see what the scoop is....first is the file code,just the end of it...


   "security": {
      "cookie_behavior": 1
   },
   "session": {
      "urls_to_restore_on_startup": [  ]
   },
   "webkit": {
      "webprefs": {
         "inspector_settings": "lastActivePanel:string:elements\n"
      }
   }

Now here is the mod code...

You will find the "webkit": {  "webprefs": { in the file. Those settings are for WebKit.
In my setting example:
   "webkit": {
      "webprefs": {
         "default_fixed_font_size": 11,
         "default_font_size": 12,
         "fixed_font_family": "Bitstream Vera Sans Mono",
         "minimum_font_size": 12,
         "minimum_logical_font_siz": 12,
         "sansserif_font_family": "Times New Roman",
         "serif_font_family": "Arial",
         "standard_font_is_serif": false,
         "text_areas_are_resizable": true
      }
   }

The minimum_font_size and minimum_logical_font_size prevent Chrome to use very small font size for display.

Remember to close Chrome first before you edit the file, or the file you saved will be overwritten by Chome after exiting.


Can you show exactly how to insert this   Thanks much...

---

### Post by kanikilu on 2009-10-06
I'm not really sure what you're asking...just open the Preferences file with gedit and then copy & paste those additional lines into the "webprefs" section.

---

### Post by ub9876 on 2009-10-06
but where exactly.??  in between the brackets? or colons?
should I get rid of this..

nspector_settings": "lastActivePanel:string:elements\n"

and replace it with the other code?

---

### Post by kanikilu on 2009-10-06
> **ub9876 said:**
> but where exactly.??  in between the brackets? or colons?
should I get rid of this..

nspector_settings": "lastActivePanel:string:elements\n"

and replace it with the other code?
I don't think it matters, just anywhere in between the curly-braces for that section. I don't know about the other setting since I don't know what it does, but I would leave it for now.

---

