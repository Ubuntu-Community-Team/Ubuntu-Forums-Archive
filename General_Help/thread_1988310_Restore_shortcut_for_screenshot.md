---
title: "Restore shortcut for screenshot"
date: 2012-05-27
forum: General Help
---

### Post by Paddy Landau on 2012-05-27
It used to be that I could open the Screenshot program, and whatever settings I made (e.g. whether or not to include the window border) would be used when taking a screenshot with Alt-Print.

In trying to get this to work (it doesn't), I have lost my shortcut for Alt-Print.

When I try to reset it, it registers Mod2+Alt L instead of Alt-Print (see screenshot). Unfortunately and bizarrely, this maps to the Alt key; so whenever I press the Alt key, a full-screen screenshot is taken!

[attach]218782[/attach]

How can I restore my Alt-Print shortcut to the screenshot, please.

---

### Post by mc4man on 2012-05-27
You didn't mention what session you're using ??

To some extent keyboard bindings are a bit of a mess - in this case you'll notice there are 2 each for the screenshot ones
(one set may be compiz, the other metacity or one compiz/metacity, the other gnome, personally give up trying to figure out.

In the future I strongly advise when messing with keyboard binding set up a new user & test/fool about there, then when you get what you want/need apply to your 'real' user account.

Maybe try this - 
open home folder > view > show hidden files.
Browse to .gconf > apps & delete the "metacity" folder (or move to trash
Then log out/in & see

---

### Post by Paddy Landau on 2012-05-27
I am using Unity 3D. But I thought that the shortcuts carried over between different types of session — I know that my Custom Shortcuts work in both Unity 3D and Gnome Classic (No Effects).

I am hesitant to delete the current settings, as it will delete all of my customisations. However, I did find in gconf the following:

/schemas/apps/metacity/keybinding_commands > command_screenshot
/schemas/apps/metacity/keybinding_commands > command_window_screenshot
/apps/metacity/keybinding_commands > command_screenshot
/apps/metacity/keybinding_commands > command_window_screenshot

Looking into it further, I discovered that the setting for Unity 3D is in CompizConfig Settings Manager > General > Gnome Compatibility > Commands, and I could set the key binding there (it was not straightforward; I had to set it to Print and then add Alt).

Via this, I also discovered the answer to your question: The top two screen-shot bindings in Keyboard Shortcuts are Compiz and the bottom two are Metacity.

My Metacity ones are still disabled, and I don't know how to re-enable them; but that's not important. I log into Gnome Classic (No Effects) only occasionally for a program that doesn't work in Unity (and for which a bug has already been raised). At least my normal screen-shot is working again!

Thank you for your prompting. I shall mark this thread as solved.

---

### Post by vasa1 on 2012-05-27
Stupid question but what is the Mod2 key in your screenshot?

---

### Post by Paddy Landau on 2012-05-27
> **vasa1 said:**
> Stupid question but what is the Mod2 key in your screenshot?
I wondered that myself. That's what appeared when I pressed Alt-Print, and in practice it actually translates to the Alt key by itself.

---

### Post by vasa1 on 2012-05-27
> **Paddy Landau said:**
> I wondered that myself. That's what appeared when I pressed Alt-Print, and in practice it actually translates to the Alt key by itself.
What fun. And in Xfce 4.10 at least, the control key is shown as "primary".

But then looking at the combination, what exactly do you have to do if Mod2 = Alt and the second key is Alt L? That means Mod2 refers specifically to Alt R? And so you invoke what you want by pressing both Alt L and Alt R? Confusing stuff. And then where does the HUD fit in?

---

### Post by mc4man on 2012-05-27
At least here the top 2 are tied to both metacity & compiz > gnome compatability. The bottom 2 haven't pursued yet.
Using a new user account

Can be seen in series of screens
screen 1 - diasbled all 4, notice that in gconf the metacity entries removed

screen 2 - manually set back to default for screenshot (Print) by clicking on little x icon in ccsm > gnome com. >.. , notice it re-enabled the top option in "Keyboard" & auto added to gconf > apps > metacity > .. "Print"

screen 3 - manually entered in gconf > metacity > ... (<Alt>Print). Notice that re-enabled 2nd option in "Keyboard >..", & also enabled in ccsm > gnome com...

Now, (maybe), to see how to re-enable bottom 2 options though not needed here

---

### Post by mc4man on 2012-05-27
So the 3rd listing is easy to set back, used gnome-shell where there are only 2 listing, set to "Print"

The 4th one is not too easy - Alt+Print produces Alt L

The 4th one can be set to anything else - so used at random Ctrl+Alt+N, then looked everywhere for where is that setting saved ??
Can't find any visible place
(ultimately doesn't matter in a ubuntu session, only the top 2 are relevant

Edit: the 4th one is in dconf/gsettings, somewhere. Removed ~/.config/dconf/user & all is back to where it started by defaut - screen 2

---

### Post by Paddy Landau on 2012-05-27
Yeesh. Who in heck decided this level of complexity? :rolleyes:

> **vasa1 said:**
> But then looking at the combination, what exactly do you have to do if Mod2 = Alt and the second key is Alt L? That means Mod2 refers specifically to Alt R? ...
No. I have only one Alt key, on the left side of the keyboard. It was just a mess — a bug, in my mind.

> **mc4man said:**
> At least here the top 2 are tied to both metacity & compiz > gnome compatability.
Different from mine, then, unless I have misunderstood what I have been seeing.

> **mc4man said:**
> ... little x icon in ccsm > gnome com. >
#-o I forgot about the reset-to-default button.

Thanks for all the input.

---

