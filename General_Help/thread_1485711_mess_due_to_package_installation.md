---
title: "mess due to package installation"
date: 2010-05-17
forum: General Help
---

### Post by iamronen on 2010-05-17
Dear Friends,

Yesterday I tried to get the GUIPDFTK package working as instructed here: [http://www.jlaforums.com/viewtopic.php?t=5563333](http://www.jlaforums.com/viewtopic.php?t=5563333)

I installed this package (and a few dependency packages that were missing - I think all from the libgtk1.2 branch) as instructed:
[http://packages.ubuntu.com/dapper/libgdk-pixbuf2](http://packages.ubuntu.com/dapper/libgdk-pixbuf2)

It has messed up my gnome and reverted it to what lools like an outdated GUI. 

[LIST]
[*]I have tried to remove the packages I installed - but I don't know if I got them all - that didn't help.

[*]I took this opportunity to upgrade to 10.04 - and that didn't help either.
[*]I tried numerous clean up procedures - but they didn't help either (at least not with this problem).
[/LIST]
The attached screenshots are what I am currenty looking at.

I'd appreciate any help you can offer.

All Things Good
Ronen

---

### Post by ryan858 on 2010-05-17
You may have to completely purge gnome altogether and reinstall it... this can be done with:

[B]$ sudo apt-get purge gnome
$ sudo apt-get update && sudo apt-get install gnome
[/B]
You should do this from the recovery shell, with networking enabled.

However, I'm not entirely sure this is a good idea... Wait for some confirmation before you go through with that...

Can we get some confirmation please guys?

---

### Post by iamronen on 2010-05-17
Thank you for the quick reply Ryan.

Would this in any way compromise other things such as additional applications that I've installed and/or personal data related to these applications?

---

### Post by pastalavista on 2010-05-17
I think, rather than reinstalling gnome, you should first try deleting the .config directory from your /home/username directory and logging out/in. You should see a default desktop again. Use Synaptic's Custom Filters to identify and fix missing or broken packages.

---

### Post by ryan858 on 2010-05-17
You might lose settings that you've saved in gnome, and customizations, etc. But it shouldn't affect other programs not related to gnome, or any of your personal files.

You can try using just *apt-get remove* instead of *purge*, if you want to keep the gnome settings and configurations. But it may not get the issue that's affecting the GUI and making it 'old-style'...


Edit: Delete .config first and see what happens, that seems like the safe bet here.

---

### Post by iamronen on 2010-05-17
I tried deleting the .config dir bu that didn't help. 

Also - the login screen itself also looks compromised - so it's probably something that goes beyond my personal preferences.

So I guess it's purge and reinstall time :) I hope to see you safely on the other side!

---

### Post by iamronen on 2010-05-17
Though I do see it - apt-get indicates that gnome is not installed.

When I tried installing it I got this:

The following packages have unmet dependencies:
  gnome: Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages

???

---

### Post by 3rdalbum on 2010-05-17
Oh no!

In future, don't follow HOWTOs or install packages for old versions of Ubuntu. The HOWTO seems to be for Ubuntu 8.04, and you've installed packages from Ubuntu 6.06 (that's what "dapper" refers to in that URL).

Linux moves so quickly that it's like trying to install some bits of Windows 98 onto Windows Seven - you're likely to break things.

---

### Post by iamronen on 2010-05-17
well now I know that :)

Question is what now?

---

### Post by iamronen on 2010-05-17
In trying to install Gnome I am now caught between two dependencies that don't want to live together: epiphany-extensions & swfdec-mozilla

---

### Post by ryan858 on 2010-05-17
Well, apparently the official Gnome package isn't installed by default... at least in 10.04.

It just uses the gnome libs and gnome utilities and stuff, but not the actual gnome package...

---

### Post by iamronen on 2010-05-17
I don't know what was wrong or if it's totally corrected. But for the record:
[LIST]
[*]The relevant package in 10.04 seems to be gnome-desktop-environment
[*]after installing it - the looks did not change - until I changed the theme appearance settings. It seems there a "custom theme" was selected - though I never selected one.
[/LIST]

---

### Post by ryan858 on 2010-05-17
I'm sorry for leading you down the wrong way. I had no idea it would make such a mess of things to reinstall gnome, and didn't know that Ubuntu uses a custom, non-standard gnome. That *apt-get install gnome *probably just messed it up. But glad to see you got it working again. Wow, just changed the theme.... Why didn't I think of that?

---

### Post by iamronen on 2010-05-18
Ryan - your advice had no detrimental affects (it did nothing to the system). Your attention helped me look in the right direction. Together we have generated new knowledge :) how great is that?

Thanks for being there when I needed help.

---

