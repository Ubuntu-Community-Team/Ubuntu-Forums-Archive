---
title: "sudo nautilus issue"
date: 2010-02-09
forum: General Help
---

### Post by Erik Jögimar on 2010-02-09
I've tried running ```
sudo nautilus
```a couple of times as i'm new and i seem to have trouble copying things
from my desktop to the desktop of another user, without using the above
code in the terminal. When i do this however, the terminal also spits out
a couple of lines of other code that i do not understand. Could someone
possibly help enligten me as to how to remedy this?

```
(nautilus:10071): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:10071): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:10071): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:10071): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: "net usershare" returnerade fel 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Filen eller katalogen finns inte
Please ask your system administrator to enable user sharing.

```I am currently running Ubuntu 9.10 on a Fujutsi Siemens Amilo laptop.

---

### Post by Bachstelze on 2010-02-09
Firstly, just a reminder, it is considered rude to copy files into another user's home folder. Better place the file where the user can access it, and let him copy it into his folder if he wishes.

Now if you have a good reason to do this, another reminder: you should use [font=monospace]gksudo[/font] instead of [font=monospace]sudo[/font] to sun graphical apps with root privileges. Try

```
gksudo nautilus
```

and see if it fixes your problem. Otherwise, why not just use good ol' [font=monospace]cp[/font]? I don't think just running [font=monospace]sudo cp /home/user1/Desktop/somefile /home/user2/Desktop[/font] is insanely complicated.

---

### Post by Erik Jögimar on 2010-02-09
> Firstly, just a reminder, it is considered rude to copy files into another user's home folder. Better place the file where the user can access it, and let him copy it into his folder if he wishes.i was copying some things into a text file and sent it to my girlfriends desktop as we share one laptop with two accounts, so it's not a random thing i'm doing. 

> 
Now if you have a good reason to do this, another reminder: you should use [FONT=monospace]gksudo[/FONT] instead of [FONT=monospace]sudo[/FONT] to sun graphical apps with root privileges. Try

```
gksudo nautilus
```and see if it fixes your problem. Otherwise, why not just use good ol' [FONT=monospace]cp[/FONT]? I don't think just running [FONT=monospace]sudo cp /home/user1/Desktop/somefile /home/user2/Desktop[/FONT] is insanely complicated.
I am pretty new to linux so i don't know how to work overly much
with commands, but i'll try that next time :) as for running gksudo instead, it still gives these error messages tho.

---

### Post by warfacegod on 2010-02-09
I get the same warnings when using gksudo nautilus. I haven't noticed any issues from it so I have bothered to fix it. From what I understand, it's just a silly glitch that doesn't mean much. I wouldn't worry about it.

Bachstelze is right about using sudo for a GUI app. It has the potential to cause some very serious harm to your filesystem. gksudo is much safer.

---

### Post by physeetcosmo on 2010-02-09
> **Erik Jögimar said:**
> ...When i do this however, the terminal also spits out
a couple of lines of other code that i do not understand.
```
** (nautilus:10071): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: "net usershare" returnerade fel 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Filen eller katalogen finns inte
Please ask your system administrator to enable user sharing.

```

i am not sure about the first few errors, those are function calls that aren't valid or aren't returning properly...

The final error is saying that:

1) Nautilus is not ALLOWED to access network shares (the error specifically states "Samba Shares").
-OR-
2) Nautilus is generically trying to access Samba Shares and none are actually available. This may be due to the fact that Nautilus is generically built for Ubuntu, and may be "defaulted" to check for Samba shares (or other forms of network shares) whenever it is launched.

I agree with warfacegod, just ignore these errors. One of the disadvantages of "pre-built" packages, that's all :)

---

