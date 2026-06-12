---
title: "How can I save xinput settings"
date: 2011-04-22
forum: General Help
---

### Post by gb1138 on 2011-04-22
Can someone please tell me how I can save xinput settings?  I'm running Peppermint Linux on an eeepc 701. After a few weeks, I've finally figured out which settings to configure with the xinput command to get my touchscreen working correctly.  However, when restart the netbook all the settings are lost and I have to reconfigure each time.  I've found threads saying to save settings in xorg.conf file, but apparently my system doesn't have this file. Any help would be much appreciated...

Thanks,
gb

---

### Post by tredegar on 2011-04-22
You don't say what the commands are, but put the commands in a file. Call the file **fix-xinput**

Make it look like this:```
#!/bin/bash
# Wait for the desktop to finish loading
sleep 5
xinput *whatever you need*
xinput *whatever more you need*
```
Make the file executable: ```
chmod +x fix-xinput
```
Add it to System Preferences Autostart

It will be run each time you login.

---

### Post by gb1138 on 2011-04-22
Hi Tredegar,

Thanks for your reply.  I've created the following file with nano:

#!/bin/bash
# Wait for the desktop to finish loading
sleep 5
xinput set-int-prop 10 280 8 1
xinput set-int-prop 10 278 8 1, 0
xinput set-int-prop 10 279 32 86 1969 166 1903


I saved it as fix-xinput, then I did; chmod +x fix-xinput.

That didn't come up with an error.  However when I type in "fix-xinput" it just says "command not found"?  

Also Peppermint linux doesn't have the  System Preferences Autostart, but I found:

/etc/xdg/lxsession/Peppermint/autostart

and modified at the end of the file:

@fix-xinput

it seemed like that was the syntax since everything else in the file looked like that (with the @ symbol).

Anyway,  that didn't work either..  Any thoughts?


Thank you again for your reply :)
gb

---

### Post by gb1138 on 2011-04-22
Hi Tredegar,

I figured it out.  I googled how to make a file executable and tried putting a ./ in front of the fix-xinput file.  It works great now :).

Thanks for your help, I would never have gotten this to work without your help.  Truly appreciated!

Best,
gb

---

### Post by tredegar on 2011-04-22
> I would never have gotten this to work without your help.
Of course you would. It might have taken a moment longer though. But you are learning fast.

**echo $PATH** will tell you the directories linux will search to find commands. If your command isn't in the PATH then you have to specify the path to it exactly: **/home/gb1138/name** or **~/name** otherwise you'll get "Command not found".

Pleased you have a solution to your problem.

Have fun with linux.

---

