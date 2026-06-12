---
title: "Upgrading from 10.10 to 11.4 - upgrade manager does not show available upgrade"
date: 2011-05-14
forum: General Help
---

### Post by appelsin on 2011-05-14
Hello Friends,

I am currently on 10.10 and want to upgrade to 11.4

I tried to follow the steps for upgrade.

I.e. Go to System- Administration - Update Manager and then checked for updates.

I was expecting the update manager to inform me that a new version is available for upgrading.

However, the update manager draws a blank. 

Just to be sure, I also checked my current version ( System - About Ubuntu) and I can confirm that my version is 10.10.

I could ofcourse try upgrading from a CD or USB. But I would appreciate your advice on why the update manager is not responding.:confused:


Thank you !
Best Regards

---

### Post by linuxuser12345 on 2011-05-14
Go to the Ubuntu Software Center, then click "Edit"..... "Software Sources".
Click on the "Updates" tab. Go down to the bottom where it says "Release upgrade". Click on the drop down menu, and make sure it is set to "Normal releases". 

You should be good to go! :)

---

### Post by linuxuser12345 on 2011-05-14
Also, on the new 11.04 LiveCD, there is an "upgrade" option you can choose from when installing. This is probably the fastest way to go!

---

### Post by JOHNNYG713 on 2011-05-14
bottom left of update manager, settings button, will open software sources windoe under updates you are probably set to never, set it to normal releases, besure to have a "natty" CD handy in case your upgrade gets botched ! also have a maverick CD as well if you want to go back ! Remember to back up your important info before doing anything !

---

### Post by appelsin on 2011-05-14
Dear Friends,

Thanks for your replies.

The 'Release Upgrade' was already set to 'Normal Releases'.  I had already chked on that ( sorry I didnt mention it in my first post).

Any more thoughts on this ( apart from installation from CD/USB).

Thanks to all !

Best Regards

---

### Post by JOHNNYG713 on 2011-05-14
do you have all the normal software boxes ticked ! and you are all up to date !?:confused:

---

### Post by appelsin on 2011-05-14
> **JOHNNYG713 said:**
> do you have all the normal software boxes ticked ! and you are all up to date !?:confused:

Yes Sir ! :confused:

All normal s/w are ticked ! I just double checked on it and all are up to date.

Best Regards

---

### Post by JOHNNYG713 on 2011-05-14
have you clicked the check button?,, before going any further, becuz we can change you sources to natty but I would like to NOT force it !

---

### Post by appelsin on 2011-05-14
> **JOHNNYG713 said:**
> have you clicked the check button?,, before going any further, becuz we can change you sources to natty but I would like to NOT force it !

Hi again - Yes, the 'Check for updates' is already checked.

Thanks.
Best Regards.

---

### Post by JOHNNYG713 on 2011-05-14
OK One more thing have you tried changing repos from main to United States,(or Vies versa) or search for the best server ? In up date manager !? and reload?

---

### Post by shinobinomono on 2011-05-15
Hi All,

I Am New to Linux and Ubuntu, however I may be able to suggest a solution :)

Type 

**"Alt + F2"**

type in the command 
[B]
update-manager -c -d [/B]

into the box and click 

**Run**

The update manger should now show the 11.4 update option.

Enjoy ;)

Cher!

---

### Post by appelsin on 2011-05-21
> **JOHNNYG713 said:**
> OK One more thing have you tried changing repos from main to United States,(or Vies versa) or search for the best server ? In up date manager !? and reload?

Dear Sir,

Thank you very much for your time and advice. I was away for a few days. But when I returned and switched on my Ubuntu, the system itself prompted me to upgrade ! And I can also see the upgrade facility in the update manager now.

Not sure which particular thing that I did, made this possible. But hey, I am happy that the update manager finally responded !

Btw, after reading all the reviews of the 11.04 version, I have decided to stick to 10.10 for the present.

You have been very helpful. Thank you.

Best Regards,

---

### Post by appelsin on 2011-05-21
> **shinobinomono said:**
> Hi All,

I Am New to Linux and Ubuntu, however I may be able to suggest a solution :)

Type 

**"Alt + F2"**

type in the command 
[B]
update-manager -c -d [/B]

into the box and click 

**Run**

The update manger should now show the 11.4 update option.

Enjoy ;)

Cher!

Hi - The update manager is working now ! I did many things to make it work and I am not sure which one actually worked.

Thanks anyways for your time and advice.

Best Regards

---

### Post by mörgæs on 2011-05-21
Good, please mark the thread 'solved'.

---

