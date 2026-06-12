---
title: "Setting GRUB default boot"
date: 2010-06-28
forum: General Help
---

### Post by acrosome99 on 2010-06-28
Howdy, All,

I'm trying to configure GRUB to boot XP preferentially- my wife insists.  Having looked up the GRUB manual I see that I can set this using the default command.

The problem is, when I go to my grub command line default is not a recognized command.  If I hit TAB for a list of commands, it isn't there.

Any ideas?

I think I'm using some 0.9x version of GRUB, since the partitions etc seem to be numbered starting at 0, not 1.

While I'm at it, I was just going to play around and figure this out, but: the menu interface lists five versions of Ubuntu (all those weird kernel variations) then XP.  So would XP be default 1 or default 5?

Thanks.

---

### Post by oldfred on 2010-06-28
Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

---

### Post by acrosome99 on 2010-06-28
Damn.

That was almost too easy...

Thanks!

Still, I'm puzzled why I RTFM and was told to do something that isn't an option.  Or did I mis-read the bit about the "default" command?  Do I have some obscure offshoot variant of GRUB?  What?

---

### Post by oldfred on 2010-06-28
With old grub you set a number that is the boot stanza of windows and it will boot that. In my old grub menu I had added a spacer line ( root =) and set the count to that line and wondered why it did not boot. Some with old grub moved the stanza to first but inside the magic area and when a new kernel was downloaded it would be deleted.

With grub2 you can use a number, or the exact title.

---

