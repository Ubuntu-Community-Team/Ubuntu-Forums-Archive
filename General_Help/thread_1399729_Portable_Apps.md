---
title: "Portable Apps?"
date: 2010-02-06
forum: General Help
---

### Post by user2037 on 2010-02-06
Ubuntu doesn't always have the latest versions of apps. And at times I move between Ubuntu installations. 

It'd be nice if there were portable editions of popular software like Firefox.

It seems possible to get close with a lot of sym-links and the 'static' binaries offered by many projects. Yet truly portable editions shouldn't use external folders by default.

Does anyone know of a effort similar to PortableApps.com yet for Ubuntu?

---

### Post by lovinglinux on 2010-02-06
No, but I know a possible solution.

[LIST=1]
[*]Download the binaries from Mozilla and extract to your removable drive.
[*]Close Firefox, then open Firefox Profile Manager and create a new profile for the portable installation. Give a name like "Portable". You can do that with the following command:

[*]```
firefox -P
```

[*]Close Firefox again, then go to ~/.mozilla/firefox and find the folder with portable in the name. Move it to your removable drive.

[*]Open the file profiles.ini inside ~/mozilla/firefox and change the path of the portable profile to point to the folder on the removable drive. Copy the portable profile settings from the profiles.ini and add it to other profiles.ini of every machine/user/Ubuntu you want to use it.
[/LIST]

I never tested this setup, but it should work, at least in theory :)

The only drawback I can see is that you need to add the path to the correct profile on every machine you plan to use it.

---

