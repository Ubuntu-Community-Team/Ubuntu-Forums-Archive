---
title: "Have to type twice to login at times..."
date: 2009-11-30
forum: General Help
---

### Post by emigrant on 2009-11-30
hi all ;)

at times i have to type twice to loggin even though i type the correct username password,
this happens for almost all the account in my system.

any suggestions... 

thank you very much :popcorn:

---

### Post by ahounsome on 2009-11-30
I would back up my files and re-install the OS. A bit drastic but quicker than fiddling around

---

### Post by emigrant on 2009-11-30
> **ahounsome said:**
> I would back up my files and re-install the OS. A bit drastic but quicker than fiddling around
so far i hate karmic very much.
now im in a dilemma to choose between jaunty and hardy.

---

### Post by StuartN on 2009-11-30
> **emigrant said:**
> at times i have to type twice to loggin even though i type the correct username password,
this happens for almost all the account in my system.

I think that for many environments it is completely inappropriate to display a list of valid usernames for all and sundry to view, but that is another issue.

You can disable this from System->Administration->Login screen and either change to from "Theme with faces" to "Theme", or untick all users under "Users". This means you type both the username and the password. It might fix your problem because it restores the old login behaviour.

---

### Post by emigrant on 2009-11-30
> **StuartN said:**
> I think that for many environments it is completely inappropriate to display a list of valid usernames for all and sundry to view, but that is another issue.

You can disable this from System->Administration->Login screen and either change to from "Theme with faces" to "Theme", or untick all users under "Users". This means you type both the username and the password. It might fix your problem because it restores the old login behaviour.

man that is not available with karmic :(

---

### Post by StuartN on 2009-11-30
> **emigrant said:**
> man that is not available with karmic :(

I see what you mean - I have a mixture of 9.04, upgrades and clean installs here, so they all behave differently!

I haven't tried it yet, but apparently you can open gconf-editor (or Applications->System tools->Configuration editor) and set **/apps/gdm/simple-greeter/disable_user_list** to **true**, which should revert to the old behaviour.

---

### Post by emigrant on 2009-11-30
thanks for you input StuartN,
but that didn't work :(

---

### Post by StuartN on 2009-11-30
> **emigrant said:**
> thanks for you input StuartN,
but that didn't work :(

{RANT}Yes, the designers are really conscious of the risks posed by users, even if they are not conscious of the risks posed by prying eyes. Displaying a list of all users is not sensible, it is stupid even as a default behaviour. It is stupid too making it difficult to reset. It is at least as block-headed as the display of clear-text passwords in Seahorse / gnome keyring. Both are fine for a child's machine, but are a ridiculous security risk anywhere else.{/RANT}

There appears to be no graphical access to this parameter, and a method that works (which I have tried on a fresh Ubuntu 9.10 install) is to open a terminal and:

```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
--type bool --set /apps/gdm/simple-greeter/disable_user_list true
```

and setting it back to false will reverse this edit, so save a link or copy of the command somewhere.

---

### Post by emigrant on 2009-12-01
thank you very much StuartN, it worked well and looks much better now :popcorn:

---

### Post by StuartN on 2009-12-09
> "It was discovered that GRUB 2 did not properly validate passwords. An attacker with physical access could conduct a brute force attack and bypass authentication by submitting a 1 character password." - [http://www.ubuntu.com/usn/USN-868-1](http://www.ubuntu.com/usn/USN-868-1)

So for a while there people have been riding bareback - username on display and no password!

---

