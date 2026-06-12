---
title: "Maybe a dumb question, but...(keyboard shortcuts)"
date: 2009-07-27
forum: General Help
---

### Post by solwic on 2009-07-27
This might be a stupid question, but I can't figure it out.  If you right click on the trash can, you'll see that "Empty Trash" is one of your options, and the "E" in "Empty" is underlined.  

That denotes a keyboard shortcut, right?  If so, how do I use that?  I tried Control+E, Alt+E, etc...not working.  Windows has a similar concept, and I never figured out how to work that one, either.

So is that what the underlined "E" means?  If so, how can I use it?

Thanks!

Oh yeah...Ubuntu 9.04, if it matters.  :)

---

### Post by SlugSlug on 2009-07-27
> **iRun said:**
> This might be a stupid question, but I can't figure it out.  If you right click on the trash can, you'll see that "Empty Trash" is one of your options, and the "E" in "Empty" is underlined.  

That denotes a keyboard shortcut, right?  If so, how do I use that?  I tried Control+E, Alt+E, etc...not working.  Windows has a similar concept, and I never figured out how to work that one, either.

So is that what the underlined "E" means?  If so, how can I use it?

Thanks!

Oh yeah...Ubuntu 9.04, if it matters.  :)

i just right clicked my and hit a bog standard e  and it worked...

---

### Post by solwic on 2009-07-27
> **SlugSlug said:**
> i just right clicked my and hit a bog standard e  and it worked...

Ah so I have to right click?  Kind of defeats the purpose of a keyboard shortcut, if you have to use the mouse to make it functional.  

Thanks, though.  :)

---

### Post by SlugSlug on 2009-07-27
> **iRun said:**
> Ah so I have to right click?  Kind of defeats the purpose of a keyboard shortcut, if you have to use the mouse to make it functional.  

Thanks, though.  :)

well I did wonder why you would right click and then look for a shortcut for a menu entry...

am sure there would be a way to map your own shortcut to empty the trash

---

### Post by solwic on 2009-07-27
> **SlugSlug said:**
> well I did wonder why you would right click and then look for a shortcut for a menu entry...

am sure there would be a way to map your own shortcut to empty the trash

Well it wasn't so much to empty the trash as just utilizing all those shortcuts that are already programmed in.  I have a lappy, and I hate touchpads, so I'm learning all the nifty little keyboard tricks that I can.  

Although I would be curious as to how to map a keyboard shortcut to empty the trash...wonder how you'd do that....

---

### Post by SlugSlug on 2009-07-27
> **iRun said:**
> Well it wasn't so much to empty the trash as just utilizing all those shortcuts that are already programmed in.  I have a lappy, and I hate touchpads, so I'm learning all the nifty little keyboard tricks that I can.  

Although I would be curious as to how to map a keyboard shortcut to empty the trash...wonder how you'd do that....

