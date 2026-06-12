---
title: "Google Chrome default icons verses Themes."
date: 2012-06-15
forum: General Help
---

### Post by irv on 2012-06-15
When I first installed Chrome Browser it had icons on the new tab. As soon as I clicked on themes in the settings there were gone. Chrome Browser in Windows works different, you can change themes and keep the icons but not in Linux.
The icons looked something like this:
[ATTACH]219752[/ATTACH]
Now they look like this since I clicked on themes.
[ATTACH]219753[/ATTACH]
I wanted to go back to the icons but for the life of me I can't figure out how to do it? Anyone have an idea how to do this?
It is not a matter of life and death, but I would like to do this.

---

### Post by irv on 2012-06-15
I ran Google Chrome in Pepperment I think it was an older version and it run the same as in windows. You can change the themes and it still keeps the icons
[ATTACH]219764[/ATTACH]
It doesn't act the same in Ubuntu 12.04. I just can get the icons back. Is anyone else running it in 12.04? And could you post a screen shot if you are keeping the icons? I am not sure what is going on here?

---

### Post by vasa1 on 2012-06-15
I'm not sure I understand your question, but you could always revert to the "default" theme by going to *Wrench*, *Settings*, *Appearance*, and then choose *Use GTK+ theme* or *Use Classic theme*.
One point to note is that the current theme, if it has been installed from the Web Store or elsewhere, will be deleted by doing so. If you want it back, you'll have to re-install it. This doesn't apply to the Classic theme.

(I use the GTK+ theme Setting).

I hope this comes even remotely close to what you were asking!

---

### Post by irv on 2012-06-16
> **vasa1 said:**
> I'm not sure I understand your question, but you could always revert to the "default" theme by going to *Wrench*, *Settings*, *Appearance*, and then choose *Use GTK+ theme* or *Use Classic theme*.
One point to note is that the current theme, if it has been installed from the Web Store or elsewhere, will be deleted by doing so. If you want it back, you'll have to re-install it. This doesn't apply to the Classic theme.

(I use the GTK+ theme Setting).

I hope this comes even remotely close to what you were asking!
The problem is no matter if I pick "Use GTK+theme" or "Use Classic theme" nothing changes. This is not the case in Windows or other distros, Just Ubuntu 12.04. I even uninstalled it and reinstalled it and it makes no difference.

---

### Post by vasa1 on 2012-06-16
> **irv said:**
> The problem is no matter if I pick "Use GTK+theme" or "Use Classic theme" nothing changes. This is not the case in Windows or other distros, Just Ubuntu 12.04. I even uninstalled it and reinstalled it and it makes no difference.

I'm not seeing the problem but I'm currently in an Xfce 4.10 session. I can install a different theme or use the default or use the GTK+ theme without any problem. I'll log out and see with Unity 3D.

BTW, uninstalling and reinstalling may not make any difference if you retain your profile (stored in ~/.config/google-chrome/Default) assuming there's a problem with something in your profile being corrupted.

---

### Post by vasa1 on 2012-06-16
Just checked. It works just fine in Unity 3D as well.

I suspect your profile is corrupted or some extension is causing a problem. Try with all extensions disabled. If no joy, and you want to check if your profile is corrupted, then:
[LIST]
[*]make sure Chrome isn't running, even background apps
[*]rename the Default folder to something else
[*]start Chrome; a new Default folder will be created; check if your problem is resolved
[*]if it is resolved, you can transfer a few files at a time from the renamed Default folder back to the new one.
[/LIST]

One more shot in the dark: are you using synch? If so, do you still have the issue with synch disabled?

---

### Post by irv on 2012-06-16
> **vasa1 said:**
> I'm not seeing the problem but I'm currently in an Xfce 4.10 session. I can install a different theme or use the default or use the GTK+ theme without any problem. I'll log out and see with Unity 3D.

BTW, uninstalling and reinstalling may not make any difference if you retain your profile (stored in ~/.config/google-chrome/Default) assuming there's a problem with something in your profile being corrupted.
Turn out to be a plugin called "Speed Dial". I disabled it and now I have the icons back. Glad I found this, it was driving me crazy. Thanks for all your help. I will mark this thread solved.

---

