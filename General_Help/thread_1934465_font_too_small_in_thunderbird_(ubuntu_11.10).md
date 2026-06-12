---
title: "font too small in thunderbird (ubuntu 11.10)"
date: 2012-03-02
forum: General Help
---

### Post by ruthlazkoz on 2012-03-02
Hi,

please, can anyone help me change the default font in thunderbird under ubuntu 11.10?
It's far too small for my confortability.

Thanks,

Ruth

---

### Post by deeminter on 2012-03-02
Open the Preferences for Thunderbird.
Select Composition 
General tab 
Select the Font you desire and the size.
Close the Preferences.

If you are needing to change the default fonts for the display:

Open the Preferences for Thunderbird.
Select Display
Formatting tab
Select the Font you desire and the size.
Close the Preferences.

Hopefully this will assist you.

Dee Minter

---

### Post by ruthlazkoz on 2012-03-02
Thanks, perhaps I should have been more specific. I tried those myself
but they do not change the font used to for instance listing the folders
or listing the mails in each folder. Those are the fonts I would like to change.

---

### Post by pqwoerituytrueiwoq on 2012-03-02
run this command
```
gedit ~/.thunderbird/`ls ~/.thunderbird/ |grep .default`/chrome/userChrome.css 
```put this in there and save and restart Thunderbird
```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
tree > treechildren {
 font-size:24px!important;
}
```Change the 24 as necessary that should be about twice the default font size

---