I would guess...  system > pref > keyboard shortcuts > add new and the command sudo rm ~/.local/share/Trash/* -Rf

but i guess you might have to mod that if you delete stuff from more than one drive...  ?

:popcorn:

---

### Post by SlugSlug on 2009-07-27
or just hold down shift to bypass the trash can...

---

### Post by solwic on 2009-07-27
> **SlugSlug said:**
> or just hold down shift to bypass the trash can...

Holding down shift doesn't work for me (you do mean Shift + Del, right?), but I'll look into that keyboard shortcuts thing.  :)

---

### Post by SlugSlug on 2009-07-27
> **iRun said:**
> Holding down shift doesn't work for me (you do mean Shift + Del, right?), but I'll look into that keyboard shortcuts thing.  :)

yer shift + the delete key should say do you want to perm delete this stuff.

---

### Post by solwic on 2009-07-27
> **SlugSlug said:**
> yer shift + the delete key should say do you want to perm delete this stuff.

Doesn't do anything for me.  Wonder why?

---

### Post by CatKiller on 2009-07-27
> **iRun said:**
> This might be a stupid question, but I can't figure it out.  If you right click on the trash can, you'll see that "Empty Trash" is one of your options, and the "E" in "Empty" is underlined.  

That denotes a keyboard shortcut, right?  If so, how do I use that?  I tried Control+E, Alt+E, etc...not working.  Windows has a similar concept, and I never figured out how to work that one, either.

Those are menu shortcuts rather than straight keyboard shortcuts. So Alt+f &#8594; m would open the _F_ile menu and then select the E_m_pty Deleted Items entry. Similarly Alt+h &#8594; a would open the _H_elp menu and select the _A_bout entry.

Sometimes a keyboard shortcut is listed as well so, in GEdit for example, next to the _F_ile &#8594; _S_ave entry, it says Ctrl+S, telling you what the keyboard shortcut is for saving the file without using the menu.

---

### Post by SlugSlug on 2009-07-27
> **iRun said:**
> Doesn't do anything for me.  Wonder why?

maybe due to laptop keyboard they do crazy things when numlock / (other) is on...  dunno tho - I'd get a usb mouse for a fiver and be done with the touch pad

---

### Post by CatKiller on 2009-07-27
> **iRun said:**
> Doesn't do anything for me.  Wonder why?

To get the confirmation box, you need to have ticked the "Ask before emptying the Deleted Items folder or deleting files permanently" setting in the Behaviour &#8594; Wastebasket section of Nautilus' Preferences screen (or set the /apps/nautilus/preferences/confirm_trash GConf key, which is the same thing) otherwise the files are just quietly deleted.

---

### Post by solwic on 2009-07-27
> **CatKiller said:**
> Those are menu shortcuts rather than straight keyboard shortcuts. So Alt+f &#8594; m would open the _F_ile menu and then select the E_m_pty Deleted Items entry. Similarly Alt+h &#8594; a would open the _H_elp menu and select the _A_bout entry.

Sometimes a keyboard shortcut is listed as well so, in GEdit for example, next to the _F_ile &#8594; _S_ave entry, it says Ctrl+S, telling you what the keyboard shortcut is for saving the file without using the menu.

Ah, OK.  That makes sense.  Well, I don't see the sense in menu shortcuts - if you're going to use the mouse, use it - but what you're saying makes sense.  

Shame, really, that there aren't more keyboard shortcuts for common functions like emptying the trash.

In any case, thanks.  :)

---

### Post by CatKiller on 2009-07-27
> **iRun said:**
>  Well, I don't see the sense in menu shortcuts - if you're going to use the mouse, use it

That's right, you don't :)

It means that you can use any menu item **without** having to use the mouse, not just those for which a defined keyboard shortcut exists. Alt-F-T is remarkably quick to type, and doesn't involve the mouse at all.

---

### Post by solwic on 2009-07-28
> **CatKiller said:**
> That's right, you don't :)

It means that you can use any menu item **without** having to use the mouse, not just those for which a defined keyboard shortcut exists. Alt-F-T is remarkably quick to type, and doesn't involve the mouse at all.

But Ctrl+T - at least in Firefox - is much quicker, and doesn't use as many keys.  :P

In any case, what I think I'm looking for is a way to map custom shortcuts.  I like the idea of emptying the trash via the keyboard, but so far can't find a way to do it.  I'm sure there is a way, even if I don't know it, yet.  :)

---

### Post by hessiess on 2009-07-28
> **iRun said:**
> Well it wasn't so much to empty the trash as just utilizing all those shortcuts that are already programmed in.  I have a lappy, and I hate touchpads, so I'm learning all the nifty little keyboard tricks that I can.  

Although I would be curious as to how to map a keyboard shortcut to empty the trash...wonder how you'd do that....

Try using a tiling WM.

---

### Post by CatKiller on 2009-07-28
> **iRun said:**
> But Ctrl+T - at least in Firefox - is much quicker, and doesn't use as many keys.  :P

True, but how would you get a Print Preview just using the keys?
>  In any case, what I think I'm looking for is a way to map custom shortcuts.  I like the idea of emptying the trash via the keyboard, but so far can't find a way to do it.  I'm sure there is a way, even if I don't know it, yet.  :)

Do you use Compiz?

---

### Post by solwic on 2009-07-29
> **CatKiller said:**
> 
Do you use Compiz?

Yeah.

---

### Post by CatKiller on 2009-07-29
Then install and run compizconfig-settings-manager and look at the Commands plugin. Arbitrary shortcuts for arbitrary commands.

---

### Post by solwic on 2009-07-29
> **CatKiller said:**
> Then install and run compizconfig-settings-manager and look at the Commands plugin. Arbitrary shortcuts for arbitrary commands.

Not bad.  I didn't know that existed.  Of course, it begs the question, "What's the command to empty the trash?"  

I'll go look that up right now.  

Thanks.  :biggrin:

---

