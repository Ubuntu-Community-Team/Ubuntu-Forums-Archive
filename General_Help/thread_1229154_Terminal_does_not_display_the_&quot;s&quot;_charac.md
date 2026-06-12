---
title: "Terminal does not display the &quot;s&quot; character"
date: 2009-08-01
forum: General Help
---

### Post by MarcusCarabas on 2009-08-01
I am running Ubuntu: Intrepid Ibex. A really strange problem seems to have cropped up over the past couple of days: my Terminal window does not display the "s" character. Every other alphabet shows up just fine, but the "s" just doesn't display. For instance, if I were to type the following command at the prompt, 

"sudo ls -a"

Then what would actually show in the terminal window would be:

$ udo l -a

Notice how the "s" character just doesn't show. And, there is no space where the "s" should have appeared. When I hit "Enter" to try to execute the command I get a bash error reporting that there is no "udo" program. It's almost as if Terminal simply ignores the "s" keystroke.

Some more interesting features of this problem:

1. If I type a command containg the letter "s" in some other application (gEdit, for instance), then copy it and paste it into the Terminal window everything shows up just fine. For example, if I type "sudo ls -a" in gEdit and copy-paste it into Terminal, then the Terminal window will show the pasted text correctly, that is, it will show "sudo ls -a". When I hit "Enter" the command will execute as expected.

2. When I type "Shift-s" an upper-case "S" is displayed in the Terminal window. If CapsLock is on when I type "Shift-S" then a lower-case "s" is displayed.

3. It seems the problem has changed while I have been typing up this post. Now, if I press the "s" key in the terminal window it behaves as the "cursor-up" key and displays the previous command in the command history.

Also this problem is only restricted to the generic non-root Terminal window. Every other application seems to work fine. My word-processor displays everything I type, so do Nautilus and Firefox. Infact even the "Root Terminal" (accessed through "Applications: System Tools" menu item) works just fine. It is only the non-root Terminal window that presents this problem.

Does anyone else have a similar problem? And, is there some way to fix this? I have a hunch that the most recent update has caused it, but I cannot be certain. Any help would be appreciated.

Thanks for taking the time to read this,
- MarcusCarabas.

---

### Post by MaxIBoy on 2009-08-01
Are you using a different keyboard layout than the standard US one? (I noticed you're posting from Canada, I don't know if the keyboards are different there.)

---

### Post by akakingess on 2009-08-01
Just a thought, is there any chance that the s key got mapped as some sort of shortcut that only works when the terminal is open? Also, I will try to find where the keyboard config is that I am pretty sure you can trash and it should rebuild itself and maybe that would solve the issue. Just trying to help brainstorm with ya'll and see what I can do to help.

---

### Post by MarcusCarabas on 2009-08-01
Thanks for the input :)

As far as I know most keyboards in Canada are configured according to the standard U.S. layout. However, I am used to the UK layout.. so I've got my keyboard set up to match that. For instance, for me open quotation marks appear when I type Shift-2 and the "@" symbol appears when I use the key combination that you would use for open quotation marks. 

Anyway, my keyboard has been set up this way ever since I purchased the laptop. The problem with the missing "s" in terminal is new. Also, i haven't set-up any new keyboard short-cuts in quite some time. So I doubt if that could be the cause. However, I agree with the second response - trashing the keyboard config file might force the creation of a new config file and thereby fix the problem....but it's going to take me some time to find the config file/settings for the keyboard. In the meantime please post back if you know where I can find this file. 

Thanks again for responding,
MarcusCarabas.

---

### Post by akakingess on 2009-08-01
> **MarcusCarabas said:**
> Thanks for the input :)

As far as I know most keyboards in Canada are configured according to the standard U.S. layout. However, I am used to the UK layout.. so I've got my keyboard set up to match that. For instance, for me open quotation marks appear when I type Shift-2 and the "@" symbol appears when I use the key combination that you would use for open quotation marks. 

Anyway, my keyboard has been set up this way ever since I purchased the laptop. The problem with the missing "s" in terminal is new. Also, i haven't set-up any new keyboard short-cuts in quite some time. So I doubt if that could be the cause. However, I agree with the second response - trashing the keyboard config file might force the creation of a new config file and thereby fix the problem....but it's going to take me some time to find the config file/settings for the keyboard. In the meantime please post back if you know where I can find this file. 

Thanks again for responding,
MarcusCarabas.


I was in no way implying that you had misconfigured anything, but rather more of a "corruption" issue for lack of a better term. Also, I have heard of people never even touching the "keyboard shortcuts" and stuff showing up there all of the sudden, or key combinations changing, that's why I brought that up.

---

### Post by MarcusCarabas on 2009-08-01
> **akakingess said:**
> I was in no way implying that you had misconfigured anything, but rather more of a "corruption" issue for lack of a better term. Also, I have heard of people never even touching the "keyboard shortcuts" and stuff showing up there all of the sudden, or key combinations changing, that's why I brought that up.

You know, now that you mention it, I'm thinking maybe something went haywire with Compiz... the CompizSettings app sets up so many keyboard shortcuts by default... I've "discovered" quite a few short-cuts to compiz features by accident all too often. Let me go check ... maybe there's a mapping there that's causing all this trouble...

Thanks for bringing this up :)

Oh man.. you were so right! It wasn't compiz though, I checked the shortcut bindings for Terminal itself and turns out somehow the shortcut for paste was "S" instead of Ctrl-Shift-v (which is how I had it previously).. don't know how it got changed .. but changing it back to the way it used to be has fixed my problem... 

merci beaucoup :)

MarcusCarabas.

---

### Post by akakingess on 2009-08-01
A perfect example as to why 2 heads are better than 1!!!  I didn't know about the Compiz issue you knew about, but me bringing up the "corruption" brought that thought to your mind. That's why I love these forums, glad you are back to running normally!!!

---

### Post by jonobr on 2009-08-02
im probably late to this gig,

but if you open a terminal window and type xev

a debug window will open, it will show input received in verbose manor.

So if you move your mouse or cvlick you will see the same dislpayed.
You could try hitting s to see if anything pops up.

If you try other buttons you will see they are proccessed

---

### Post by akakingess on 2009-08-02
> **jonobr said:**
> im probably late to this gig,

but if you open a terminal window and type xev

a debug window will open, it will show input received in verbose manor.

So if you move your mouse or cvlick you will see the same dislpayed.
You could try hitting s to see if anything pops up.

If you try other buttons you will see they are proccessed
Thanks for the tip, I will probably have the chance to use it later!!

---

