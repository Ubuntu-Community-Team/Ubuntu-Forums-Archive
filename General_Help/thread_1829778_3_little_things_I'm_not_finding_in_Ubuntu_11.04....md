---
title: "3 little things I'm not finding in Ubuntu 11.04..."
date: 2011-08-20
forum: General Help
---

### Post by Sp3ctre18 on 2011-08-20
Hi everyone. After having had a chance to try out Ubuntu for not more than a few days something like 5 years back, I'm glad to finally be back and actually try it out for everyday use. :)

Couple things I'd like some help with if you please; I've already googled and searched these forums and can't find anything or anything that works.

If it matters, I'm using Gnome. Unity doesn't work for me (I see my vid card is too old and not supported).

**1. Delete Confirmation: **IIRC, I think Mac is like this? (That'll be my next OS to try out, haha.) I hit the delete key and the file goes straight to trash. Admittedly, that's nice sometimes, but not always. In Windows you can pick either one; confirm send to recycle bin, or send straight to recycle bin. ONCE AT recycle bin is a whole other step of having confirmation or not.

I'd like confirmation. One of my keyboards has a huge delete key, sometimes I type in the dark...whatever, we all have our reasons. Being able to hit cancel or ESC to the delete prompt is great for not interrupting your workflow without having to spend all the extra clicks and time to go through the trash. Can I get this changed for Nautilus? Everyone seems to say there is no such option but there has to be a way to edit SOMETHING and make it happen right? I'd be surprised if Windows 1UP's Linux on something like this.

**1.5: Undo Delete: **This might be more important and valuable than above. In Windows, even if you DO send to recycle bin, you can just hit CTRL-Z to undo and carry on. Doesn't seem to work here. Can I make that happen? If so, then I wouldn't care about delete confirmation. This would be most streamlined, imo.

Oh yeah, and rnerwein has also posted in 2010:

> 
in your ~/bashrc ---> alias rm='rm -i'
may be this can help you a little bit. ( but not for undo ).
on every rm you will be ask for " .... realy want .... ?.
but be careful that other scripts will run without to confirm your "rm" command ( you can use : unalias rm to set the alias back )
Although if I recognize rm despite being a noob, that still only involves permanent delete and not the trash?

[B]
2. Most volume controls ding[/B] so that you know if you've set a comfortable volume. I'm not getting that. I have to load a music file or enable system sounds to get anything. Quite clunky. I saw a post from 2010 that said to make a new panel application with the command "canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/bell.ogg" He made no explanation how that was supposed to work though; I tried it, doesn't do anything. Nothing happens on click, volume control is no different.

**3. Disable mini-search. **This isn't much of a deal, but its redundancy makes me want to do something about it. :P When browsing a folder, in Windows, hitting a letter on the keyboard scrolls and selects the first file or folder starting with that letter. Repeating that key will select the next one. In Ubuntu/Nautilus, I'm seeing that any typing brings up a mini-search. I actually kind of like that, but we already have a quick, non-intrusive search that comes up with CTRL-F. Seems to defeat the purpose of the mini-search, since you might as well have the main search work the same way.

However, my whole use of hitting the first letter in Windows is when I'm not sure of the file name and only need a quick scroll down - maybe I'm not even going for that letter, but I'm simply scrolling to that part of the alphabet. Nautilus's use of a search when doing this removes my ability to use the arrow keys to select nearby, and forces me to hit ESC or backspace to clear out of that "mode." Is there an option for this, or some way to change that, or somehow keep both?

Thanks. :)

---

### Post by Sp3ctre18 on 2011-08-26
Scratch the mini-search one; I just discovered my desired function is done with the scroll wheel. That works well; you get to search if I know then name, otherwise you type the first (or more) letters and use scroll wheel to cycle through. :)

Anyone have any ideas for the remaining two?

---

### Post by kerry_s on 2011-08-26
did you look through nautilus preferences?

i know that feature is in pcmanfm, undo is standard if you use trash.

nada on sound.

---

### Post by Sp3ctre18 on 2011-08-27
Yeah, I had already checked. You must be in a different version or something. My preferences looks different, and in that Behavior tab, there's a labeled section called "Trash" and my only options are "ask before emptying trash or deleting files" which is on, and "include a delete command that bypasses trash" which I'm keeping off.

and yeah, not pcmanfm. This is Nautilus.

---

