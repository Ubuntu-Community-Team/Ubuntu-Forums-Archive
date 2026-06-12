---
title: "How do you remount a usb drive with nautilus in lynx?"
date: 2010-05-08
forum: General Help
---

### Post by ridetheteapot on 2010-05-08
After using "safely remove drive" on a usb drive automatically mounted (in lucid lynx) i no longer have the ability to remount that drive without cycling its power.

I don't know if it has anything to do with removing the "unmount" option from nautilus in favor of cleaning up menu.
Anyway I didnt see any forum posts on the issue ---



ps. 
anyone have trouble using a proprietary gfx driver (nvidia for me), a custom console resolution (specified by grub), and the splash screen - when trying to access the ctrl-alt-function tty's?
seems the resolution is all screwed up or something and i cant see the login prompt. disabling splash via grub fixed it fine (EDIT - did not fix it) , but is kind of ugly if it happens to everyone with that configuration.

---

### Post by TenPlus1 on 2010-05-08
To remount a flash drive click on the Places menu on your bar and select the greyed out drive, it remounts...

---

### Post by mc4man on 2010-05-08
you may need to build nautilus and revert this patch, otherwise 'safely remove' does power off the device making it unavailable till powered on. (either w/ power switch or removing and reinserting

( or do from cli 

>  * Add 16_hide_unmount.patch: Do not show Unmount when showing Eject/Safe
    removal. Having three menu entries (unmount/eject/safe removal) in a
    volume/drive menu entry is too confusing. Unmount only really makes sense
    for internal drives, for external ones it is pretty much a "geek" option.
    Geeks can use palimpsest or "unmount /media/foo" from the CLI if they
    really want to, for everyone else it is just an unintuitive and hard to to
    explain menu entry. (LP: #453072)

---

### Post by ridetheteapot on 2010-05-08
mc4man thanks i *might* try this, but i don't need the feature so much that i what to build a custom nautilus - might it be a pain to package correctly for ubuntu?
The other tip in the quote i'll use to workaround - maybe i'll just make a unmount script for nautilus actions.
And not that it matters here, but isn't ditching "safely remove" and keeping unmount the more versatile choice?

tenplus1 does that still work for you in lucid? i dont using a usb *flash drive* - but a few pata/sata -> usb converters, and a flash mp3 player - none of which can be remounted like that.

---

### Post by mc4man on 2010-05-08
> isn't ditching "safely remove" and keeping unmount the more versatile choice?

Possibly, though..
For instance here I have several usb hdd's, some have power buttons, 1 doesn't.
So when I use the safely remove on the one without the button it unmounts, ejects and powers it off which is very useful.
On 1 of the ones with a button for some reason it won't power off while the usb cord is connected - again s.r. is useful

I guess you could call yourself a corner case geek...

---

### Post by ridetheteapot on 2010-05-08
kk thanks again for the info, i'm gonna mark as solved. regardless which way they went, i like the clean up.

EDIT: 
TenPlus1, i don't know if this is what you originally meant, but i just realized that if you click the eject button in the nautilus "places" pane it uses the unmount action. you can then remount from there.

So sloppy, it must be an oversight, its not even listed as a workaround in the patch notes mc4man posted.

---

### Post by jorgemarmo on 2010-07-08
> TenPlus1, i don't know if this is what you originally meant, but i just  realized that if you click the eject button in the nautilus "places"  pane it uses the unmount action. you can then remount from there.that was very very helpfull, however I fear that this "bug" will be fixed soon, so I will not be able to unmount from nautilus...

has anybody figured how to add the "unmount" option again??

---

### Post by ridetheteapot on 2010-07-25
you can revert the patch as suggested earlier in the thread; or nautilus-elementary (a nicer looking version of nautilus) still uses the old 'sloppy' way of giving all the choices. ppa info @ [https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa](https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa)

---

### Post by Andrew_P on 2012-03-23
> **TenPlus1 said:**
> To remount a flash drive click on the Places menu on your bar and select the greyed out drive, it remounts...

It still shows in the Places > Computer view, but, *no*, it *is not* greyed out and *no*, it *does not* remount when one clicks on it. (Ubuntu 10.04.4 LTS "Lucid Lynx")

---

