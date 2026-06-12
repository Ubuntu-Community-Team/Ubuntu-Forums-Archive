---
title: "Thunderbird won't start after adding Firetray"
date: 2012-08-30
forum: General Help
---

### Post by kiwipenguin on 2012-08-30
Hi,
I'm relatively new to Ubuntu but learning fast and loving it.
I was trying to set up Thunderbird to start automatically (but minimised or running in the background) by installing the Firetray add-on.
Now Thunderbird won't open when I click on it in the launcher.
I can't get it to open so I can uninstall Firetray and try something else...

Ubuntu 11.10
Thunderbird 14 (I think)
Firetray 0.4.2

Any suggestions please?

PS: I would still like it to start automatically when I login, minimised, with new email notifications showing in the tray.

Thanks!

---

### Post by Habitual on 2012-08-30
My Firetray v0.3.2 didn't like Tbird 14 and I haven't tried the 0.4.2 version (namely b/c it doesn't show up when I look for updates to my addons...)
0.3.2 worked once, but successive (re)starts, it died a slow and painful death.
Tools > Addons > "incompatible" smth.

0.4.2 [here]("https://en-us.add-ons.mozilla.com/en-US/thunderbird/addon/firetray/?src=search") says "Works with                       Firefox 7.0 and later,             SeaMonkey 2.1 and later,             Thunderbird 7.0 and later". 

NOTE: I do NOT use the OS of your choice.
I am content to run Tbird 3.1.9 for this sole reason, I LOVE the message indicator in my notification area.

what does terminal >
```
thunderbird 
``` indicate about the addon?

---

### Post by Phugoid on 2012-08-31
Exact same issue here.

I installed Firetray yesterday and today Thunderbird doesn't open. The mail icon still turns blue when I receive a mail and a notification appears, so it is running, but the actual window will not open in order for me to view my mails, etc.

And of course, I can't remove Firetray as an add-on unless I can do that.

Trying to open Thunderbird from the terminal does nothing also.

---

### Post by Habitual on 2012-08-31
> **Phugoid said:**
> Exact same issue here.

I installed Firetray yesterday and today Thunderbird doesn't open. The mail icon still turns blue when I receive a mail and a notification appears, so it is running, but the actual window will not open in order for me to view my mails, etc.

And of course, I can't remove Firetray as an add-on unless I can do that.

Trying to open Thunderbird from the terminal does nothing also.

terminal >
```
thunderbird --safe-mode
```

---

### Post by Habitual on 2012-08-31
yesterday, for "grins and giggles" I installed Tbird14 in slackware, and installed the Firetray version 0.4.2.
Tbird would "start" but not be visible.
a terminal >
```
pidof -x thunderbird
``` had 2 processes.

I shoved it back in the hole it came out of and went back to 3.1.9 using v0.3.2

Tbird14 also re-arranged my tabs/buttons/ and menu placement within the program.

Upgrade? No thanks, it works fine as is.

---

### Post by Petro Dawg on 2012-08-31
Ok, having thunderbird starting up automatically & minimized sounds like a good idea, so this is how I did it....


Step 1:  Install "Minimize On Start and Close 1.3.2" add on for thunderbird

Step 2:  Select "minimize on start" in the extension's preferences

Step 3:  Create a start up script by creating an empty document in your home folder and name it ".thunderbird.sh"

Step 4:  Paste the following code into the document...
```
#!/bin/bash
sleep 10 && thunderbird;
```

Step 5:  Right click on .thunderbird.sh and select "Properties"

Step 6:  Click on permissions tab and select "Allow executing file as program"

Step 7:  Open "start up applications" from dash and click "Add"

Step 8:  Enter "Thunderbird" as Name and hit browse and find and select the .thunderbid.sh file you created earlier in your home folder.


Thunderbird should now start up minimized 10 seconds after your desktop loads.

---

### Post by kiwipenguin on 2012-09-04
> **Habitual said:**
> My Firetray v0.3.2 didn't like Tbird 14 and I haven't tried the 0.4.2 version (namely b/c it doesn't show up when I look for updates to my addons...)
0.3.2 worked once, but successive (re)starts, it died a slow and painful death.
Tools > Addons > "incompatible" smth.

0.4.2 [here]("https://en-us.add-ons.mozilla.com/en-US/thunderbird/addon/firetray/?src=search") says "Works with                       Firefox 7.0 and later,             SeaMonkey 2.1 and later,             Thunderbird 7.0 and later". 

NOTE: I do NOT use the OS of your choice.
I am content to run Tbird 3.1.9 for this sole reason, I LOVE the message indicator in my notification area.

what does terminal >
```
thunderbird 
``` indicate about the addon?
When I put the code:
thunderbird
or
thunderbird --safe-mode
into terminal, nothing happens...
Is that what you were wanting me to do..?

---

### Post by Habitual on 2012-09-05
> **kiwipenguin said:**
> When I put the code:
thunderbird
or
thunderbird --safe-mode
into terminal, nothing happens...
Is that what you were wanting me to do..?

Yes, exactly but stick with --safe-mode for now. :)
Terminal > 
```
whereis thunderbird
```
output please.

---

### Post by kiwipenguin on 2012-09-05
Hi Habitual, thanks for reply.
output from
whereis thunderbird

thunderbird: /usr/bin/thunderbird /etc/thunderbird /usr/lib/thunderbird /usr/share/man/man1/thunderbird.1.gz

thunderbird still not starting in safe mode:
thunderbird --safe-mode

---

### Post by Habitual on 2012-09-05
I'd open a terminal and type
```
mv ~/.thunderbird ~/.thunderbird.org
thunderbird &
```NOTE: This will reset all your Thunderbird accounts to NONE. AND you will have to re-install firetray.
You will have to test your Firetray that way, maybe add some trivial account and fire off an email to yourself to test Firetray....

---

### Post by kiwipenguin on 2012-09-06
Thanks for your help Habitual. That got it working again after restarting.

I don't think I'll re-install Firetray for now.

The "Minimize On Start and Close 1.3.2" add-on that Petro Dawg suggested does the job perfectly (and I only needed to follow steps 1&2). - thanks!

---

### Post by Habitual on 2012-09-06
Glad it worked out!

---

