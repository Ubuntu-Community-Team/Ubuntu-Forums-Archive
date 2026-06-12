---
title: "Firefos starts in offline mode (Lucid)"
date: 2010-07-16
forum: General Help
---

### Post by jackn on 2010-07-16
Firefox is set to launch automatically at startup.
It regularly starts up in offline mode.
Then, once wireless connection is established, I have to restart FF in order to get it to browse the net.

This has been amply discussed and fixes have been suggested.
I've tried at least three modifications using FF's 'about:config', but to no avail.

What should I do?

---

### Post by mike555 on 2010-07-16
so I guess you have tried; 

 open about:config and set:

toolkit.networkmanager.disable

to "true"

---

### Post by jackn on 2010-07-16
Yes, I have, Mike.
And, just to be sure, I've just tried it again.
No honey.

Thank you for your help.

---

### Post by jackn on 2010-07-16
Bump.

---

### Post by lovinglinux on 2010-07-17
Instead of adding Firefox to the Startup Applications, create a script to delay the start of Firefox until the network is up like this:

```
#!/bin/bash

sleep 3000
firefox
```

Then add the script to the startup.

---

### Post by anutjob on 2010-07-17
[https://addons.mozilla.org/en/firefox/addon/13233/](https://addons.mozilla.org/en/firefox/addon/13233/)

---

### Post by lovinglinux on 2010-07-17
> **anutjob said:**
> [https://addons.mozilla.org/en/firefox/addon/13233/](https://addons.mozilla.org/en/firefox/addon/13233/)

Don't forget that extension hasn't been approved (thus not reviewed) by Mozilla yet, so is not recommended to use it. Mozilla will soon change it's policy in regard to experimental extensions, which will no longer be visible in the site unless from a direct link. This is to make sure all public extensions are safe to use. A couple of days ago [they discovered a malware on one of the experimental extensions](http://www.ubuntuforums.org/showthread.php?t=1530536). They scan all extensions for malware, but if the extension is not reviewed, then you can't be sure it is safe.

---

### Post by jackn on 2010-07-17
I appreciate the add-on reference, anutjob, but I agree with lovinglinux that it may not be safe.
To be honest, I also like toying with getting FF to behave, and clicking on FF to start each time, instead of an automatic launch, hasn't bothered me enough so far for me to despair.

OK, lovinglinux, tried your idea.

I've tried your script, as well as one of my own, inspired by yours, and here's the upshot:
when I run either script from within a session, no problem, FF starts.
When, however, I restart the session, or go all the way to a reboot, nada - nothing launches, and I'm left staring at the desktop...

To have either script run at startup, I used embraceubuntu.com's [advice]("http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/").
The terminal report upon running the update-rc.d script (suggested by embraceubuntu.com), which integrates a given script into several run levels, was just fine.

All of the above holds true for either your script, or the following one:
```
#!/bin/bash

ping -c 2 -w 300 google.com &&
firefox
```

I've tried an alternative script as I thought it would be nice to have a functional test of the connection before launching FF, as opposed to a set time delay.

I'm very grateful, lovelinux and anutjob.

What do you think?

---

### Post by lovinglinux on 2010-07-17
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **toolkit.networkmanager.disable** in the filter and double-click the resulting preference to set it as true. That will disable the automatic offline/online switcher.

More info [http://kb.mozillazine.org/Toolkit.networkmanager.disable](http://kb.mozillazine.org/Toolkit.networkmanager.disable)

I got this preference from that extension code, which seems to be safe to use.  Due the simplicity of the extension, it was about time to become approved. It has been developed since July 2009. But I'm not sure it will be approved by Mozilla some day, because it just changes a preference.

---

### Post by jackn on 2010-07-17
Have tried, didn't work.

When it is set to 'true', and FF is among the startup applications, it starts right off, though the wireless is not on yet.

Thank you kindly for your attention and help, lovinglinux.

---

### Post by jackn on 2010-07-22
Bump.

---

### Post by mike555 on 2010-07-22
This should work for Firefox too ;

to delay the startup of an app in the startup , use a command like ;
      
 by adding    bash -c "sleep 20:         to the command it sleeps for 20 seconds before starting . notice the spaces , and quotes (before sleep and after the command )  ....

     bash -c "sleep 20; /usr/bin/checkgmail"     for instance for checkgmail ......
   ==== put this Checkgmail text in the startup programs edit ====


  or ;

 putting   bash -c "sleep 20; /usr/bin/thunderbird"     in the startup list will start thunderbird 20 seconds after when you startup ... good to use with Thunderbirds add-on " firebird" , which can minimize Thunderbird to the top toolbar , letting it run and tell you when you have mail ...

---

### Post by jackn on 2010-07-22
Thank a lot for the answer, Mike.

Will you please tell me where exactly I should put this command?

---

### Post by mike555 on 2010-07-22
in System > Preferences > Startup applications > highlight Firefox (assuming it is already there -if not put it there ) in the command box put [   bash -c "sleep 20; /usr/bin/firefox"   ]  ... that should work and delay Firefox opening for 20 seconds .... set it to more if needed ..

---

### Post by jackn on 2010-07-22
It worked, Mike.

Thank you very very much...
I settled on 10 seconds of sleep, which gives the wireless enough time to set up, though I might have to give it a bit more time in the future.
It's pretty much instantaneous now, and no more annoying offline launches...

If you're game, I'd like to look at this more closely.

For one, it worked this time, but not earlier, when trying something similar, as your suggestion introduced the desired command with "bash -c"
```
bash -c "command"
```, 
whereas earlier, I just placed my command directly in the startup applications' menu item, without "bash -c"...
This is why I asked you where you wanted me to put it.

Then, I'm wondering why a different version of the command doesn't work.
I thought I'd try a solution which would condition FF launching on verification of the connection.
This way, there's no arbitrary setting of a time delay:
```
bash -c "ping -c 2 -w 300 google.com && /usr/bin/firefox"
```

This didn't work.
The problem seems somehow to lie with "&&". It's supposed to tell the next command to run only upon successful execution of the previous one.
Your ";", on the other hand, as obviously you know, simply tells the commands to run in the given order, regardless of the success of the first one.

As a result, I get FF online with ";" (the FF launch command runs, but doesn't pay attention to the "ping" command).
Or, I get no FF launch with "&&".
Somehow, the answer might be that "ping" fails.  
Yet, it gets plenty of time to manage.

Any ideas?

---

### Post by lovinglinux on 2010-07-22
I just realized my suggestion from post #5 is missing the "&&". I wasn't understanding why it wasn't working.

The correct script should be like this:

```
#!/bin/bash

sleep 3000 && firefox
```

That will work. You just need tweak the sleep time.

Sorry for that.

---

### Post by mike555 on 2010-07-22
Sorry , I don't know why it works , it just works (I'm not a programmer)

---

