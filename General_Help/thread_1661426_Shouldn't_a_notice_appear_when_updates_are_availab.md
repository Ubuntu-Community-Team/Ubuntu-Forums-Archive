---
title: "Shouldn't a notice appear when updates are available?"
date: 2011-01-06
forum: General Help
---

### Post by nrundy on 2011-01-06
I always manually check Update Manager and there are updates, but I never received any kind of notice indicating such. I thought some sort of popup or notice was supposed to appear in the panel or something to alert me that updates are available? Am I mistaken? Is there a setting I need to activate be alerted that updates are available?

---

### Post by jesse.melhuish on 2011-01-06
I'm not 100% sure, but here's a suggestion.  Go to System > Administration > Update Manager.  When the window pops up, click the "Settings" button in the lower left.  Go to the "Updates" tab, and set the box for how often to check for updates to daily.  That may not be it, but it's worth a try.

---

### Post by wilee-nilee on 2011-01-06
As of the Jaunty release the update manager was made to show only security updates. 
[http://ubuntuforums.org/showthread.php?t=1462608](http://ubuntuforums.org/showthread.php?t=1462608)

---

### Post by nrundy on 2011-01-06
> **jesse.melhuish said:**
> I'm not 100% sure, but here's a suggestion.  Go to System > Administration > Update Manager.  When the window pops up, click the &quot;Settings&quot; button in the lower left.  Go to the &quot;Updates&quot; tab, and set the box for how often to check for updates to daily.  That may not be it, but it's worth a try.

 Yeah, I'm on daily updates. Thanks though.

---

### Post by nrundy on 2011-01-06
> **wilee-nilee said:**
> As of the Jaunty release the update manager was made to show only security updates. 
[http://ubuntuforums.org/showthread.php?t=1462608](http://ubuntuforums.org/showthread.php?t=1462608)

 This prolly explains it. So I can expect some sort of notice if/when a security update is released? It will notify my automatically? Do you know what it will do--is a popup issued or a panel icon will appear or something in the notification area?  Thanks for letting me know about the change from Jaunty.

---

### Post by wilee-nilee on 2011-01-06
> **nrundy said:**
> This prolly explains it. So I can expect some sort of notice if/when a security update is released? It will notify my automatically? Do you know what it will do--is a popup issued or a panel icon will appear or something in the notification area?  Thanks for letting me know about the change from Jaunty.

Yeah, if you change it you will see a icon in the notification area, after the computer runs its auto checks.

You can change it in the gconf-editor under apps-update manager just untick the manager.

To get to gconf just hit alt-f2 then type in gconf-editor, and hit run click on apps, scroll down to update manager.

---

### Post by Krytarik on 2011-01-07
Thanks for the info about the only-security-updates thing, also started to wonder about this.

To enable the Update-Notifier-Icon in the Notification-Applet in the panel:

```
gconftool-2 --set --type bool /apps/update-notifier/auto_launch false
```

---

### Post by nrundy on 2011-01-08
krytarik, where do I type that command--in a Terminal? Is there a GUI way to make this setting?  I had a security update yesterday. A notifier just popped up right in the middle of a document I was trying to write. I'm thinking about setting it to just show a notification icon in the panel.

---

### Post by kostkon on 2011-01-08
> **nrundy said:**
> krytarik, where do I type that command--in a Terminal? Is there a GUI way to make this setting?  I had a security update yesterday. A notifier just popped up right in the middle of a document I was trying to write. I'm thinking about setting it to just show a notification icon in the panel.
Yes, there is. Press ALT+F2 and give
```
gconf-editor
```

---

### Post by Krytarik on 2011-01-08
> **nrundy said:**
> krytarik, where do I type that command--in a Terminal? Is there a GUI way to make this setting?  I had a security update yesterday. A notifier just popped up right in the middle of a document I was trying to write. I'm thinking about setting it to just show a notification icon in the panel.
Yes, just enter it in a terminal, or paste it in the Alt+F2 dialog.

If you want to set it in gconf-editor, you have to browse down the path and add the option as a "New Key", because it's not there by default.

---

### Post by nrundy on 2011-01-10
Is there a GUI way to do it? (So I know what options are available to me)

---

### Post by Krytarik on 2011-01-10
> **nrundy said:**
> Is there a GUI way to do it? (So I know what options are available to me)
That would be the 'gconf-editor'-way we described.

---

### Post by nrundy on 2011-01-11
> **Krytarik said:**
> Yes, just enter it in a terminal, or paste it in the Alt+F2 dialog.

If you want to set it in gconf-editor, you have to browse down the path and add the option as a "New Key" because it's not there by default.

 Krytarik, am I mistaken? It doesn't look like I have to add a new key.

Is this the right item--do you have this in your box too? 
1. Run gconf-editor 
2. apps > update-notifier > auto_launch (untick)

---

### Post by Krytarik on 2011-01-12
> **nrundy said:**
> Krytarik, am I mistaken? It doesn't look like I have to add a new key.

Is this the right item--do you have this in your box too? 
1. Run gconf-editor 
2. apps > update-notifier > auto_launch (untick)
You are obviously right, I've checked this in gconf-editor. Since there is a description, the key must be there by default. I tought I haven't seen it the time I've set those option.

Anyway.

---

