---
title: "Firefox 3.5 Doesn't Open External Links In A New Tab"
date: 2009-07-23
forum: General Help
---

### Post by Mark76 on 2009-07-23
I was quite happily using the previous version (.3.0.11), when it suddenly decided to stop working.  So I removed it and installed 3.5 instead.

Unfortunately whenever I try to open a link from an email I get a new window instead of a new tab.  And I can't seem to find anyway to stop it (yes, I did look under the Tabs tab in Edit/Preferences)

---

### Post by nikhilk on 2009-07-23
> **Mark76 said:**
> Unfortunately whenever I try to open a link from an email I get a new window instead of a new tab.  And I can't seem to find anyway to stop it (yes, I did look under the Tabs tab in Edit/Preferences)

Does using a new, freshly created profile solve this?

---

### Post by Mark76 on 2009-07-23
Probably not

Besides, I don't want to creat a new profile.

---

### Post by nikhilk on 2009-07-23
> **Mark76 said:**
> Probably not

Besides, I don't want to creat a new profile.

That's OK. I was just trying to isolate the problem as I suspect a corrupt firefox profile.
I have seen many weird things happening due to a corrupted profile. Creating a fresh one and importing bookmarks and stuff from the previous one usually works.

---

### Post by Mark76 on 2009-07-23
Also, there doesn't appear to be any obvious way to do it.

I reinstalled 3.0. It seems to be working again.

I don't think the version of 3.5 in the repos is ready for primetime.

---

### Post by regala on 2009-07-23
> **Mark76 said:**
> Probably not

crystal ball or guts ?
besides if you're not willing to test anything that could pinpoint a problem, don't care to ask here.
Let me remind you of something important about profiles and Firefox: no guarantee that your profile won't be screwed when changing "major" versions like between 3.0.x and 3.5.x. So it is highly possible that it is not the root of the problem, but that your profile is not compatible.

---

### Post by lovinglinux on 2009-07-23
> **nikhilk said:**
> That's OK. I was just trying to isolate the problem as I suspect a corrupt firefox profile. I have seen many weird things happening due to a corrupted profile. Creating a fresh one and importing bookmarks and stuff from the previous one usually works.

Yep, profiles are usually the culprit and if you create new one and it works, then you know the problem resides in the profile.

> **Mark76 said:**
> Also, there doesn't appear to be any obvious way to do it.

Run the following command:

```
firefox -P
```

This will launch the profile manager.

You can also run this to create a profile from command-line.

```
firefox -CreateProfile **[COLOR="Red"]JoelUser[/COLOR]**
```

For a full list of Firefox commands, visit [https://developer.mozilla.org/en/Command_Line_Options](https://developer.mozilla.org/en/Command_Line_Options)


> **Mark76 said:**
> I don't think the version of 3.5 in the repos is ready for primetime.

Maybe not for you, but It works like a charm for me.

> **regala said:**
> crystal ball or guts ?
besides if you're not willing to test anything that could pinpoint a problem, don't care to ask here.
Let me remind you of something important about profiles and Firefox: no guarantee that your profile won't be screwed when changing "major" versions like between 3.0.x and 3.5.x. So it is highly possible that it is not the root of the problem, but that your profile is not compatible.

I agree. I strongly recommend making profiles backups regularly. See the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) for more information on profiles, backups and how to pinpoint and solve problems with profile corruptions.

---

### Post by VCoolio on 2009-07-23
Nevermind

---

### Post by CatKiller on 2009-07-23
> **Mark76 said:**
> Unfortunately whenever I try to open a link from an email I get a new window instead of a new tab.  And I can't seem to find anyway to stop it (yes, I did look under the Tabs tab in Edit/Preferences)

System &#8594; Preferences &#8594; Preferred Applications &#8594; Internet &#8594; Web Browser. Make the command

```
firefox-3.5 -new-tab "%s"
```

---

